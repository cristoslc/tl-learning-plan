---
source-id: "cogn-iq-adaptive-testing"
title: "Adaptive Testing in Psychometrics — Definition & Examples"
type: web
url: "https://www.cogn-iq.org/learn/theory/adaptive-testing/"
fetched: 2026-04-10T14:15:00Z
---

# Adaptive Testing in Psychometrics

## Overview

Adaptive testing (Computer Adaptive Testing / CAT) dynamically adjusts question difficulty based on test-taker responses. Using Item Response Theory (IRT), it selects optimal items in real-time to efficiently measure ability with fewer questions than traditional fixed-form tests while maintaining or improving measurement precision.

Key benefits:
- Reduces testing time by up to 50% compared to traditional tests
- Provides more precise ability estimates across the ability spectrum
- Widely used in GRE, GMAT, and clinical assessments

## How Adaptive Testing Works

### The Adaptive Process

1. Set initial ability estimate (typically population mean θ₀)
2. Select most informative item from calibrated bank at current θ
3. Present item and record response
4. Update ability estimate (MLE or Bayesian methods)
5. Check stopping rules — if sufficient precision, stop; otherwise return to step 2

### Item Selection Algorithms

- **Maximum Information**: Selects items providing most statistical information at current ability estimate
- **Randomized within optimal range**: Enhances test security
- **Content balancing**: Ensures coverage of all domains
- **Exposure control**: Prevents overuse of certain items

### Stopping Rules

- **Fixed-length**: Predetermined number of items
- **Precision-based**: Continues until standard error falls below threshold
- **Hybrid**: Combines multiple criteria, balancing efficiency with practical constraints

## IRT Foundation

Item Response Theory models the probability of a correct response as a function of both person ability (θ) and item characteristics:

- **Difficulty (b)**: Ability level at which examinee has 50% probability of correct response
- **Discrimination (a)**: How well an item differentiates between examinees of different abilities
- **Pseudo-guessing (c)**: Probability of correct response by random guessing

### Information Functions

Items provide maximum information when difficulty matches examinee ability. The test information function (sum of item information functions) indicates measurement precision across the ability continuum.

### Ability Estimation Methods

- **Maximum Likelihood Estimation (MLE)**: Finds ability value maximizing likelihood of observed response pattern
- **Bayesian (EAP, MAP)**: Incorporates prior distributions for stable early estimates
- **Weighted Likelihood Estimation (WLE)**: Addresses MLE bias for extreme response patterns

## Applications

- GRE (section-level adaptation)
- GMAT (item-level adaptation)
- NCLEX-RN nursing licensure (CAT)
- PROMIS health outcomes assessment
- Military recruitment (CAT-ASVAB)
- Corporate assessment for employee selection

## Challenges and Limitations

| Challenge | Solution |
|---|---|
| Item bank requirements | Collaborative development, automated item generation |
| Content balance | Content constraints, shadow testing algorithms |
| Test anxiety (can't review) | Optional review stages, clear instructions |
| Score comparability | IRT scaling, equating procedures |
| Technical infrastructure | Cloud-based solutions, redundancy planning |
| Initial development costs | Phased implementation, shared platforms |

## Future Directions

- Multidimensional adaptive testing for complex constructs
- Machine learning integration for improved item selection
- Adaptive testing with constructed response items
- Real-time learning analytics and diagnostic feedback
- Mobile-optimized adaptive assessments

## References

- van der Linden & Glas (2010). Elements of Adaptive Testing. Springer.
- Wainer et al. (2000). Computerized Adaptive Testing: A Primer. Lawrence Erlbaum.
- Embretson & Reise (2000). Item Response Theory for Psychologists. Lawrence Erlbaum.