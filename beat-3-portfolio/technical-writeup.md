# From a Missing Spider to a Merged Open-Source Contribution

## Overview

For my open-source contribution, I worked on All the Places, a project that collects location data from businesses around the world. I chose an issue involving Freightliner Trucks in Australia because the repository was missing a spider to collect its dealership information. My goal was to use Freightliner's public API to retrieve dealership locations, contact details, services, and opening hours.

I built a Python spider using Scrapy that collected 61 dealerships and produced 161 service-specific records. After testing the implementation and fixing validation errors, I submitted [pull request #20501](https://github.com/alltheplaces/alltheplaces/pull/20501), which was merged on November 12, 2026.

## What happened

### Understanding and reproducing the issue

I started by reviewing the issue and looking through existing spiders in the repository to understand its conventions. Before writing any code, I tried running the missing spider:

```text
uv run scrapy crawl freightliner_au

KeyError: 'Spider not found: freightliner_au'
```

This confirmed that the problem was a missing implementation rather than a broken existing spider.

I then inspected Freightliner's official dealership API. The original issue listed 58 locations, but the API returned 61 unique dealerships. I also found that each dealership contained separate services with their own opening hours.

My API inspection produced:

```text
Total dealers: 61
Unique IDs: 61
Services:
  Repair & Maintenance: 61
  New Vehicle Sales: 39
  Parts-Sales: 61
```

This information helped me decide how to structure the spider.

### Building the spider

I created `locations/spiders/freightliner_au.py` using the repository's existing `JSONBlobSpider` class. Rather than manually parsing every field, I relied on its shared utilities to handle common dealership information.

One decision I made was to create separate records for each service. A dealership might offer repairs, parts, and truck sales, but each service could have different opening hours.

The following part of my implementation creates a unique record for each service:

```python
for service in feature["services"]:
    service_item = item.deepcopy()
    service_item["ref"] = f'{item["ref"]}-{service["serviceId"]}'
    apply_category(self.SERVICE_CATEGORIES[service["name"]], service_item)
```

Using a combination of the dealership ID and service ID allowed each record to have a unique reference while preserving its specific category.

I also used the repository's `OpeningHours` helper to convert the API's structured schedules into the expected format.

### Fixing errors during testing

The first crawl successfully collected 161 records, but it also produced six website validation errors. After inspecting the output, I found that two dealerships provided website URLs without an HTTP or HTTPS scheme.

I updated the code to add `https://` when needed:

```python
if website := communications.get("internet"):
    item["website"] = website if website.startswith(("http://", "https://")) else f"https://{website}"
```

I chose to keep this fix inside the spider because the existing pipeline did not normalize these website values. After making the change, I reran the crawler and confirmed that the errors were resolved.

### Validating and submitting the contribution

After fixing the URL issue, I checked the exported GeoJSON and verified that the spider produced 161 unique references. The records included 39 truck sales, 61 truck repairs, and 61 truck parts entries.

I also ran the repository's existing tests and code-quality checks:

```text
Brand validation:
3 passed, 1 warning

Pre-commit:
All applicable checks passed

Spider crawl:
161 items exported
0 duplicate items dropped
```

I used CodePath's plan-check and ship-gate tools throughout the contribution process. One problem occurred when the ship-gate incorrectly reported unrelated file changes because my local `master` branch was outdated. After updating the branch, I reran the checks and addressed a question about my website URL handling in the PR description.

The final ship-gate passed, and I opened my pull request.

All the Places' automated scraper bot independently tested the spider and reported:

```text
Result: success
Items: 161
Errors: 0
Warnings: 3
```

The warnings involved category matching and repeated contact information across service records. The pull request was later merged into the upstream repository on November 12, 2026.

## Limitations and what's next

One limitation of the implementation is that the spider creates multiple records for dealerships offering different services. This preserves separate categories and opening hours, but it can also produce repeated phone numbers and email addresses. The automated test also reported missing Name Suggestion Index matches for 122 repair and parts records.

Another limitation is that the spider depends on the structure of Freightliner's API. If the API changes its response format or service names, the spider may need updates.

If I continued working on the project, I would monitor future crawl results to make sure the dealership information remains accurate. I would also investigate whether the category matching could be improved without losing the distinction between different services.

This contribution helped me gain practical experience with Scrapy, API data processing, debugging, and testing. More importantly, I learned how to work within an existing codebase, follow its contribution guidelines, and take a change through the open-source pull request process.