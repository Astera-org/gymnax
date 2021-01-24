## TODOs, Notes & Questions
- [ ] Add timeout condition with env_params and t in state!
- [ ] Episode rollout wrapper
    - [ ] Policy Gradient Wrapper with update only after transition
    - [ ] Q-Learning Wrapper with update after each transition
    - [ ] Deterministic vs. stochastic policy rollout
- [ ] Learn more about setup in dm_env
- [ ] Add TPU speed tests
- [ ] Add more environments
    - [ ] bsuite classics - catch for transfer of catch rlax dqn example
    - [ ] Gridworld/4 rooms
    - [ ] Toy text from gym
    - [ ] Simple bandit environments
- [ ] Add test for transition correctness compared to OpenAI gym
    - [x] Continuous Control
- [ ] Add backdoor for rendering in OpenAI gym
- [ ] Add random policy/sampling for basic rollout
- [ ] Figure out if numerical errors really matter
- [ ] Connect notebooks with example Colab https://colab.research.google.com/github/googlecolab/colabtools/blob/master/notebooks/colab-github-demo.ipynb#scrollTo=K-NVg7RjyeTk


## 19/01/21 - Start working on episode wrappers

- Want a template that wraps around `step`, `reset`, `make` and provides nice `lax.scan` if policy is given in the right format.
    - As much flexibility while giving highest level of abstraction
    - `policy_step` function is where the magic is happening
    - Allow for stochastic rollout
    - Flexible data storage - what are stats to store

- Base wrapper running as well for haiku, flax MLP policies
    - Do we also need a recurrent wrapper?
    - Implement PPO and DQN examples with rlax


## 24/01/21 - Episode wrappers + bsuite catch

- [x] Get rollout wrapper to smoothly integrate with `evosax`
- [ ] Implement bsuite catch env
- [ ] Different types of wrappers?
- [ ] Include timestep in state and terminate/set done

## Next thing to do

- Add another vmap for parameter dimension - useful for ES
- Decide what variables to store and provide specialized wrapper on top
    - Disentangled base wrapper from specialized ones
    - Value based: states, rewards, actions, dones
        - Interleave step with update
        - Add buffer system to store transitions?!
    - PG based: log prob pi, entropy, returns
    - ES: only cumulated rewards
- Implement catch environment from bsuite
- Adopt DQN example from rlax