 <div align="center">
  <h2>Optimal Capacity Planning in Service Operations</h2>
  <p><i>An M/M/1/1 Framework for Small Business Revenue Optimization</i></p>
  <p><i>Sudip Khadka</i></p>
  <p><i>Applied Stochastic Processes</i></p>
   <p><i>University of Maryland, College Park</i></p> 
</div>


<hr>

<div align="center">
  <h3>Abstract</h3>
</div>
<p>
  This research develops and validates an analytical framework for revenue optimization in capacity constrained service businesses using M/M/1/1 queuing theory. I modeled a small lawn care business facing stochastic customer demand where limited service capacity necessitates rejection of arriving contracts when busy. Using continuous-time Markov chain analysis and renewal theory, I derive closed-form expressions for expected revenue, lost revenue from rejections, and optimal service rates. I use Monte Carlo simulations with 100 independent replications to validate the theoretical model with errors below 1% across all performance metrics. Sensitivity analysis reveals an inverted U-shaped relationship between arrival rate and net revenue which identifies optimal operating regimes. For the base case (λ=2.0, μ=3.0), the model predicts 40% system utilization and $460/time net revenue, with 40% of arriving contracts rejected. The framework provides actionable decision support for workforce planning, capacity investment, and pricing strategy in data-scarce environments where machine learning approaches are infeasible.
</p>

<h3>1. Introduction</h3>
<h4>1.1 Motivation and Problem Context</h4>
<p>
Machine learning models have achieved remarkable success across diverse applications, from robotics to weather forecasting and fraud detection. However, these data-driven approaches face fundamental limitations in scenarios such as limited foundational knowledge and insufficient training data. In such contexts, analytical models in stochastic process theory offer a powerful alternative for understanding and optimizing complex systems.
 
To operationalize the theory to the practical application, I consided the operational challenge faced by a family owned lawn care business during peak season. The business owner must determine optimal workforce allocation to maximize revenue while minimizing losses from rejected contracts. This problem is compounded by the stochastic nature of customer demand, where contract arrivals are random and service times uncertain. Unlike large-scale operations with extensive historical data suitable for machine learning, small businesses typically lack the data volume necessary for reliable model training and validation. This paper addresses three fundamental questions:
</p>

<div>
<b>1. Performance Prediction:</b> What are the expected revenue, lost revenue, and system utilization given specific arrival and service rates?<br>
<b>2. Capacity Planning:</b> How many contracts exceed acceptable completion times, and what does this imply for workforce sizing?<br>
<b>3. Revenue Optimization:</b> What is the optimal service capacity that maximizes net revenue while accounting for operational costs?
</div>


<h4 style="margin-bottom: 0;">1.3 Modeling Approach</h4>
<p style="margin-top: 0;">
I modeled the business as an M/M/1/1 queuing system, a single server system with no waiting queue where arriving customers finding the server busy are immediately rejected. This "loss system" captures the operational reality of small service businesses unable to maintain contract backlogs. Contracts arrive according to a Poisson process and require exponentially distributed service times, assumptions justified by the memoryless nature of random customer behavior and job complexity uncertainty. I apply continuous-time Markov chain theory and renewal processes to accurately derive revenue metrics that address and correct errors present in the preliminary analysis. Through a comprehensive validation process using event-driven Monte Carlo simulations with 100 replications our model demonstrates high accuracy, achieving less than 1% error across all performance metrics. Furthermore, we conduct sensitivity analyses to identify optimal operating regimes and critical thresholds for arrival and service rates. Finally, our work provides a quantitative decision support framework that guides workforce planning, pricing strategy, and capacity investment decisions.
</p>

<h3>2. Model Formulation</h3>
I modeled the lawn care business as an M/M/1/1 queuing system that represents a single-crew operation with no waiting capacity. In this framework, potential service contracts arrive following a Poisson process N(t) with an arrival rate <i>λ &gt; 0</i>. The service times are assumed to be independent and identically distributed exponential random variables with rate <i>μ &gt; 0</i>. Since the system can accommodate only one job at a time (<i>K = 0</i>), any new contract that arrives while the server is busy is immediately rejected, reflecting a lost-customer scenario.

