# Metriker Ingest Action

Send SBOM and coverage metrics to Metriker.

## Inputs

- `api_key` (required): API key for Metriker (use secrets)
- `component`: Metric component tag sent as `x-metric-component` (optional; default: empty)
- `sbom_path`: Path to the SBOM JSON file (default: empty; when set, SBOM is uploaded)
- `coverage_path`: Path to the LCOV file (default: empty; when set, coverage is uploaded)
- `metric_name`: Custom metric name to ingest (default: empty)
- `metric_value`: Custom metric numeric value to ingest (default: empty)
- `fail_on_error`: Fail the action if ingestion fails (default: `true`)

## Example usage

```yaml
- name: Ingest metrics to Metriker
  uses: metriker/actions@v1
  with:
    api_key: ${{ secrets.METRIKER_API_KEY }}
    component: backend
    sbom_path: sbom.json
    coverage_path: coverage/lcov.info
    metric_name: build_time_seconds
    metric_value: 123.45
```

## Example usage (SBOM only)

```yaml
- name: Ingest SBOM to Metriker
  uses: metriker/actions@v1
  with:
    api_key: ${{ secrets.METRIKER_API_KEY }}
    component: backend
    sbom_path: sbom.json
```

## Example usage (coverage only)

```yaml
- name: Ingest coverage to Metriker
  uses: metriker/actions@v1
  with:
    api_key: ${{ secrets.METRIKER_API_KEY }}
    component: backend
    coverage_path: coverage/lcov.info
```
