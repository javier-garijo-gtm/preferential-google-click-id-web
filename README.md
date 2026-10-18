# Preferential Google Ads Click ID - Fixed Analytics™

A **web Google Tag Manager (GTM) variable template** that fetches six Google Ads click IDs from JavaScript (`_gcl_*`) and first-party (`FPGCL*`) cookies in one object. **Unlike single-ID fetchers**, it automatically selects a **`preferential_click_id`** using **GCLID → GBRAID → WBRAID**, with **first-party before JavaScript** within each type. It also returns `preferential_click_id_type`, the **exact cookie name** that supplied the selected ID. No manual cookie comparisons needed. Developed by **Javier Garijo**.

## Setup

1. Import `template.tpl` under **Web GTM → Templates → Variable Templates**.
2. Create a variable named `Click IDs – All`.
3. It returns an **object** (several named values):

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

## Extract a value for your tags

Create an **Object Property Extractor** variable (install its template if needed). Set **Source Object** to `{{Click IDs – All}}` and **Property Name** to `preferential_click_id`. It returns `ABC123` for tags. Extract `preferential_click_id_type` to identify its cookie, or another field for a specific ID.

Missing IDs return `null`. If `ad_storage` is denied, the object is `undefined`. Priority does **not** indicate the newest click.
