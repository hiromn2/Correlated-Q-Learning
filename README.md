# Q-Learning with Messages
Advanced ML Project: does Q-learning algorithm learn correlated equilibrium if given the right messages? 

## Features
- Stateless Q-learning approach that stores action values without explicit states.
- Variation of the benchmark algorithm by Q-values being conditional on a message
- Optional decreasing exploration Boltzmann policy
- The code was written from scratch with the help of Chat GPT to solve minor issues

All the data comes from simulations, so there is no need to install anything to run the code. 

- Q-Learning with Messages.ipynb produces the results in section 3 (it takes more than 4 hours to run this code).
- cond_Q_learn_opt_v2.ipynb produces the results in section 4 in the case of only public messages.
- cond_Q_learn_opt_private_V2.ipynb produces the results in section 4 in the case of private messages.
- Correlated Q-Learning Private Msgs.ipynb produces time-series graphs of the mixed-strategy and were not featured in the text.
- Q_learn_v2.ipynb is the prototype of the Q-learning with messages algorithm, where we explore different parametrizations.

Mateus Hiro Nagata, Francesco Giordano
