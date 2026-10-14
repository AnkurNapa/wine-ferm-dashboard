# Wine Fermentation Monitor Dashboard

A self-contained HTML dashboard showing winery vessel/fermentation status:
tank cards with fill levels, stage, wine analysis (ABV, pH, SO₂, TA), smart
alerts, active lots and D3 packing/dispatch charts.

**Live page:** https://ankurnapa.github.io/wine-ferm-dashboard/

## What this is

This is a **standalone, public demo** version of a Dynamics 365 / Dataverse web
resource (`dia_wine_fermCardsV1`). The original fetches live data from a Dataverse
org via `odata()`; a public static page can't authenticate to that org, so this
version ships with **baked-in synthetic sample data** (`_DEMO` in `index.html`).
Everything renders with no login and no backend.

It is designed to be embedded, for example as an iframe tile in a table/dashboard:

```html
<iframe src="https://ankurnapa.github.io/wine-ferm-dashboard/"
        style="width:100%;height:900px;border:0"></iframe>
```

## Files

- `index.html`: the entire dashboard (HTML + CSS + JS + sample data, single file)

## Differences from the live Dynamics version

| Live web resource | This static page |
|---|---|
| `odata()` → Dataverse Web API `/api/data/v9.2/…` | `odata()` → returns baked `_DEMO` data |
| `dia_d3_uikit.js` web resource | inlined demo data layer |
| `dia_wine_chatbotV1` web resource | removed (needs Dataverse + LLM backend) |
| d3 from `/WebResources` | d3 from jsDelivr CDN |

To refresh the sample data, edit the `_DEMO` builder near the top of the `<script>`
block in `index.html` (the `V` array of vessels and the lot/bottling/bottle arrays).

## Hosting

No build step. GitHub Pages serves `index.html` from the repo root on `main`.