**Notation:**
- <i>λ</i>: Arrival rate (contracts per time unit)  
- <i>μ</i>: Service rate (contracts per time unit)  
- <i>ρ = λ / μ</i>: Traffic intensity  
- <i>θ</i>: Mean revenue per completed contract  
- <i>η</i>: Mean lost revenue per rejected contract  
- <i>c(μ)</i>: Cost rate as a function of service capacity  
- <i>D</i>: Threshold duration for “long” contracts  

-----
### Preliminaries we will use moving forward: 

**Preliminaries 1:**
The arrival process $N(t)$ is assumed to be a Poisson process with rate $\lambda$, characterized by *stationary independent increments*. Specifically, for any sequence of times $0 \leq t_1 < t_2 < \cdots < t_n$, the increments

$$
N(t_2) - N(t_1), \; N(t_3) - N(t_2), \; \ldots, \; N(t_n) - N(t_{n-1})
$$

are independent random variables. Moreover, the distribution of each increment $N(t+s) - N(s)$ depends only on the length of the interval $t$, and not on the starting point $s$.

**Preliminaries 2:** Let $X(t)$ denote the system state at time $t$:

$$
X(t) = \begin{cases}
1, & \text{if server busy (in service)} \\
0, & \text{if server idle}
\end{cases}
$$

The stochastic process $\{X(t) : t \geq 0\}$ forms a continuous-time Markov chain (CTMC) on the state space $S = \{0, 1\}$. A Markov process on a countable set $S$ is a CTMC if its sample paths are right-continuous and piecewise constant with finite jump times (Serfozo, 2009). Formally, 

$$
X(t) = X_n \quad \text{if} \quad t \in [T_n, T_{n+1}) \text{ for some } n,
$$

where $T_n$ denotes the $n$-th transition time.  

 ** Transition Rate Matrix **

The infinitesimal generator $Q$ of this CTMC is:

$$
Q = \begin{pmatrix}
-\lambda & \lambda \\
\mu & -\mu
\end{pmatrix}
$$

with transition rates:

- $q_{01} = \lambda$ (idle $\rightarrow$ busy when a contract arrives)  
- $q_{10} = \mu$ (busy $\rightarrow$ idle when a contract completes)

**Preliminaries 3:** Under the ergodicity condition ($\lambda, \mu > 0$), the CTMC possesses a unique stationary distribution $\pi = (\pi_0, \pi_1)$ satisfying the global balance equations:

$$
\pi Q = 0, \quad \sum_{i \in S} \pi_i = 1
$$

Solving these equations yields:

$$
\mathbb{P}_0 = \pi_0 = \frac{\mu}{\lambda + \mu}
$$

$$
\mathbb{P}_1 = \pi_1 = \frac{\lambda}{\lambda + \mu}
$$

**Interpretation:**  

- $\mathbb{P}_1$ represents the long-run proportion of time the system is busy (utilization).  
- $\mathbb{P}_0$ represents the long-run proportion of time the system is idle. The traffic intensity $\rho = \frac{\lambda}{\mu}$ relates to utilization as:

$$
\mathbb{P}_1 = \frac{\rho}{1 + \rho}.
$$

---

<h3>3. Revenue Analysis</h3>
<h4>3.1 Completed Contracts: Renewal Reward Theory</h4>

Let $\{T_i : i \geq 1\}$ denote the sequence of contract completion times, and define the counting process:

$$
N(t) = \sum_{i=1}^{\infty} \mathbb{1}(T_i \leq t), \quad t \geq 0
$$

where $N(t)$ counts the number of contracts completed by time $t$. This forms a renewal process with inter-renewal times having a distribution determined by the alternating idle/busy periods.  

Let $Y_i$ denote the revenue from the $i$-th completed contract, assumed to be i.i.d. random variables with mean $\mathbb{E}[Y_i] = \theta$, independent of the process $\{X(t)\}$. The cumulative revenue from completed contracts is:

$$
Z(t) = \sum_{i=1}^{N(t)} Y_i, \quad t \geq 0
$$

This is a compound renewal process. By the renewal reward theorem (Ross, 2014):

$$
\lim_{t \to \infty} \frac{Z(t)}{t} = \frac{\mathbb{E}[Y_1]}{\mathbb{E}[\text{cycle length}]} \quad \text{a.s.}
$$

**Derivation of Completion Rate:**

The system alternates between idle and busy periods. In steady state:

