# DroneLedger open dataset

Open data from [DroneLedger](https://droneincidents.com), a source-backed archive of drone incidents worldwide.
Each dossier keeps three questions apart: was a drone present, what was the impact, and who is responsible.
Each answer has its own evidence state and the sources that support it.

This repository is a copy of the public exports on droneincidents.com and is updated daily when the data changes.
`data/STATUS.json` shows the number of dossiers and the site release it was copied from.

Archived snapshots with a DOI are on Zenodo: [10.5281/zenodo.23345422](https://doi.org/10.5281/zenodo.23345422)
(concept DOI; it always resolves to the latest version).

## Files

| File | Contents |
|---|---|
| `data/incidents.csv` | One row per published dossier, with sources, evidence states and nested fields as JSON columns |
| `data/incidents.json` | The same dossiers as JSON, with licence and coverage notes |
| `data/claims.csv` | One row per sourced claim: claimant, statement, literal quote, quote language, check time, source |
| `data/incidents.geojson` | Coarse locations (city, region or country level, never precise positions for conflict incidents) |
| `data/drone-types.json` | Drone type catalogue with sourced specifications |

The live API, feeds and an MCP server are described at <https://droneincidents.com/llms.txt>.

## Method in short

- **Evidence tiers** (`corroboration`): `single` means one source reports drone activity at a place and date;
  published so early and local reports are visible, never as confirmation. `multiple` means two or more different
  publishers report the same incident; independence has not been established by an editor. `curated` means an
  editor checked the cited sources line by line and found every quote in the claims table verbatim in its source.
- **Evidence states** are separate per question: `droneStatus`, `impactStatus` and `attributionStatus`
  (confirmed, reported, inconclusive, debunked, unknown). "Reported" is not "confirmed". A claim by a party to a
  conflict stays a claim.
- Automatically published dossiers show at most a city or region for conflict incidents and never live movement.
- Full method: <https://droneincidents.com/methodology/>

This is a curated, selective archive. Counts in this dataset are not counts of all drone incidents worldwide.
It is not a warning service; for incoming threats follow official alerts.

## How to cite

Cite the dossier and its revision, for example:
"DroneLedger, dossier <id>, revision <n>, https://droneincidents.com/incident/<id>/".
For the dataset as a whole, cite the Zenodo DOI above.

## Licence

Our own dossier text, structured data, drawings and videos: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/),
attribution "DroneLedger (droneincidents.com)". See `LICENSE`.
Quoted source passages and linked articles remain the copyright of their publishers; they are included as short
quotations for verification. City and region names in automatically published dossiers are checked against
GeoNames (CC BY 4.0).

## Delivery and support

The data is and stays free. For a delta feed, webhooks, a delivery and correction promise and support, see the
[DroneLedger Data Service](https://droneincidents.com/data-service/).

Corrections: info@droneincidents.com
