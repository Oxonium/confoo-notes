# API lessons learned

## Introduction

- Same Hyrum's law as yesterday.
- Check who is the API client (internal API = both producer and consumer)
- Questionable design choices that does not have physical impact VS bridges or roads
- The art of communication is important when designing an API

## API design

### Choose a paradigm and stick to it

- Apply the same paradigm in all endpoints.
- REST, RPC, GraphQL… and other buzzwords
- Check FB issues with GraphQL
- **Intent** first, that translates into a **contract**
- Make it make more sense, do it consistently:
  - `/cloneInvoice`
  - `/viewInvoice`
  - `/printInvoice`
- Alternation/nesting, not able to express that kind of stuff in regular filters
- Filters in a json structure that covers all needs (tree of different clauses)
  - How to transport it to an API? Encoding it as query parameters?
- Front-end: npm install QS (query string): json object in structured queries
  - qs.parse()
  - qs.stringify()
- PHP understands it as hashmap arrays
- Resources linked between them

### Polymorphism and how to tame it

- Client prepared to receive a defined amount of object "types", not easy to modify
- Separate these types in different collections, easier to involve and make it backward compatible

### Never say never

- Introduce new endpoint when needed
- Return only data common to all defined types that are related to the invoice (note, pdf, order, etc)
  - `GET /invoiceDocuments`

### Error messages must be helpful

- 200 OK error true : not helpful at all
- 400 Bad Request / wrong payload : still not helpful
- Show how can the client fix the error he has
- Return list of error messages

### Uphold the rules and break them

- Send info in body instead of query strings
- Proxying the code with Trait in PHP

### Micro optimization of the number of requests

- `/batches`, list of URIs proxied to be processed internally and returned as a list
- Other stuff to take into consideration: security, pagination, performance, partial resource access, group operations, resource nesting, configurable filters…
