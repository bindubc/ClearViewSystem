# User Management with Identity Service

## Context
The application should provide a mechanism for users, to register with  ClearView system.  The system is intended to attract diverse talent from underrepresented demographics, thus making user information confidential to the ClearView system only.

## Status
Proposed


## Considered Options

* Identity Service with OpenID Connect
* Integration with external Auth Providers like Google, Facebook.
* Auth Service as well as External Auth Provider, for basic details fetch.

## Decision Outcome

Chosen option: "Identity Service with OpenID Connect",  The primary users of ClearView are from underrepresented demographics, thus may not be registered with external auth providers.  Moreover, user information is confidential, and usage of external auth providers may result in ClearView users information leak, in the events of security breaches.
