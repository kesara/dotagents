# Before / After: narrative rewritten as specification

This file is an example only. It is not normative.

## Before (narrative — avoid)

> When a client wants to fetch a resource it should send a GET request, and it
> really needs to include an Authorization header with a bearer token,
> otherwise the server will reject it. The server checks the token, and if it's
> valid it returns the resource with a 200, but if the token is missing or
> expired it returns a 401, and for tokens that are valid but not permitted to
> access that resource it returns a 403. Note that tokens expire after one hour.

Problems: mixed requirement levels, an enumeration of status codes dispersed
across sentences, an example detail ("one hour") inline with normative text,
and reasoning ("otherwise the server will reject it") that belongs to another
layer.

## After (specification)

### Request

A client MUST send a GET request to fetch a resource.

A request MUST include an `Authorization` header carrying a bearer token.

### Response

The server MUST respond according to the following table.

| Condition                                             | Status |
|-------------------------------------------------------|--------|
| Token valid and permitted to access the resource      | 200    |
| Token missing or expired                              | 401    |
| Token valid but not permitted to access the resource  | 403    |

A `200` response MUST include the requested resource in the body.

### Token lifetime

A bearer token MUST expire no later than one hour after issue.

---

**Example** (non-normative): a client fetches `/reports/42` by sending
`GET /reports/42` with header `Authorization: Bearer <token>`.
