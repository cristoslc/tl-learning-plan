---
source-id: "schwarz-adaptive-competency-placement"
title: "A Computerized Adaptive Competency-Based Placement Test to Determine the Optimal Entry Point in Online Courses"
type: web
url: "https://link.springer.com/chapter/10.1007/978-3-031-93409-4_15"
fetched: 2026-04-10T14:30:00Z
notes: "Paywalled — abstract and references only. Full chapter would require institutional access."
---

# A Computerized Adaptive Competency-Based Placement Test to Determine the Optimal Entry Point in Online Courses

**Authors**: Kim Alexa Schwarz, Sylvio Rüdian, Christian Kellermann  
**Venue**: AIEER 2024, Communications in Computer and Information Science, vol 2519, Springer, 2025  
**DOI**: https://doi.org/10.1007/978-3-031-93409-4_15

## Abstract

Personalization in online learning exists in several domains (language, chemistry, math) but rarely beyond. Due to fixed learning progressions, enrolled learners must complete entire courses to succeed. Learners' prior knowledge is often not considered, leading to disengagement when task difficulty doesn't align with their skills.

This paper introduces a placement test to estimate learners' competency levels employing Item Response Theory (IRT). The authors implement a computerized competency-based adaptive placement test in real-world online courses on the KI-Campus platform.

Key contributions:
- Demonstrates how to identify a **domain-independent, optimal course entry point** tailored to the learner
- Addresses challenges of applying IRT with multiple competencies in a real-world setting
- Promises to optimize learning time by accounting for prior knowledge, potentially reducing dropout rates

## Relevance

This is directly aligned with our use case: using adaptive assessment to determine where a learner should *start* in a learning progression, rather than forcing everyone through the same fixed path. The paper addresses:
- Multi-competency IRT models for placement
- Domain-independent entry point identification
- Real-world implementation challenges
- Connection between appropriate placement and reduced dropout

## Key References from the Paper

- Schwarz et al. use IRT (1-parameter Rasch model and extensions) for adaptive item selection
- Reference to Csikszentmihalyi's flow theory: optimal engagement occurs when challenge matches skill
- Reference to Kirschner & van Merriënboer (2013): "Do learners really know best?" — cautioning against pure learner autonomy without scaffolding
- Reference to Choi & McClenen (2020): Adaptive formative assessment using CAT and dynamic Bayesian networks
- Reference to Zhuang et al. (2022): Neural CAT for online education — fully adaptive framework

## Connection to Our Work

This paper represents the state of the art in applying IRT-based adaptive placement to online learning. It demonstrates that placement testing for optimal entry points is not just theoretical but being implemented in production learning platforms. The emphasis on domain independence (not tied to a single subject) and the connection to dropout reduction reinforces the value proposition of pedagogical scaffolding for starting-point determination.