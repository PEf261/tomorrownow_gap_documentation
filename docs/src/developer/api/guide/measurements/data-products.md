# Data products

Use the exact `product` identifier in API requests. The catalogue below covers **17 public product identifiers**, reviewed on 8 October 2026. It includes the daily rainfall catalogue cleanup planned for the next API release. The live [options endpoint](https://gap.tomorrownow.org/api/v1/measurement/options/) and [interactive API](https://gap.tomorrownow.org/api/v1/docs/) show what the running service currently exposes; access also depends on your account permissions.

## Forecasts

| Product | API identifiers | Attribute reference |
|---|---|---|
| NextGen daily forecasts | `nextgen_forecast`, `nigeria_nextgen_daily_forecast` | [Fields](attributes-reference/nextgen-daily.md) |
| NextGen hourly forecasts | `nextgen_hourly_forecast`, `nigeria_nextgen_hourly_forecast` | [Fields](attributes-reference/nextgen-hourly.md) |
| KMSA Kenya daily rainfall forecast | `kenya_rainfall_daily` | [Fields](attributes-reference/kenya-rainfall.md) |
| Google WeatherNext 2 | `google_weathernext2` | [Fields](attributes-reference/weathernext2.md) |
| Daily precipitation forecast | `precipitation_blend_forecast` | [Fields](attributes-reference/precipitation-blend.md) |
| NeuralGCM S2S | `neuralgcm_s2s`, `neuralgcm_s2s_realtime` | [Fields](attributes-reference/neuralgcm.md) |

## Observations, historical data and soil

| Product | API identifiers | Attribute reference |
|---|---|---|
| IMERG V07 daily rainfall | `imerg_v07` | [Fields](attributes-reference/imerg.md) |
| Arable weather stations | `arable_ground_observation` | [Fields](attributes-reference/arable-stations.md) |
| TAHMO weather stations | `tahmo_ground_observation` | [Fields](attributes-reference/tahmo-stations.md) |
| Disdrometer observations | `disdrometer_ground_observation` | [Fields](attributes-reference/disdrometer.md) |
| Windborne radiosonde observations | `windborne_radiosonde_observation` | [Fields](attributes-reference/radiosonde.md) |
| TAMSAT rainfall long-term normals | `tamsat_ltn` | [Fields](attributes-reference/tamsat-ltn.md) |
| iSDA Soil | `isda_soil` | [Fields](attributes-reference/isda-soil.md) |
| SoilGrids v2 | `soilgrids_v2` | [Fields](attributes-reference/soilgrids.md) |

## Coverage and product choice

A forecast horizon or year range is a catalogue label, not a guarantee that every run, date or point is populated. Query a small region first and inspect times, units and missing values. Station products and gridded products have different spatial support.

NextGen, Nigeria NextGen and WeatherNext 2 are retained. FOCUS/1F models are not retired by this catalogue cleanup; they are not listed as separate public `/measurement/` identifiers in the reviewed catalogue. Use the access route supplied for your account rather than inventing a product identifier.

For old integrations, read [product changes](product-changes.md). The timetable and forecast archive guidance is under [forecast availability](ingestor-schedule.md).
