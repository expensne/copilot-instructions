---
applyTo: "**/*.java"
---

# Java Language-Specific Copilot Instructions

## Language Features
- Prefer records for immutable DTOs and value objects.
- Use sealed classes for controlled inheritance hierarchies.
- Use pattern matching for `switch` and `instanceof` where it improves clarity.
- Use `var` only for obvious inferred types; avoid reducing readability.
- Use text blocks (`"""`) for multi-line strings (e.g., SQL, JSON).
- Use `Optional` only for return types; never for fields or parameters.
- Favor Streams for collection transformations; avoid overly complex pipelines.
- Prefer immutable objects; avoid exposing mutable internals.
- Use `Duration`, `Instant`, `LocalDateTime` (java.time) instead of legacy date/time APIs.
- Use Lombok to reduce boilerplate (e.g., `@Builder`, `@RequiredArgsConstructor`).

## Project Structure
- Keep domain model free of framework dependencies.
- Keep controllers thin.

## Configuration
- Use `application.yml` with Spring profiles: `application-{profile}.yml`.
- Use `@ConfigurationProperties` + `@Validated` for typed config.
- Never hardcode secrets; resolve via environment or external vault.
- Fail fast on missing mandatory configuration.

## Logging
- Use SLF4J with parameterized logging: `log.debug("User {} not found", id)`.
- Never log sensitive data (PII, secrets, tokens).
- Use `INFO` for lifecycle, `DEBUG` for diagnostics, `WARN` for recoverable issues, `ERROR` for failures.

## Error Handling
- Create focused custom exceptions (e.g., `DomainValidationException`, `ResourceNotFoundException`).
- Never swallow exceptions; rethrow with context or map to meaningful responses.
- Include correlation or trace IDs in error logs.

## REST API
- Use clear, resource-oriented URIs; plural nouns.
- Validate input.
- Return proper HTTP status codes; never overload 200.

## Testing
- Use JUnit 5 (Jupiter), AssertJ for fluent assertions, Mockito for mocks, Testcontainers for integration tests.
- Separate test types:
  - Unit: fast, isolated, no Spring context.
  - Slice tests: `@DataJpaTest`, `@WebMvcTest`, etc.
  - Integration: use Testcontainers for real dependencies.
- Name tests descriptively: `should[ExpectedBehavior]When[StateUnderTest]`.
- Follow AAA pattern: Arrange, Act, Assert.
- Use `@BeforeEach`/`@AfterEach` for setup/teardown.
- Keep tests short and focused.
- Assert edge cases: nulls, empties, time boundaries, large inputs.
- Use `@Nested` to group related scenarios.

## Code Quality
- Use `final` for fields and parameters unless mutation is required.
- Keep methods short; extract logic into well-named private methods.
- Avoid premature abstraction; refactor duplication only after it repeats.
- Prefer composition over inheritance.

## Dependency Management
- Use Maven for dependency management.

## Documentation
- Document architectural decisions (ADR) for significant choices.
- Add Javadoc only where it clarifies intent beyond the code.

## Naming & Structure
- Classes: `PascalCase`; methods/fields: `camelCase`; constants: `UPPER_SNAKE_CASE`.
- Avoid abbreviations unless ubiquitous (e.g., `id`, `api`).
- Keep packages cohesive and low coupling.

## Validation & Defensive Coding
- Validate inputs at boundaries (controllers, public APIs).
- Use `Objects.requireNonNull` for mandatory constructor parameters.
- Fail fast on invalid state.