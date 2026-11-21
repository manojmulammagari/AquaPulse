# State & Pilot District Selection Rule — AquaPulse

- **Date Locked:** November 21, 2026 (Pre-data acquisition & pre-modeling)
- **Author:** Manoj Kumar Reddy Mulammagari

## 1. Objective State Selection Rule
We evaluate candidate Indian states (Maharashtra, Karnataka, Tamil Nadu, Kerala) against three strict public-data criteria:
1. **Water Quality Station Coverage:** Minimum 30+ active CPCB National Water Quality Monitoring Programme (NWMP) surface/groundwater stations with valid decimal latitude and longitude coordinates.
2. **Disease Surveillance Completeness:** Multi-year district-level IDSP records covering Typhoid, Acute Diarrhoeal Disease (ADD), Cholera, and Hepatitis A in machine-readable tabular format (CSV/XLSX or text-extractable PDF).
3. **Boundary Alignment:** Clean polygon coverage in official public Indian district boundary GeoJSON/Shapefile datasets (`EPSG:4326`).

The single state with the highest combined CPCB station count and multi-year IDSP district coverage is locked for the full pipeline.

## 2. Objective Pilot & Demo District Selection Rule
Within the chosen state, the pilot district for Phase B spatial-join verification (and primary UI demo walkthrough) is selected strictly as the district with:
1. The highest count of geo-located CPCB monitoring stations, AND
2. At least 2 distinct historical monsoon outbreak spikes (`outbreak_count > 0`) in the IDSP logs.
