# Product changes

Reviewed 8 October 2026. The following removals are prepared for the API release; rollout is still pending. Stop using these identifiers for new integrations. The running service may show them until that release is deployed.

| Legacy identifier | Guidance |
|---|---|
| `google_gencast`, `google_gencast_2_nigeria` | Move to `google_weathernext2` for ensemble forecasts after checking attributes, units, intervals and coverage. |
| `cbam_shortterm_forecast`, `cbam_shortterm_hourly_forecast` | Evaluate `nextgen_forecast` or `nextgen_hourly_forecast`; the field names and statistical meaning differ. |
| `nigeria_daily_forecast`, `nigeria_hourly_forecast` | Evaluate `nigeria_nextgen_daily_forecast` or `nigeria_nextgen_hourly_forecast`. |
| `cbam_historical_analysis`, `cbam_historical_analysis_bias_adjust` | No longer listed in this guide. Existing integrations should contact TomorrowNow; for new historical rainfall work use `imerg_v07`. |

After deployment, new requests for these retired products return HTTP 410. These are not simple name substitutions: update and validate your queries against each new product's field reference.

The daily precipitation layer keeps `precipitation_blend_forecast` and 24 weather fields. Obsolete component rainfall, component weights and model-count diagnostics are removed from discovery and rejected as inactive in new requests. Existing rainfall aliases remain.

The active guide also omits catalogue entries that are inactive or internal: GraphCast, Nowcast, Salient forecasts and hourly CBAM reanalysis. Their omission is not a new retirement of the underlying data or internal workflows.

NextGen, Nigeria NextGen, WeatherNext 2, KMSA Kenya rainfall and FOCUS/1F are preserved. Existing issued exports are not revoked by the public catalogue cleanup.

[Current product catalogue](data-products.md)
