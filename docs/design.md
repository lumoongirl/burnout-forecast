# Design Overview

This document describes the high-level design of the Burnout Forecast project.

The system ingests daily behavior logs, transforms them into interpretable
features, and outputs a daily burnout risk score with explanations.

Why local-first instead of cloud?

As a student working with personal wellbeing data, I prioritised privacy and control over convenience. A local-first design ensures sensitive behavioural data (sleep, work patterns, energy levels) never leaves the device by default. It also keeps the system simpler and cheaper to run, which is appropriate for a solo student project.
If this were ever extended into a larger product, cloud sync could be added later as an opt-in feature, but starting local avoids unnecessary risk and complexity.

Why rule-based baseline before ML?

I intentionally started with a rule-based baseline to establish a clear, explainable reference point before introducing machine learning. This makes it easier to validate whether later models are actually adding value rather than just complexity.
As a student, this approach helps me reason about the problem domain first, build intuition, and avoid treating ML as a black box. It also ensures the system produces meaningful outputs even with small datasets.

Why interpretability over accuracy?

For a wellbeing-focused system, understanding why a prediction is made is more important than maximising raw accuracy. A slightly less accurate but interpretable model allows users to reflect on their behaviour and take informed action.
As a student project, prioritising interpretability also demonstrates good engineering judgement: choosing solutions that are appropriate to the problem context rather than optimising a single metric.

Why demo data instead of real logs?

Using demo data allows the full pipeline to be shared and reviewed publicly without exposing personal or sensitive information. This is especially important for a student portfolio project that may be viewed by recruiters or interviewers.
The demo dataset is designed to be realistic enough to demonstrate functionality, while real personal logs are intentionally kept private and excluded from version control.

Why these signals and not others?

The chosen signals (sleep, workload, session patterns, context switching, and self-reported energy) are:

easy to measure consistently as a student

directly connected to burnout risk in everyday academic life

simple enough to reason about and explain

I deliberately avoided signals that require specialised hardware or intrusive tracking, as the goal was to build something practical and sustainable rather than exhaustive.
