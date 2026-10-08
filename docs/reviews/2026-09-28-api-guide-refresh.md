# API user guide refresh — 28 September 2026

## Scope and source

Updated the repository that owns the requested public site: `kartoza/tomorrownow_gap_documentation`, branch `codex/refresh-api-user-guide-20260928`. The published guide URL returned HTTP 200 during the review. This report records validation before commit and publication.

Catalogue evidence: API fixture state at `3e81a69374b80d1839c6c0c49c26458dd47cb962` (blend cleanup PR #1718), excluding the six public retirements in PR #1717. Both API releases are still pending. The user-facing product-changes page states this clearly. A machine-readable product/field manifest is saved alongside this report.

The guide now documents 19 retained product identifiers across 16 reference pages, with 219 product-specific field entries. Historical CBAM daily reanalysis, NextGen and Nigeria NextGen, WeatherNext 2 and FOCUS/1F are preserved. FOCUS/1F are not invented as new public identifiers. Inactive/internal products are omitted from the active catalogue without claiming their underlying data was newly retired.

## Changes

- Rebuilt product navigation and field references from active dataset, attribute and mapping flags.
- Added NextGen daily/hourly and Nigeria variants, WeatherNext 2, daily precipitation, Kenya rainfall, NeuralGCM historical/realtime, IMERG, iSDA and SoilGrids.
- Removed obsolete active reference pages; eight old paths redirect to the product-changes page.
- Updated authentication, GET measurement versus POST location instructions, dates and run selection, output restrictions, asynchronous status handling and errors.
- Replaced the unverifiable ingestion timetable with availability guidance.
- Refreshed Python, notebook, R, point-CSV R and Postman downloads. Removed saved notebook output and credential placeholders from executable source; examples use environment tokens. Failed Python downloads preserve existing files without reopening them as new output.
- Corrected repository/edit links. Documentation CI builds PRs but only publishes pushes to main; configuration and example changes now trigger it too.

## Verification

- Full MkDocs build completed successfully. Existing informational notices about unrelated pages outside the navigation remain; no missing guide-link warning.
- `scripts/check_api_guide.py /private/tmp/gap-blend-audit-20260928` passed: 19 products, 219 fields, 95 local links, Python syntax, notebook and Postman field queries. Install docs requirements and build first.
- Checked Python downloader success, HTTP failure and HTML response with mocked HTTP; old output remains untouched on failure.
- Shell snippets pass `bash -n`; Postman JSON and ZIP contents match.
- Headless Chromium inspected desktop catalogue, getting-started and rainfall pages, plus mobile catalogue at 390px. No body overflow. Rainfall renders 24 field rows. An old GenCast URL redirects to product changes.
- `git diff --check` passed.

Screenshots and logs: `/private/tmp/gap-guide-evidence-20260928/` and `/private/tmp/gap-guide-build.log`. Preview server: `http://127.0.0.1:8768/developer/api/guide/`.

## Limits and release notes

No authenticated production data request was made. R is not installed locally, so R samples were reviewed but not executed. At validation time, no GitHub CI run or publication had been triggered. Do not claim the prepared API retirements or 24-field cleanup are deployed until the backend releases and live acceptance checks complete.

The current catalogue labels six-hour precipitation as `mm/day` for WeatherNext 2/NeuralGCM. The guide records that mismatch and asks users to confirm intervals before aggregation; it does not silently rewrite backend units. The known blend missing-member/missing-timestep defects remain separate work.

## Update, 8 October 2026

- **CBAM removed from the public guide.** The two remaining CBAM daily reanalysis pages (`cbam_historical_analysis`, `cbam_historical_analysis_bias_adjust`) are no longer listed. The API still serves them for existing integrations, so `product-changes.md` names them, and both old pages redirect there. `scripts/check_api_guide.py` skips them through `NOT_LISTED`, and they are removed from the catalogue manifest.
- **KMSA named.** `kenya_rainfall_daily` is now listed as the *KMSA Kenya daily rainfall forecast* (Kenya Meteorological Service Authority), directly after NextGen. Its page states:
  - the grid (0.05°, about 5.5 km) and horizon (lead days 0–41);
  - that it is rainfall-only;
  - that missing values mean "unavailable", not zero;
  - that a run can arrive up to two days after its run date.

  These facts come from the operational GAP MCP product registry (`config/products.yaml`, `ke_national_rainfall_daily`).
- **Examples switched from CBAM temperature to IMERG V07 rainfall** (`imerg_v07`, `precipitation`, 1–3 Sep 2026) in the Python, Jupyter, R, curl and Postman examples. The Postman ZIP is rebuilt from its JSON.
- **Validation:** the MkDocs build passes. `scripts/check_api_guide.py` against kartoza/tomorrownow_gap PR #1718 fixtures (`3e81a69`) reports **PASS: 17 products, 201 fields, 87 local links, Python snippets, notebook and Postman queries**. Against `main` (`5d59538`), the product list passes; only the blend field count differs, because #1718 is still open.
- **Not run live:** the new IMERG examples could not be executed. `gap.tomorrownow.org` returns HTTP 410 to the reviewing network, while it serves normally from elsewhere. Run them once against the live API before merging.
