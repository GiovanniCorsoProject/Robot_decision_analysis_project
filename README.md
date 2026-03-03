# Robot_decision_analysis_project
Introduction

This project explores how different models of decision-making influence the behavior of autonomous agents operating in exploratory environments.

In real-world scenarios, intelligent systems rarely act under perfect certainty. Sometimes they possess complete information and can optimize deterministically. In other situations, they must balance exploration and exploitation. In more complex cases, they operate under uncertainty and must protect themselves against potentially adverse outcomes.

To investigate these differences, three simulated robots are designed and compared. Each robot repeatedly faces mission choices characterized by three parameters:

Benefit – the expected positive outcome of the mission
Cost – the resources required to execute it
Stress – a negative psychological or operational burden

Although all robots evaluate the same mission options, they differ fundamentally in how they interpret and process the available information.

All three robots rely on the same underlying evaluation model: V = V1*benefit - V2 *cost + V3*stress 
The weights V1,V2,V3 are set to 1 by default, meaning that benefit, cost, and stress are equally influential in determining the mission value.

What distinguishes the robots is not the value function itself, but how they use it.

THREE DECISION STRATEGY
Robot 1 – Deterministic Maximizer

Robot 1 represents a fully rational agent with complete and exact information.
For each decision round, it computes the value of every available option and selects the one with the highest score. If multiple options share the same maximum value, it breaks ties randomly.
This agent embodies classical rational choice theory: given perfect information, it always chooses the optimal solution.

Robot 2 – Probabilistic Explorer

Robot 2 also has access to exact information, but its decision process is intentionally stochastic.
Instead of selecting the maximum deterministically, it transforms the computed values into probabilities using a softmax function. This introduces a controlled degree of randomness regulated by a parameter called instinct (default value: 1.25).
Lower instinct values make Robot 2 behave similarly to Robot 1.
Higher values increase exploration, allowing the robot to occasionally select suboptimal options.

Robot 3 – Conservative Agent Under Uncertainty

Robot 3 operates under a different assumption: it does not trust the exact values provided.
Instead, it assumes that each parameter may vary within an uncertainty interval:

lower = value/range_factor
upper = value/range_factor

With a default range_factor = 2.66, Robot 3 acknowledges substantial uncertainty around each mission parameter.
Given this incomplete knowledge, it adopts a worst-case (maximin) strategy. For each option, it evaluates the minimum guaranteed outcome by considering:
-the smallest possible benefit
-the largest possible cost
-the most negative stress

Unlike Robot 2, it does not explore randomly. Unlike Robot 1, it does not assume certainty. It protects itself against potential adverse conditions.

Experimental Structure

The simulation consists of four independent scenarios.
For each scenario:
-The user defines three mission options.
-The system runs 1000 independent decision rounds.
-Each robot selects an option in every round.
-The program records absolute frequencies and selection percentages.
-Results are printed and displayed through comparative bar charts.
-The user proceeds to the next scenario.


The comparison highlights a fundamental principle in decision theory:
Rational behavior depends on the structure and reliability of available information.
When information is certain, maximization is natural.
When variability is allowed, probabilistic exploration emerges.
When uncertainty dominates, conservative strategies become rational.
The project therefore serves as a simplified but meaningful illustration of how information constraints reshape intelligent behavior.
