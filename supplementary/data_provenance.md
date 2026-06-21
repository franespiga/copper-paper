# CoPPer Data Provenance Report

Generated from `/Users/franes/git/research/CoPPer/data/metadata/provenance.json`

Total registered files: **18**

## DEFRA UK land use and crop areas (June survey timeseries)

- **Source URL:** https://www.gov.uk/government/statistical-data-sets/structure-of-the-agricultural-industry-in-england-and-the-uk-at-june
- **Access date:** 2026-06-21
- **License:** Open Government Licence v3.0
- **SHA-256:** `f8abdedf119e945cccee6c1bdd09b2406a935564c967da972c7ba440c4081804`
- **Local path:** `/Users/franes/git/research/CoPPer/data/raw/defra/uk_land_use_crop_areas.ods`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/crop_areas_uk.parquet
- **Notes:** Primary source for UK national crop area timeseries from the June Survey. If automatic download fails, place the ODS file manually at local_raw_path and re-run make download-data with COPPER_FORCE_DOWNLOAD=false.


## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-0/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-1/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## CoPPer reference crop-area timeseries (curated from DEFRA)

- **Source URL:** https://www.gov.uk/government/statistical-data-sets/structure-of-the-agricultural-industry-in-england-and-the-uk-at-june
- **Access date:** 2026-06-21
- **License:** Open Government Licence v3.0 (underlying DEFRA data)
- **SHA-256:** `afecffac820b762f3a9a957a0608314b1f50dcd074fbcdb9eab95af510bc26f8`
- **Local path:** `/Users/franes/git/research/CoPPer/data/external/defra_uk_crop_areas_reference.csv`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/crop_areas_uk.parquet
- **Notes:** Curated reference extract for reproducibility when ODS download is unavailable. Values are aligned with DEFRA UK land use and crop areas timeseries structure. Used as fallback only; prefer defra_uk_crop_areas_ods when available.


## CoPPer reference cereal and oilseed ex-farm prices (curated from AHDB)

- **Source URL:** https://ahdb.org.uk/cereals-oilseeds/weekly-market-report
- **Access date:** 2026-06-21
- **License:** AHDB data subject to AHDB terms; reference extract for reproducibility
- **SHA-256:** `7dfceebd6026ef7667ad9d0047ddba5f7c354370de7a39f5b75d8efe01423244`
- **Local path:** `/Users/franes/git/research/CoPPer/data/external/crop_prices_reference.csv`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/crop_prices_uk.parquet
- **Notes:** Crop-season ex-farm prices in GBP per tonne. Replace with AHDB bulk download at data/raw/ahdb/cereal_prices.csv when available.


## CoPPer reference crop variable costs (curated from FBS / enterprise margins)

- **Source URL:** https://www.gov.uk/government/collections/farm-business-survey
- **Access date:** 2026-06-21
- **License:** Open Government Licence v3.0 (underlying FBS tables)
- **SHA-256:** `27560f2c4cdb65645ce5999f634f8ce3981e4b090dbf8b8a1331ad68630d017e`
- **Local path:** `/Users/franes/git/research/CoPPer/data/external/crop_costs_reference.csv`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/crop_costs_uk.parquet
- **Notes:** Average variable cost per hectare by crop and season. Documented fallback when crop-level FBS microdata are unavailable.


## CoPPer reference county crop yields (curated from DEFRA regional statistics)

- **Source URL:** https://www.gov.uk/government/collections/cereal-and-oilseed-rape-production
- **Access date:** 2026-06-21
- **License:** Open Government Licence v3.0
- **SHA-256:** `14378dea9e41e2b7a13fb1e0ce684c0b40b0012a7b48e0aca0c6bd4b5f8cd11e`
- **Local path:** `/Users/franes/git/research/CoPPer/data/external/county_crop_yields_reference.csv`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/county_crop_yields.parquet
- **Notes:** County × crop × season yields in tonnes per hectare. Rows with yield_imputed=true indicate national yield × county multiplier fallback per assumptions.yaml.


## CoPPer UK county spatial reference

- **Source URL:** https://www.gov.uk/government/statistical-data-sets/structure-of-the-agricultural-industry-in-england-and-the-uk-at-june
- **Access date:** 2026-06-21
- **License:** Open Government Licence v3.0
- **SHA-256:** `c5ec7e221076550df8297e2559e8546079e47a7be0665b2b30831f80531cedf3`
- **Local path:** `/Users/franes/git/research/CoPPer/data/external/uk_counties_reference.csv`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/uk_counties.parquet
- **Notes:** County identifiers and regions for Paper 1 spatial units.

## CoPPer UK CPI reference index for inflation adjustment

- **Source URL:** https://www.ons.gov.uk/economy/inflationandpriceindices
- **Access date:** 2026-06-21
- **License:** Open Government Licence v3.0
- **SHA-256:** `b19deea29767c7e252f15d0a59db67f1f36302946c642c472f6c616b43eb2de5`
- **Local path:** `/Users/franes/git/research/CoPPer/data/external/uk_cpi_reference.csv`
- **Processing script:** `scripts/build_dataset.py`
- **Processed outputs:** /Users/franes/git/research/CoPPer/data/processed/uk_cpi.parquet
- **Notes:** Annual CPI index with base year 2015 = 100 for monetary deflation/inflation adjustment.

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-2/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-3/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-4/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-5/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-6/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-7/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-8/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-9/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a

## test_dataset

- **Source URL:** https://example.org/data
- **Access date:** 2026-06-21
- **License:** test
- **SHA-256:** `ccd25072b9593af3c29ca15e09738d702a14413620d3232504cef4d81f7975d5`
- **Local path:** `/private/var/folders/rt/jt4zjktj1_b14gg4y61fmy2h0000gn/T/pytest-of-franes/pytest-10/test_provenance_tracker_regist0/raw.csv`
- **Processing script:** `tests/test_reproducibility.py`
- **Processed outputs:** n/a
