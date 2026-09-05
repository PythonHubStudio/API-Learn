# Security Policy

Thank you for helping keep **API Learn** safe.

API Learn is an educational platform intentionally designed for experimentation with HTTP, REST APIs, SOAP, web scraping, authentication, browser automation, and related technologies.

Some unusual responses, rate limits, authentication flows, scraping traps, or deliberately misleading page elements may be intentional parts of the learning environment.

However, genuine security vulnerabilities should be reported privately.

## Reporting a vulnerability

Please **do not create a public GitHub Issue or Discussion** for a suspected security vulnerability.

A security report may include issues such as:

* authentication or authorization bypass
* access to another user's private application state
* exposure of secrets or credentials
* unintended access to server or infrastructure resources
* injection vulnerabilities
* serious cross-site scripting vulnerabilities
* CSRF vulnerabilities affecting protected actions
* unintended data exposure
* mechanisms that allow the service to be significantly disrupted

When reporting a vulnerability, please include:

* a clear description of the issue
* affected URL or endpoint
* reproduction steps
* expected behavior
* actual behavior
* proof-of-concept details when necessary
* possible security impact

Please avoid accessing, modifying, or deleting data beyond what is necessary to demonstrate the problem.

## Educational behavior is not necessarily a vulnerability

API Learn intentionally includes behavior used for teaching, including:

* rate limiting
* scraping detection
* honeypots
* dynamic HTML
* authentication challenges
* intentionally generated error responses
* fake users, products, carts, and orders

If you are unsure whether something is intentional, you may first ask a general question in GitHub Discussions without publishing exploit details.

## Public disclosure

Please allow reasonable time for a security issue to be investigated and fixed before publicly disclosing technical details.

## Scope

The security policy applies to:

* https://apilearn.tukas.dev/
* the REST API
* the SOAP service
* associated public functionality of API Learn

Third-party services and infrastructure providers are outside the project's direct scope.

Thank you for reporting security issues responsibly.
