# 4 Reliability Anti-Patterns

# [Official slides](https://github.com/confooca/2024/blob/main/2024-02-23/4-reliability-anti-patterns.pdf)

## Introduction

- The future belongs to those who believe in reliability
- Reliability: most important feature in our systems
- SRE: Site Reliability Engineer

## #1 Reliability Procrastination Culture

- Mindset where we avoid embracing reliability (perceived inconvenience of reliability)
- Reactive VS proactive: lots of negative impact (tech debt, etc)
- Short-term vision: quick fixes over long-term solutions
- Blame game: blaming people over collaboration
- Potential solutions below.

### Cultural shift

#### Blameless culture

- Admitting the mistake, explaining why it was made, and how it can be avoided (+ bonus when doing this)

#### Post-mortems

- Learning from our failures

#### No hero

- Team of people, there should be no hero saving the day

#### SLOs

- Service Levels Objectives: metrics (latency, availability)

### SRE Culture

- Dev / Ops split
- Then DevOps
- SRE: common goal, working on reliability challenges
- Force multiplier: the team that excels at reliability 1.8x more likely to meet or exceed organization goals.

## #2 Failure Denial Syndrome

- Mindset where we avoid or deny the inevitability of failures in complex system
- Risk analysis meeting: we need to anticipate everything

### Introduction

- Fear of failure:
  - People may worry about the consequences
  - Fear of getting blamed in case of failure
  - Not a lack of skills, it's a lack of reliability culture

### Solutions

- The question is not if it's going to fail, but how it is going to fail
- Don't tell me how it works, tell me how it fails
- We need to design for failure
- Each unit should be replaceable
- Crash-only software: this system should handle failures or recover from a failure in a simple manner
- Don't detect failure, but the absence of success
  - What does it mean to have this success, and alert if not present
- Bulkhead pattern: isolate failure, make sure it's not spreading
- Graceful degradation:
  - Avoid failing completely and spreading
  - Queue to handle user requests
  - Handling requests that were already abandoned
  - FIFO under normal conditions: first in, first out
  - LIFO under heavy load: last in, first out

## #3 Observability deficiency

### Introduction

- Streetlight effect: cognitive bias, when people focus on what is easily visible
- Trap of observability
- Some negative impacts of observability done wrong:
  - Inefficiency
  - Blind spots in system monitoring: customers are seeing errors but not the people monitoring
  - Misleading (missing word…)
- We need observability because:
  - System are more and more complex
  - Deliver new changes at fast paces
  - 3 pillars:
    - First principle: discover the source of the problem
    - Unknow unknown: discover problems outside of our awareness
    - Explorability
- Observability = you can understand any state of your system, without needing to ship new code

### Solutions

- We should understand why we need observability
- We should promote a culture of observability
- It should stay a moving target: not something static, it has to evolve with the system

## #4 Rollout roulette

### Introduction

- Risky practice of deploying to prod without a defined plan
- Negative impacts:
  - Stress
  - Customer dissatisfaction
  - Reputation damage

### Best practices

#### Frequency

- If you release more frequently, the less change between releases, less issues

#### Test

- Rollout even if there are no changes

#### Adapt

- Canary VS progressive rollout
  - Canary: partial and time-limited
    - Few production envs
  - Progressive rollout: progressively increasing scope that allow for problem detection
    - Many production envs

#### Rollback

- Rollback: if it can break, it will break. Rollout to an earlier version.
  - Tested
  - Effective
  - Easily accessible

#### Feature flag

- Consistency

#### Rollout supervision

- End user metrics, as close as possible to user happiness
- Any behavior changes: track any behavior change (CPU, response code, latency…)
  - Not directly tied to user happiness, but it will impact it at some point

### Conclusion

- Change is the first source of outages
- Faster is safer
- Rely on proven industry best practices
- Observability = backbone for reliability
- Build efficient rollout plans
- [Talk slides](https://docs.google.com/presentation/d/e/2PACX-1vSliUbEggyAxG6lXczPtR_lGRR5UIURiEJ3mlyf9Hlw-BNcfxloTWIPcwjmxeAgGxbnIAyodtpuLkEc/pub?start=false&loop=false&slide=id.g2b9775219ee_0_57)