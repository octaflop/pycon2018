# User-Focused API Design
## Renato Oliveira

# API Design

- Architecture
- Nouns
- Verbs
- Status Code

But don't forget the user...

"P.S. your API is a user interface"

User interface: the means a user interacts with machines

Why we forget:

UX: APIs are invisible products, devs only use it one

## UX

Encloses the aspects of user interaction with the company and its products
You are guiding a user through a maze. Do it right, and they don't get lost.

Design: meet the exact needs of consumer without fuzz or bother.

## UX Honeycomb (PIC)

DEV Experience:

- Extension of UX that focuses on developer
- understand how devs get work done
- combination of ux and dev

## UX Process

We'll use the UX process to map to API def

product definition → research → analysis → design → validation
^- back to definition

- "Maybe a user wants this" is different than "8 out of 10 users tend to want this"
- We need to synthesize user behavior.

Collect feedback, metrics; etc

## Map UX to Developer Experience

### Personas: A user of our product. Separation of purpose

- frontend
- mobile
- backend
- clients
  - sub-clients, roles
- teammate

### Design Specification aka Documentation

We can still make intuitive and discoverable specifications

### Think of documention as an onboarding

For both an employee or a client it's a way to guide the steps

#### Onboarding

Decrease the learning curve

#### Quick-Start:

[Q: is it helpful to do a doc-first / test-first approach?]

Use step-by-step examples: auth, first endpoint, decreate the time to first call,
use common use cases

#### Errors

Errors should guide users on how to accomplish tasks
Error-based communication
Different errors should return different messages
Help people debug: link to answers

## Your API docs are also a UI

- Information architecture
- Keep it clean and easy to read

## Testing and Feedback

- Prototypes are the cheaper way to get insights from your
  user without having to write code
- Write client code: eat your own dogfood (write client code to get feedback on your API)
- This is an iterative process

## Metrics

One you put your API in place, you must still start collecting metrics to help

- Errors: a great hint on improving docs
  - Add a logging tool with grouping
- Number of requests
- User-agent: gives you a hint on personas and SDKs
- Traffic: keep your API robust and tune what you need

## Conventions and Patterns

use the status code wisely: https://httpstatusdogs.com http://http.cat

Conventions and patterns:

- GET, HEAD, and OPTIONS should be safe: they should never change server state.
- PUT and DELETE are idempotents, they should always have the same result.
- Only POST should change state and change result

- Allow sorting, filtering, and selecting fields form query strings

[Q: How do we deprecate an API?]
- Versioning is extremely important
