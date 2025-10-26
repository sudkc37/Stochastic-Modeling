 <div align="center">
  <h2>Optimal Capacity Planning in Service Operations</h2>
  <p><i>An M/M/1/1 Framework for Small Business Revenue Optimization</i></p>
  <p><i>Sudip Khadka</i></p>
</div>

<hr>

<div align="center">
  <h3>Abstract</h3>
</div>
<p>
  This research develops and validates an analytical framework for revenue optimization in capacity constrained service businesses using M/M/1/1 queuing theory. I modeled a small lawn care business facing stochastic customer demand where limited service capacity necessitates rejection of arriving contracts when busy. Using continuous-time Markov chain analysis and renewal theory, we derive closed-form expressions for expected revenue, lost revenue from rejections, and optimal service rates. I use Monte Carlo simulations with 100 independent replications to validate the theoretical model with errors below 1% across all performance metrics. Sensitivity analysis reveals an inverted U-shaped relationship between arrival rate and net revenue which identifies optimal operating regimes. For the base case (λ=2.0, μ=3.0), the model predicts 40% system utilization and $460/time net revenue, with 40% of arriving contracts rejected. The framework provides actionable decision support for workforce planning, capacity investment, and pricing strategy in data-scarce environments where machine learning approaches are infeasible.
</p>

<h3>1. Introduction</h3>
<h4>1.1 Motivation and Problem Context</h4>
<p>
Machine learning models have achieved remarkable success across diverse applications, from robotics to weather forecasting and fraud detection (Goodfellow et al., 2016). However, these data-driven approaches face fundamental limitations in scenarios characterized by limited foundational knowledge and insufficient training data. In such contexts, analytical models grounded in stochastic process theory offer a powerful alternative for understanding and optimizing complex systems.
 
We consider the operational challenge faced by a family-owned lawn care business during peak season. The business owner must determine optimal workforce allocation to maximize revenue while minimizing losses from rejected contracts. This problem is compounded by the stochastic nature of customer demand, where contract arrivals are random and service times uncertain. Unlike large-scale operations with extensive historical data suitable for machine learning, small businesses typically lack the data volume necessary for reliable model training and validation. This paper addresses three fundamental questions:
</p>

<div>
<b>1. Performance Prediction:</b> What are the expected revenue, lost revenue, and system utilization given specific arrival and service rates?<br>
<b>2. Capacity Planning:</b> How many contracts exceed acceptable completion times, and what does this imply for workforce sizing?<br>
<b>3. Revenue Optimization:</b> What is the optimal service capacity that maximizes net revenue while accounting for operational costs?
</div>


<h4 style="margin-bottom: 0;">1.3 Modeling Approach</h4>
<p style="margin-top: 0;">
We model the business as an M/M/1/1 queuing system—a single-server system with no waiting queue where arriving customers finding the server busy are immediately rejected. This "loss system" captures the operational reality of small service businesses unable to maintain contract backlogs. Contracts arrive according to a Poisson process and require exponentially distributed service times, assumptions justified by the memoryless nature of random customer behavior and job complexity uncertainty.
</p>


