##  Modeling Revenue Projection Via Queuing Process / Workforce Forecasting for a Lawn Care Business


**Project Description**
This project aims to assist a family-owned small lawn care business in forecasting workforce requirements to balance labor costs and revenue. The goal is to:

Predict the average revenue generated with a specific number of workers and a given contract completion rate (μ).
Calculate the potential revenue loss due to under- or overstaffing.
Identify how many contracts might exceed a certain time threshold to completion.


The business faces the challenge of unpredictable contract acquisition and a sequential, first-in-first-out (FIFO) contract processing system. This model seeks to provide actionable insights based on stochastic contract behaviors.


**Our Model Assumptions**
    - Poisson Process: Contracts arrive according to a Poisson process with rate λ, characterized by stationary and independent increments.

    - Exponential Service Times: The time required to complete each contract is independently exponentially distributed with rate μ.

    - Queue Discipline: Contracts are processed sequentially following a First-In-First-Out (FIFO) order.

    - Independent Events: Contract arrivals and service times are statistically independent.


**Methodology**

To address these questions, the project employs the following techniques:

**Queueing Theory**
- The system is modeled as an M/M/1 queue, where:
    - Arrival process follows a Poisson distribution.
    - Service times are exponentially distributed.
    - One server (worker or team) processes contracts sequentially.

**Simulation and Analysis**
    - Simulate the arrival and processing of contracts to capture dynamic system behavior.
    - Compute key performance indicators (KPIs) like average queue length, waiting time, and system utilization.

**Revenue and Risk Analysis**
    - Estimate revenue based on worker availability and completion rates.
    - Quantify revenue loss due to understaffing or overstaffing.
    - Assess contract delays exceeding a specified time threshold.