# Preferential Google Ads Click ID - Fixed Analytics™

A **web GTM variable** reading six GCLID, GBRAID and WBRAID cookies (`_gcl_*` and `FPGCL*`). **Unlike single-ID fetchers, it selects a preferential click ID automatically:** GCLID → GBRAID → WBRAID, preferring first-party cookies within each type. It also identifies the winning cookie.

## Install and use

1. Import `template.tpl` under **Web GTM → Templates → Variable Templates**.
2. Create a variable using the template, e.g. `{{Google Click IDs - All}}`.
3. Its output is an **object** containing eight properties:

```json
{
  "fp_gclid": "ABC123",
  "fp_gbraid": "DEF456",
  "fp_wbraid": null,
  "gclid": null,
  "gbraid": null,
  "wbraid": null,
  "preferential_click_id": "ABC123",
  "preferential_click_id_type": "FPGCLAW"
}
```

4. For an individual field, create an **Object Property Extractor** variable. Set its source object to `{{Google Click IDs - All}}` and property name to `preferential_click_id`. Use `preferential_click_id_type` for its source cookie.

## Logging Preferences

- **Disable Logging:** no logs.
- **Debug Mode (default):** logs only in GTM Preview/Debug.
- **Always Log:** logs in Preview and production.

Logs show consent outcome, available-ID count, and preferred cookie name—**never click ID values**.

Missing IDs are `null`; denied `ad_storage` returns `undefined`. Initialize consent early. Priority is **not** click recency.

Developed by **Javier Garijo · Fixed Analytics™**.
