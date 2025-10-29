---
applyTo: "**/*Controller.java,**/*.html,**/*.yaml,**/*.yml"
---

# API-Specific Copilot Instructions

## REST API Design.

### API Design & Specification
- API designs MUST be resource-centered and use correct HTTP methods (RMM Level 1).
- OpenAPI 3.0 must be used for all HTTP APIs.
- English is mandatory for API description and domain terms (if available).
- Meta information in every API specification:
    - `title` [MUST]
    - `description` [MUST]
    - `contact` (for B2B APIs) [MUST]
    - `datevInfo` Extension [MUST]
    - `copyright` (for B2B, external APIs) [MUST]

### Versioning
- OpenAPI specifications must be semantically versioned (`version` field).
- APIs in production must contain major version in URL path.
- For breaking changes: increase major version.
- Parallel operation of multiple major versions must be possible.

### Schema & Naming
- Use domain-specific identifiers for schema components (no "DTO").
- Schema Object: PascalCase.
- Property & path parameter & query parameter: camelCase.
- Resource name & HTTP header: kebab-case.

### URI Design
- "/" indicates hierarchies.
- URIs must not end with "/".
- No reserved delimiters or "." in domains.
- No "_" in URIs (use "-" instead).
- Only lowercase letters.
- Singular for single resource, plural for list resources.
- No version information in resource names.
- No verbs or CRUD terms in URIs.
- Activity resources (e.g. reset-password) only for actions:
    - must appear as verb in path.
    - must use HTTP POST.

### HTTP Methods
- HTTP methods must be used according to RFC 9110 (GET, POST, PUT, DELETE, PATCH, HEAD).

### Request Body & JSON
- For strings, `maxLength` must be defined and validated.
- For arrays, `maxItems` must be defined and validated.

### Header & Authentication
- Header fields must follow HTTP reference (RFC 9110).
- Basic Auth (Authorization: Basic …) is not allowed.
