# machine learning
0. Learning From Data, Not Rules:
1. compare with traditional programmi:
traditional programmi: 
you write the rules, the program apply to data to product output.
machine learning:
you provide data and expected outputs, the algorithm discover rules.
3. learned result:
The "model" that comes out of training IS the rules, 
encoded as numbers (weights, parameters), 
then could make predictions on data it has never seen.

# learning paradigms
4. 3 basic learn paradigm: supervised, unsupervised, reinforcement.
5. 2 mixed learn paradigm: Semi-supervised and Self-supervised.
## supervied leaning
You have input-output pairs. 
The model learns to map inputs to outputs.
1. classification
2. regression
## unsupervised learning
You have inputs only. No labels. 
The model finds structure on its own.
1. clustering
2. dimensionality reduction
## reinforcement learning
An agent actions in an environment and receives rewards or penalties. 
It learns a strategy (policy) to maximize total reward.
1. policy optimization
2. value learning
## Semi-supervised learning
uses a small set of labeled data and a large set of unlabeled data.
## Self-supervised learning
creates supervision from the data itself without human labels at all.
model creates its own prediction task from the structure of the data.


# learning methods

## neural-network-based
### shallow learning
- Perceptron
- Single-hidden-layer MLP
### deep learning
- CNN
- RNN / LSTM
- Transformer
- Diffusion

## statistical
- linear models
- probabilistic models
- Bayesian methods

## kernel-based
- SVM
- kernel regression

## tree-based
- decision trees
- random forests
- gradient boosting

## instance-based
- KNN
- case-based reasoning

## ensemble
- bagging
- boosting
- stacking

## evolutionary / swarm-based
- genetic algorithms
- PSO
- ACO

## rule-based / logic-based
- association rules
- ILP
- fuzzy rules

## matrix factorization
- SVD
- ALS

