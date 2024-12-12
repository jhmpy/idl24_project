# IDL24 Project

# Deep Reinforcement Learning-Based Mobile Robot Navigation in Social Spaces

# Abstract

Navigating crowded social spaces poses unique challenges for mobile robots, particularly in maintaining safety and adhering to social norms. Traditional navigation approaches, which often treat humans as mere obstacles, fall short in dynamic environments. Deep reinforcement learning has recently made significant strides in developing human-aware navigation policies, but real-world implementation is hindered by constraints in navigation distance and oversimplified environmental assumptions. This paper introduces an enhanced Socially Aware Reinforcement Learning (SARL) framework that addresses these limitations through three innovations. First, it integrates global path planning via a Dijkstra-based algorithm to determine intermediate local goals, ensuring steady progress towards global targets. Second, it refines the action space by screening out unsafe maneuvers through forward velocity simulations and occupancy-grid-based environmental modeling. Third, it leverages a value network architecture employing multilayer perceptrons and a socially attentive pooling mechanism, which processes inputs such as the robot's state and surrounding humans' states to quantify the relative significance of each human in the scene. The output is an optimal, socially compliant navigation policy that enables more natural trajectories. Experimental results demonstrate significant improvements in navigation efficiency, zero-collision performance, and robustness over baseline SARL methods. These findings highlight the feasibility of deploying socially aware reinforcement learning for real-world applications where human-robot coexistence is paramount.


# Setup and Run

The CrowdNav/ folder contains the crowd_sim/ folder that runs the simulation environment and crowd_nav/ folder that contains codes for training and testing the policy.

1. Install [Python-RVO2](https://github.com/sybrenstuvel/Python-RVO2) library
2. From the CrowdNav folder, install crowd_sim and crowd_nav into pip with:
   ```
   pip install -e .
   ```

Go into the crowd_nav/

3. Train the SARL model policy
   ```
   python train.py --policy sarl
   ```
4. Test the policy after training
   ```
   python test.py --policy sarl --model_dir data/output --phase test
   ```
5. Visualize simulation run result of a test case (in this case, test case 0)
   ```
   python test.py --policy sarl --model_dir data/output --phase test --visualize --test_case 0
   ```
6. Plot and visualize trajectory path
   ```
   python test.py --policy sarl --model_dir data/output --phase test --visualize --test_case 0 --traj

# Trajectory Plot

Baseline SARL  &nbsp; &nbsp; &nbsp; &nbsp;  Our SARL
<p float="left">
   <img src="https://github.com/jhmpy/idl24_project/blob/main/crowd_nav/data/output/trajectory_sarl.png" width="500" />
   <img src="https://github.com/jhmpy/idl24_project/blob/main/crowd_nav/data/output/our_sarl_trajectory.png" width="500" />
</p>