- Proportion of time busy: $P_1 = \frac{\lambda}{\lambda + \mu}$  
- When busy, service completions occur at rate: $\mu$  

Thus, the effective completion rate is:

$$
\frac{\lambda \mu}{\lambda + \mu}
$$

Therefore, the average revenue rate from completed contracts is:

$$
\bar{R}_{\text{complete}} = \theta \cdot \frac{\lambda \mu}{\lambda + \mu}
$$


<h4>3.3 Net Revenue Formulation</h4>

Let $c(\mu)$ denote the cost per unit time of maintaining service rate $\mu$. This cost function typically includes:

- Labor costs (wages for workers/crew)  
- Equipment depreciation and maintenance  
- Overhead allocated to service capacity  

The **net average revenue rate** is:

$$
\bar{Z}(\lambda, \mu) = \bar{R}_{\text{complete}} - \bar{R}_{\text{loss}} - c(\mu)
$$

Substituting the expressions from Sections 3.1 and 3.2:

$$
\bar{Z}(\lambda, \mu) = \frac{\theta \lambda \mu}{\lambda + \mu} - \frac{\eta \lambda^2}{\lambda + \mu} - c(\mu)
$$

Factoring the first two terms:

$$
\bar{Z}(\lambda, \mu) = \frac{\lambda (\theta \mu - \eta \lambda)}{\lambda + \mu} - c(\mu)
$$


<h4>3.4 Optimization Problem</h4>

**Objective:** Determine the optimal service rate $\mu^*$ that maximizes net revenue:

$$
\mu^* = \arg \max_{\mu > 0} \bar{Z}(\lambda, \mu)
$$

Taking the derivative with respect to $\mu$ and setting it equal to zero:

$$
\frac{\partial \bar{Z}}{\partial \mu} = \frac{\theta \lambda^2}{(\lambda + \mu)^2} - c'(\mu) = 0
$$

This yields the first-order optimality condition $\mathrm{c}'(\mu^*)$:

$$
\frac{\theta \lambda^2}{(\lambda + \mu^*)^2}
$$


**Economic Interpretation:**  
At the optimum, the marginal cost of increasing service capacity equals the marginal revenue benefit from reduced utilization and fewer rejections. The denominator $(\lambda + \mu)^2$ reflects diminishing returns — as $\mu$ increases, additional capacity improvements yield progressively smaller reductions in rejection rate.

**Second-Order Condition:** To verify this is a maximum:

$$
\frac{\partial^2 \bar{Z}}{\partial \mu^2} = -\frac{2 \theta \lambda^2}{(\lambda + \mu)^3} - c''(\mu)
$$

If $c''(\mu) \geq 0$ (convex cost function), then $\frac{\partial^2 \bar{Z}}{\partial \mu^2} < 0$, confirming a local maximum.

<h3>4. Contract Duration Analysis</h3>
<h4>4.1 Service Time Distribution</h4>

Service times $\xi_i$ are exponentially distributed with rate $\mu$:

$$
\mathbb{P}(\xi_i > t) = e^{-\mu t}, \quad t \geq 0
$$

The exponential distribution is characterized by the **memoryless property**:

$$
\mathbb{P}(\xi > s+t \mid \xi > s) = \mathbb{P}(\xi > t)
$$

This property is realistic for service operations where the remaining work is independent of elapsed time — job complexity and unforeseen complications make future completion time unpredictable regardless of progress.


<h4>4.2 Long Contract Rate</h4>
Define a long" contract as one exceeding threshold duration $D$. The probability that a randomly selected completed contract is long is:

$$
p_{\text{long}} = \mathbb{P}(\xi > D) = e^{-\mu D}
$$

Since contracts are completed at rate $\frac{\lambda \mu}{\lambda + \mu}$ and each is independently long with probability $e^{-\mu D}$, the rate of long contracts is:

$$
\bar{N}_{\text{long}} = \frac{\lambda \mu}{\lambda + \mu} \cdot e^{-\mu D}
$$

Equivalently, using the stationary distribution:

$$
\bar{N}_{\text{long}} = \mathbb{P}_1 \mu e^{-\mu D}
$$

<h4>4.3 Operational Implications</h4>
The proportion of completed contracts that are long is:

$$
\frac{\bar{N}_{\text{long}}}{\text{completion rate}} = \frac{\mu e^{-\mu D}}{\mu} = e^{-\mu D}
$$

