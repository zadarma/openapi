# Zadarma OpenAPI Specification

OpenAPI 3.0.3 specifications for the [Zadarma](https://zadarma.com) VoIP API and Teamsale CRM API.

- **Live API docs:** https://zadarma.com/en/support/api/
- **Base URL:** `https://api.zadarma.com`
- **Specs:**
  - `spec/v1/openapi.json` — Zadarma VoIP API
  - `spec/v1/openapiteamsale.json` — Zadarma Teamsale CRM API

## Quick Start

Validate the specification:

```bash
npx @redocly/cli lint spec/v1/openapi.json
```

Preview rendered documentation locally:

```bash
npx @redocly/cli preview spec/v1/openapi.json
```

Build a standalone HTML documentation file:

```bash
npx @redocly/cli build-docs spec/v1/openapi.json -o index.html
```

## Using the Specs

Import either `spec/v1/openapi.json` or `spec/v1/openapiteamsale.json` into tools like:

- [Postman](https://www.postman.com/) — import as OpenAPI collection
- [openapi-generator](https://openapi-generator.tech/) — generate client libraries
- [Swagger UI](https://swagger.io/tools/swagger-ui/) — interactive API browser

## Authentication

Every request requires an `Authorization` header in the format `userKey:signature`. The signature is computed as:

1. Sort request parameters alphabetically by key
2. Build a query string (RFC 1738)
3. Concatenate: `method_path + query_string + md5(query_string)`
4. `signature = base64(HMAC-SHA1(concatenated_string, secret_key))`

Rate limits: 100 requests/min (general), 3 requests/min (statistics endpoints).

## Official SDKs

- [TypeScript](https://github.com/zadarma/user-api-typescript)
- [PHP](https://github.com/zadarma/user-api-v1)
- [Python](https://github.com/zadarma/user-api-py-v1)
- [C#](https://github.com/zadarma/user-api-cs-v1)

## License

[MIT](LICENCE)
