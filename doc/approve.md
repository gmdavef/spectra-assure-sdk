# SpectraAssureApiOperationsApprove

Execute a approve() API call.

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

Returns the 'requests.result' of the approve() API call.

May raise exceptions on issues with the HTTP connection or wrong parameters:

- SpectraAssureInvalidAction: our exception.
- any other exception from requests.get().

## Portal API documentation

- [approveVersion](https://docs.secure.software/api-reference/#tag/Version/operation/approveVersion)

## Code example

```python

def approve_version(
    api_client: SpectraAssureApiOperations,
    project: str,
    package: str,
    version: str,
    reason: str | None = None,
) -> Any:
    qp: Dict[str, Any] = {}
    if reason:
        qp["reason"] = reason

    rr = api_client.approve(
        project=project,
        package=package,
        version=version,
        **qp,
    )
    print("Version approve", rr.status_code, rr.text)
    return rr
```
