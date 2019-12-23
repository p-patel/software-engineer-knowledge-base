# Feature Switching and Branching By Abstraction
https://www.youtube.com/watch?v=lqRQYEHAtpk

- CI => integrate work regularly (CI is defined as integrating daily)
- Big merges = commit race!
- "trunk-based development" / branching by abstraction - http:trunkbaseddevelopment.com
  - Zookeeper / Consul - run-time configuration
  - branch-by abstraction
    - use flag in as few places as possible (one!)
    - remove once you're done
    - can also be used for A/B testing (or beta testers user group)
    - (with some work) canary releasing
  - treat every check-in as a release candidate
  - Ops Meta-Metrics - John Allspaw
  - Split.io
  - DevOps Handbook - Kim, Humble, Debois, Willis
  - Integrate often, keep batch size small, ship often (unconvinced that using branches for features is a good idea)
