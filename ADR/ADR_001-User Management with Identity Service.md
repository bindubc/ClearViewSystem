# User Management, Identity Service with OIDC

## Context
The application should provide a mechanism for users to register with the ClearView system, supporting both employers and the job seekers. All user information must be kept confidential, encrypted for data anonymization, and accessible exclusively to the ClearView system.

## Status
Proposed


## Considered Options

* Auth Service with OIDC.
* Integration with external authentication providers like Google, Facebook.
* Auth Service as well as External Auth Provider, for basic details fetch.

## Decision Outcome
Selected option: "Auth Service with OIDC." User information is highly sensitive and confidential, and relying on external authentication providers could expose it to risks in the event of a data breach. In such a scenario, the data of both employers, including MNCs, and job seekers could be compromised.
