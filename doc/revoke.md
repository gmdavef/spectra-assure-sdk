# SpectraAssureApiOperationsRevoke

Execute a revoke() API call.

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

Returns the 'requests.result' of the revoke() API call.

May raise exceptions on issues with the HTTP connection or wrong parameters:

- SpectraAssureInvalidAction: our exception.
- any other exception from requests.get().

## Portal API documentation

- [revokeVersion](https://docs.secure.software/api-reference/#tag/Version/operation/revokeVersion)

## Code example

```python

def revoke_version(
    api_client: SpectraAssureApiOperations,
    project: str,
    package: str,
    version: str,
    reason: str | None = None,
) -> Any:
    qp: Dict[str, Any] = {}
    if reason:
        qp["reason"] = reason

    rr = api_client.revoke(
        project=project,
        package=package,
        version=version,
        **qp,
    )
    print("Version revoke", rr.status_code, rr.text)
    return rr
```
