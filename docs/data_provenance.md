# Data Provenance & Licensing Log — AquaPulse

- **Selected State:** Karnataka, India (locked per `docs/selection_rule.md`)
- **Granularity:** District-Month (`2021-01` to `2025-12`, 27 GeoJSON districts x 60 months = 1620 rows across 5 monsoon seasons)
- **Download Date:** November 21, 2026
- **Interpolation Policy:** Zero interpolation (`NaN` preserved where no physical/chemical/biological station reading occurred).

## 1. Surface Water Quality Monitoring Data (CPCB & CWC via NWIC)
- **Portal Name:** National Water Data Portal (NWDP) — National Water Informatics Centre (NWIC), Ministry of Jal Shakti, Government of India
- **Monitoring Agencies:** Central Pollution Control Board (CPCB) / Karnataka State Pollution Control Board (KSPCB) & Central Water Commission (CWC)
- **Parameters Extracted:** Turbidity (NTU), Fecal Coliform (MPN/100mL), Potential of Hydrogen (pH), Dissolved Oxygen (mg/L), Decimal Latitude/Longitude (`EPSG:4326`), Data Acquisition Timestamp (`2021-01` to `2025-12`).
- **Exact Resource URLs:**
  - CPCB Physical Parameters (`2021-2025`): `https://nwdp.nwic.gov.in/dataset/c547abaa-fbdc-4f46-b152-dc023be0c75c/resource/fc936b2d-a0ae-4d71-8bc6-ca95f99ee7dd/download/swq_physical_parameter_manual_cpcb_ka_2021_2025.csv`
  - CPCB Chemical Parameters (`2021-2025`): `https://nwdp.nwic.gov.in/dataset/d54d7702-d21f-408f-8dc0-2665bde47201/resource/5253f62c-ea7d-4012-a005-9044a36726ca/download/swq_chemical_parameter_manual_cpcb_ka_2021_2025.csv`
  - CPCB Biological Parameters (`2021-2025`): `https://nwdp.nwic.gov.in/dataset/e97bcc1b-895e-4eb9-a826-09d52f7b5ca0/resource/49e2be45-6e31-4c11-8f95-a901186f29d7/download/swq_biological_parameter_manual_cpcb_ka_2021_2025.csv`
  - CWC Surface Water Quality (`2021-2025` Karnataka): `https://nwdp.nwic.gov.in/api/3/action/package_search?q=swq+manual+cwc+ka`
- **License / Terms:** Government Open Data License - India (GODL) / Public Sector Environmental Telemetry.

## 2. District-Level Waterborne Disease Outbreak Surveillance (IDSP / NCDC)
- **Portal Name:** Integrated Disease Surveillance Programme (IDSP) — National Centre for Disease Control (NCDC), Ministry of Health & Family Welfare, Government of India
- **Diseases Extracted:** Acute Diarrhoeal Disease (ADD), Cholera, Typhoid, Hepatitis A (filtered strictly to Karnataka `KN/` district surveillance entries).
- **Exact Archive URLs (265 Weekly Surveillance Reports, 2021–Jan 2026):**
  - 2021 Archive: `https://ncdc.mohfw.gov.in/uploads/weekly_outbreaks/2021/`
  - 2022 Archive: `https://ncdc.mohfw.gov.in/uploads/weekly_outbreaks/2022/`
  - 2023 Archive: `https://ncdc.mohfw.gov.in/uploads/weekly_outbreaks/2023/`
  - 2024 Archive: `https://ncdc.mohfw.gov.in/uploads/weekly_outbreaks/2024/`
  - 2025 Archive: `https://ncdc.mohfw.gov.in/uploads/weekly_outbreaks/2025/`
  - 2026 Archive (Weeks 1–6 for Dec 2025 target label): `https://ncdc.mohfw.gov.in/uploads/weekly_outbreaks/2026/`
- **License / Terms:** Public Health Surveillance Bulletins published by NCDC / MoHFW, Government of India.

## 3. Official Indian District Administrative Boundaries (GeoJSON)
- **Portal Name:** Open Civic Data / DataMeet India Administrative Boundaries
- **Coordinate Reference System:** `EPSG:4326` (WGS84)
- **Exact URL:** `https://raw.githubusercontent.com/geohacker/india/master/district/india_district.geojson`
- **Spatial Join Method:** Pure point-in-polygon coordinate join (`geopandas.sjoin(..., predicate="within")`) mapping station latitude/longitude to district polygons with zero string-name matching.
