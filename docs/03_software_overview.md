# 3. Software overview

> **BTH is a research prototype, not a medical device.**

The software is a means to an end. This page describes what each stage is for, not how it works.

```
acquire  ->  condition  ->  estimate state  ->  adapt assistance  ->  safety
```

1. **Acquire.** Read the autonomic sensors and the motion sensors with a common time base.
2. **Condition.** Check signal quality and reject or flag artefacts. When signal quality is not good enough,
   the system says so and does not produce an estimate.
3. **Estimate state.** A deterministic index summarises the patient's physiological state. It is the
   data-acquisition foundation, not the product.
4. **Adapt assistance.** Propose a change in how much the exosuit assists. The adaptive component proposes;
   it never drives the motor directly.
5. **Safety.** Deterministic limits check every proposal. Hardware limits sit below the software and cannot
   be overridden by it. A clinician supervises and can stop the session.

## Personalisation concept

The goal is a patient-specific model: one that learns each patient's own autonomic baselines over sessions
and adapts assistance to that patient, rather than applying population thresholds. How it learns and how
state is turned into assistance are not described here.

Status: the concept is implemented only against a simulator. It has not been tested on any person.

## Governance

A separate governance layer constrains and audits the adaptive component. It is described in its own showcase: [bth-governance-showcase](https://github.com/yasferaru/bth-governance-showcase).

## Interfaces

A backend and a clinician dashboard exist for running sessions and reviewing them. They are ordinary
engineering and are not the subject of this repository.
