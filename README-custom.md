# Python SDK custom files

Custom files for the FlexPrice Python SDK. These are merged into `api/python/` when you run `make merge-custom`.

## Layout

- `examples/` – example scripts (may need import/API updates to match the current Speakeasy-generated SDK)
- `MANIFEST.in` – included in the Python package build

## Adding custom code

1. Create files under `.speakeasy/custom/api/python/` with the same paths as in `api/python/`.
2. Run `make merge-custom` (or `make sdk-all`) so they are copied into `api/python/`.