**Decision Rule:**  
If $e^{-\mu D}$ exceeds an acceptable threshold (e.g., 30%), management should:

- Increase service rate $\mu$ through additional staffing  
- Improve operational efficiency via training or equipment  
- Set customer expectations appropriately during booking  
- Implement priority scheduling for time-sensitive contracts

<h3>5. Simulation Methodology</h3>
<h4>5.1 Key Implementation Details:</h4>

- **Random Number Generation:** Exponential random variables generated via inverse transform:  

  $X = -\frac{\ln(U)}{\lambda}, \quad U \sim \text{Uniform}(0,1)$

- **Revenue Variability:** To simulate realistic heterogeneity in contract values, we introduce ±20% uniform variability around the means $\theta$ and $\eta$.

- **Event Ordering:** Events are processed in strict chronological order to maintain causality.

- **Trajectory Recording:** For the first simulation run, the system state is recorded at regular intervals for convergence analysis.

<h4>5.1 Experimental Design / Parameter Configuration:</h4>
    
<div class="table-container">
       
   <table>
            <thead>
                <tr>
                    <th>Parameter</th>
                    <th>Symbol</th>
                    <th>Value</th>
                    <th>Unit</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Arrival rate</td>
                    <td class="math">λ</td>
                    <td>2.0</td>
                    <td>contracts/time</td>
                </tr>
                <tr>
                    <td>Service rate</td>
                    <td class="math">μ</td>
                    <td>3.0</td>
                    <td>contracts/time</td>
                </tr>
                <tr>
                    <td>Traffic intensity</td>
                    <td class="math">ρ</td>
                    <td>0.667</td>
                    <td>dimensionless</td>
                </tr>
                <tr>
                    <td>Mean revenue</td>
                    <td class="math">θ</td>
                    <td>1000</td>
                    <td>$/contract</td>
                </tr>
                <tr>
                    <td>Mean lost revenue</td>
                    <td class="math">η</td>
                    <td>800</td>
                    <td>$/contract</td>
                </tr>
                <tr>
                    <td>Cost rate</td>
                    <td class="math">c</td>
                    <td>100</td>
                    <td>$/time</td>
                </tr>
                <tr>
                    <td>Simulation horizon</td>
                    <td class="math">T<sub>max</sub></td>
                    <td>10,000</td>
                    <td>time units</td>
                </tr>
                <tr>
                    <td>Days threshold</td>
                    <td class="math">D</td>
                    <td>1.0</td>
                    <td>days</td>
                </tr>
            </tbody>
        </table>
    </div>
    
 <h4>Replication Strategy</h4>
    
<p>To ensure statistical reliability and quantify estimation uncertainty, we employ the following replication strategy:</p>
    
<ul>
        <li><span class="emphasis">Number of runs:</span> 100 independent replications</li>
        <li><span class="emphasis">Independence:</span> Each run uses independent random number streams with different seeds</li>
        <li><span class="emphasis">Burn-in period:</span> Results recorded after initial transient (first 1000 time units discarded in trajectory analysis)</li>
        <li><span class="emphasis">Statistical analysis:</span> Mean, standard deviation, and 95% confidence intervals computed across replications using the Central Limit Theorem</li>
    </ul>
    
 <h4>Rationale for Parameter Selection</h4>
    
