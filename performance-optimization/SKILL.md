---
name: performance-optimization
description: Use for performance investigations and improvements. Focuses on measurement-driven optimization, identifying bottlenecks, and avoiding unnecessary complexity.
---

# Performance Optimization

Use when improving:

- Latency
- Throughput
- CPU usage
- Memory usage
- Database performance
- Scalability

---

# Measure first

Before optimization:

Identify:

- Current performance.
- Bottleneck location.
- Expected improvement.
- Measurement method.

Do not optimize based only on assumptions.

---

# Optimization priorities

Prefer:

1. Remove unnecessary work.
2. Improve algorithms.
3. Reduce expensive operations.
4. Optimize data access.
5. Improve caching where appropriate.

---

# Avoid premature optimization

Do not:

- Add complexity without measurement.
- Introduce caching without invalidation strategy.
- Optimize rarely used paths.
- Sacrifice correctness.

---

# Verification

After changes:

Measure:

- Before vs after performance.
- Resource usage.
- Correctness impact.

---

# Final response

Include:

- Bottleneck identified
- Measurement method
- Optimization applied
- Performance impact
- Trade-offs
- Remaining risks