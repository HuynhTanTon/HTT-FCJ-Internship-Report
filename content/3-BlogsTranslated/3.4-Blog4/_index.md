---
title: "DynamoDB counters"
date: 2026-07-14
weight: 4
chapter: false
pre: " <b> 3.4. </b> "
---

# Implement resource counters with Amazon DynamoDB

#### 1. Source information

| Item | Details |
| --- | --- |
| Original title | Implement resource counters with Amazon DynamoDB |
| Source | [AWS Database Blog](https://aws.amazon.com/blogs/database/implement-resource-counters-with-amazon-dynamodb/) |
| Topics | Atomic counters, `UpdateItem`, ConditionExpression, concurrency accuracy |

#### 2. Summary

The article examines **resource counters** on DynamoDB (votes, inventory, tickets) under concurrent updates. It compares approaches on accuracy, cost, and complexity — from simple **atomic counters** with `UpdateItem`/`ADD` and optional ConditionExpressions, to optimistic concurrency, transactions with client request tokens, and counting via item collections / sets. A key theme: handle 500-series ambiguity (did the update apply?) and choose retry strategies to avoid over/undercounting.

#### 3. Main content

**3.1. Atomic counters** — one `UpdateItem` increments/decrements; DynamoDB serializes item updates. Optional conditions (e.g. never go below zero). Cheap and simple; lower accuracy than transactional patterns under complex failure/retry — fine when approximation or simple conditions are enough.

**3.2. Conditions and thresholds** — ConditionExpression rejects updates that would violate state rules.

**3.3. Advanced directions** — OCC, TransactWriteItems + client request token, marker items for higher accuracy / idempotency.

#### 4. Reflection (project link)

Maps directly to `clickCount` in my redirect handler:

- `UpdateCommand` / atomic increment instead of Get-then-Put (fewer races).
- `ConditionExpression: attribute_exists(shortCode)` → missing codes fail cleanly (404) instead of creating stray items.
- For the lab, an atomic counter is enough to demonstrate clicks; the blog explains why that pattern is sound and when transactions become necessary for stricter counting (e.g. sellable inventory).
