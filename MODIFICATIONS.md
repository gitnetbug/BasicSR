# Compatibility modifications

## Repository

`gitnetbug/BasicSR`

## Files changed

| File | Original backup | Modification | Reason |
|---|---|---|---|
| `basicsr/data/degradations.py` | `backups/original/basicsr/data/degradations.py` | Prefer `torchvision.transforms.functional.rgb_to_grayscale`, with a fallback to the old `functional_tensor` path. | Supports both modern and older torchvision releases. |
| `basicsr/version.py` | N/A (file was missing/ignored upstream) | Added tracked package version metadata for BasicSR 1.4.2. | Prevents `ModuleNotFoundError` when importing BasicSR directly and allows pip metadata generation. |
| `setup.py` | `backups/original/setup.py` | Read the static `VERSION` file during metadata generation and remove obsolete `setup_requires` fetching. | Prevents modern pip metadata/build failures caused by legacy setuptools dependency fetching. |
| `.gitignore` | `backups/original/.gitignore` | Unignored `basicsr/version.py`. | Ensures the required metadata file is included in the fork. |

All original source files modified in this change are preserved under `backups/original/`.
