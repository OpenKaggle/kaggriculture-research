# Data and upstream sources

This is a source-and-methods archive, not a data mirror. Reproduction starts
with the upstream owner and their current terms.

| Material | Authoritative location | Public-release treatment |
| --- | --- | --- |
| Kaggriculture competition page, data, rules, and platform updates | [Kaggle: Kaggriculture](https://www.kaggle.com/competitions/kaggriculture) | Link only. Do not commit downloaded competition files. |
| Competition replay payloads and submission state | The competition page and the account that owns the run | Link or describe only. Do not commit replay payloads, cache output, or submission bundles. |
| Third-party Kaggle notebooks and kernels | Their original Kaggle Code pages | Link to the creator's original page when a citation is needed; do not mirror notebooks, kernel metadata, or extracted artifacts. |
| OpenKaggle-authored source and documentation | This repository | Tracked when it passes the public-release checks in [RELEASE_MANIFEST.md](RELEASE_MANIFEST.md). |

## Derived material

Some agent source expects locally produced fixtures such as `actions.json` or
`tapes.json`. Those files can encode replay-derived behavior and are excluded
from the public archive. Their absence is intentional: a public checkout must
not silently substitute, reconstruct, or fetch protected inputs.

If a future release contains an OpenKaggle-owned derived dataset, it needs a
separate provenance record, a rights review, a documented transformation, and a
clean-room restore test before publication. A reversible de-identification map
is private archival material, never a public repository artifact.
