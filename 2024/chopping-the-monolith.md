# Chopping the monolith

# [Official slides](https://github.com/confooca/2024/blob/main/2024-02-23/Chopping-the-monolith-Nicolas-Frankel.pdf)

## Introduction

- Current state: monolith (bad), microservices (good)
- Characteristics of microservices (Martin)
- Decentralized governance and data management
- Conway's law: architecture reflects the communication channel in the organization
- Reversing Conway's law to make it work for microservices

## Talk

- Middle managers, 3 main responsibilities :
  - Accept the vacations (lol)
  - Proxy of the yearly raise
- Recipe for failure:
  - Read about MS
  - Remembers only the benefits
  - Applies on the technical aspects
  - Leaves for another job with a shinier CV
- Benefits:
  - Strong module boundaries: if you don't do monorepo, own repo for each
    - Many other way to enforce boundaries
    - With fewer downsides
  - Technology diversity
    - Satisfies some people's aspirations
    - Doesn't help the organization as a whole
  - Lead time, one of the golden devops metrics (we want to reduce this time as much as possible)
    - Specification
    - Implementation
    - Deployment
  - How did we manage releases "back in the days"
    - Non-frequent releases, release trains
    - You don't want to miss the train
      - Bugfixes are allowed
      - Shove feature intro a bugfix

- It's not possible to release often and test monoliths well
- Real problem:
  - Not all parts on an app change at the same speed
  - Some are more stable than others
  - Reasons for change
    - Business requirements
    - Law
- Rules engine: (created to address the challenge of delivering more often)
  - No release
  - Business changes the rules how often they want
  - With great power comes great responsibility
- Isolate the quick-changing part?
  - Rules engine
  - Microservice
  - Serverless function
  - …

- Strangling the monolith, which shrinks over time
  - https://microservices.io/patterns/refactoring/strangler-application.html
  - "Chop" the part outside the monolith
- E-Commerce: business wants to push some products:
  - Pricing should be very flexible
  - Impossible to model pricing options ahead of time
  - Chop the pricing engine
    - Don't break the client!

## Misc

- [apisix](https://apisix.apache.org/) (API gateway) / [etcd](https://etcd.io/)
- Proxy-rewrite
- First: two calls, version / checkout
- Second: still two calls
- Third: with the same backend version, call an Azure function
- Check GitHub for the source code
- Solve a specific problem in a specific context
- Hype driven industry

## Documentation

- https://github.com/nfrankel/chop-monolith
- https://blog.frankel.ch/chopping-monolith/
- https://github.com/apache/apisix
- https://openresty.org/en/ (change conf with LUA calls)