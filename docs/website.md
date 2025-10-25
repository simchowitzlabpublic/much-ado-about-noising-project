Website outline

Title: Much Ado About Nosing: Dispelling the Myths of Generative Robotic Control

Abstract:
Generative models, like flows and diffusions, have recently emerged as popular and efficacious policy parameterizations in robotics. There has been much speculation as to the factors underlying their successes, ranging from capturing multi-modal action distribution to expressing more complex behaviors.
In this work, we perform a comprehensive evaluation of popular generative control policies (GCPs) on common behavior cloning (BC) benchmarks.
We find that GCPs *do not* owe their success to their ability to capture multi-modality or to express more complex observation-to-action mappings.
Instead, we find that their advantage stems from *iterative computation*, as long as intermediate steps are supervised during training and this supervision is paired with a suitable level of *stochasticity*.
As a validation of our findings, we show that a *minimal iterative policy* (MIP), a lightweight two-step regression-based policy, essentially matches the performance of flow GCPs.
Our results suggest that the distribution-fitting component of GCPs is less salient than commonly believed, and point toward new design spaces focusing solely on control performance.

## Finding1: Neither multi-modality nor policy expressivity account for GCPs’ success

Through careful benchmarkingi over 27 tasks with 3 different input modalities (state, image, point cloud), we found
1. with proper architecture, regression $\approx$ flow in most of tasks
2. flow mainly wins in high precision tasks. 
3. neither multi-modality nor policy expressivity account for GCPs’ success.

(refer to figure static/images/performance.png)

> Carefully align the architecture and training procedure between RCP and GCPs is important. 

## Finding2: After parsing the key ingradient of GCPs, we found noise injection and supervised iterative compute is the key. 

Given a common GCP architecture:

(refer to figure static/images/gcp_architecture.png)


We first expose the key ingredient of GCPs:

(refer to figure static/images/key_ingredient.png)

After benchmarking it on 7 most challenging tasks, we found: *supervised iterative compute + stochasticity injection is the key*.

(refer to figure static/images/results.png)

> For control problem, distribution fitting is less important for final performance. Instead of focusing on action generation itself, it is more important to explore the design space of the mapping from observation to action.

## Finding3: Manifold adherence given out-of-distribution observations is the key 

What benefit do stochasticity injection and supervised iterative compute bring?

We found that it mainly helps the policy to adhere to the manifold of the expert data given *out-of-distribution* observations.

(refer to figure static/images/manifold_adherence.png)