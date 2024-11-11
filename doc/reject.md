# SpectraAssureApiOperationsReject

Execute a reject() API call.

## Targets

- Version

## Arguments

- project: str, mandatory.
- package: str, mandatory.
- version: str, mandatory.
- auto_adapt_to_throttle: bool, default False, optional.

## Query parameters

| Name          | Type      | Default | Validation |
| --            | --        | --      | --         |
| reason        | `string`  |         |            |

## Responses

Returns the 'requests.result' of the reject() API call.

May raise exceptions on issues with the HTTP connection or wrong parameters:

- SpectraAssureInvalidAction: our exception.
- any other exception from requests.get().

## Portal API documentation

- [rejectVersion](https://docs.secure.software/api-reference/#tag/Version/operation/rejectVersion)

## Code example

```python

def reject_version(
    api_client: SpectraAssureApiOperations,
    project: str,
    package: str,
    version: str,
    reason: str | None = None,
) -> Any:
    qp: Dict[str, Any] = {}
    if reason:
        qp["reason"] = reason

    rr = api_client.reject(
        project=project,
        package=package,
        version=version,
        **qp,
    )
    print("Version reject", rr.status_code, rr.text)
    return rr
```
