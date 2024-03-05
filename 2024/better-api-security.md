# Towards the better API security

## Introduction

- Hyrum's law: consistent, backward compatible
- All possible behaviors will be used by somebody
- Basics:
  - API key
  - No open access
  - No access to sensitive data without encryption
  - AutN/AuthZ
  - Secured endpoints with permissions
- OWASP APIs security top 10

## API design

### Resource probing

- API response exposing API design (ie: returning "email does not exist")
  - Never inform client on what was wrong (for sensitive endpoints)

### Resource enumeration

- API redirections with IDs in URIs
- Possible to remove the IDs (`/me` instead of `user/1`)
- Use UUIDs, or another slug field to identify the resource
- 64 bits integer: 10 bits of timestamp 10 bits machine identifier, 12 bits of randomness

### Timing attacks

- 204 no content / password reset
  - Same response no matter the context (existing / non-existing account)
  - BUT, API response faster when non-existing account
  - Behavior research to check what's behind
- Constant-time algorithm
- Do not leak information that can be analysed in what took a shorter period of time or not
- Example: PHP `hash_equals()`

### Prevent side-channels - excessive information exposure

- Security questions asking for stuff that can be found elsewhere in the system (display of dogs name AND ask of dogs names in the security questions).
- Split the API endpoints and require the user to re-authenticate itself (2FA, etc) to access that type of data even if he is already authenticated.

### Unbounced collections - DDOS

- Returning collections of things.
- Risk of exposing too much information (ORM schema by stuff returned that are not specifically formatted for the API endpoint).
- Control the amount of stuff that can be set in the API endpoints, to prevent that kind of DDOS attacks.
- Split that between different endpoints to dissipate that issue (IDs instead of whole object).

### Best practices

- Monitor any and all communication details.