<p>The parameter choices reflect realistic operating conditions and ensure system stability:</p>
    
   <ul>
        <li><span class="math">ρ</span> = 0.667 &lt; 1: System not overloaded; steady state exists and is stable</li>
        <li><span class="math">T<sub>max</sub></span> = 10,000: Long horizon ensures convergence to steady state and reduces transient effects to negligible levels</li>
        <li>100 runs: Sample size sufficient for detecting errors ≥1% with statistical power &gt; 0.95 at significance level <span class="math">α</span> = 0.05</li>
        <li><span class="math">η/θ</span> = 0.8: Lost revenue approximately 80% of completed revenue, reflecting opportunity cost and customer dissatisfaction</li>
    </ul>
    
   <div class="note">
        <strong>Note:</strong> The traffic intensity <span class="math">ρ</span> = 0.667 places the system in a moderate utilization regime where queuing effects are significant but not extreme, making it ideal for demonstrating model behavior across the full range of system dynamics.
    </div>
    
   <h4>Sensitivity Analysis Design</h4>
    
   <p>To examine robustness and identify optimal operating regimes, we conduct two-dimensional sensitivity analysis by systematically varying arrival and service rates:</p>
    
   <ol>
        <li>
            <span class="emphasis">Arrival rate <span class="math">λ</span>:</span> Range [0.5, 4.5] with 15 equally spaced values, holding <span class="math">μ</span> = 3.0 fixed
            <ul>
                <li>Covers traffic intensities from <span class="math">ρ</span> = 0.17 (underutilized) to <span class="math">ρ</span> = 1.5 (heavily overloaded)</li>
                <li>Reveals the non-monotonic relationship between demand and profitability</li>
            </ul>
        </li>
        <li>
            <span class="emphasis">Service rate <span class="math">μ</span>:</span> Range [1.5, 5.5] with 15 equally spaced values, holding <span class="math">λ</span> = 2.0 fixed
            <ul>
                <li>Spans capacity from inadequate (<span class="math">μ</span> &lt; <span class="math">λ</span>) to generous (<span class="math">μ</span> &gt; 2<span class="math">λ</span>)</li>
                <li>Identifies optimal capacity investment levels</li>
            </ul>
        </li>
    </ol>
    
   <p>For computational efficiency, sensitivity runs use <span class="math">T<sub>max</sub></span> = 5000 and 20 replications per parameter value. This reduced configuration maintains adequate precision (standard errors &lt; 2% of mean) while enabling comprehensive parameter space exploration.</p>
    

   <h4>5.2 Validation Metrics:</h4>
    
   <p>We validate the model by comparing simulated results against theoretical predictions for the following performance metrics:</p>
    
   <div class="table-container">
        <p class="caption">Table 3: Validation Metrics</p>
        <table>
            <thead>
                <tr>
                    <th>Metric</th>
                    <th>Theoretical Formula</th>
                    <th>Interpretation</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Utilization</td>
                    <td class="math">P<sub>1</sub> = λ/(λ+μ)</td>
                    <td>Long-run fraction of time busy</td>
                </tr>
                <tr>
                    <td>Completion rate</td>
                    <td class="math">λμ/(λ+μ)</td>
                    <td>Contracts completed per time unit</td>
                </tr>
                <tr>
                    <td>Rejection rate</td>
                    <td class="math">λ<sup>2</sup>/(λ+μ)</td>
                    <td>Contracts rejected per time unit</td>
                </tr>
                <tr>
                    <td>Revenue rate</td>
                    <td class="math">θλμ/(λ+μ)</td>
                    <td>Revenue earned per time unit</td>
                </tr>
                <tr>
                    <td>Loss rate</td>
                    <td class="math">ηλ<sup>2</sup>/(λ+μ)</td>
                    <td>Revenue lost per time unit</td>
                </tr>
                <tr>
                    <td>Net revenue rate</td>
                    <td class="math">[θλμ - ηλ<sup>2</sup>]/(λ+μ) - c</td>
                    <td>Profit per time unit</td>
                </tr>
                <tr>
                    <td>Long contracts rate</td>
                    <td class="math">[λμ/(λ+μ)]e<sup>-μD</sup></td>
                    <td>Contracts exceeding D days per time</td>
                </tr>
            </tbody>
        </table>
    </div>
    
   <p>For each metric, we compute the percentage error as:</p>
    
   <p style="text-align: center; margin: 20px 0;">
        <span class="math">Error = |Theoretical - Simulated Mean| / |Theoretical| × 100%</span>
    </p>
    
   <p>Model validation is deemed successful if all metrics exhibit errors below 5%, with typical errors expected below 1% given the large sample size and long simulation horizon.</p>
    
</body>
</html>

<h3>6. Results</h3>

<img src="https://github.com/sudkc37/Stochastic-Modeling/blob/master/Results/Distributions.png" alt="Screenshot 2024-12-09 at 2 17 15 PM" width="1000" height="800">

<img src="https://github.com/sudkc37/Stochastic-Modeling/blob/master/Results/sensitivity-analysis.png" alt="Screenshot 2024-12-09 at 2 17 15 PM" width="1000" height="700">


<h3>1. Reference </h3>
Serfozo, Richard. Basics of Applied Stochastic Processes. Springer Berlin Heidelberg, 2009.
