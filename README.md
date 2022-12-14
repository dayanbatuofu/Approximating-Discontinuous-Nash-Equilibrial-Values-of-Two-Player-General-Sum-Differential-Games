# Approximating-Discontinuous-Nash-Equilibrial-Values-of-Two-Player-General-Sum-Differential-Games
<br>
Lei Zhang,
Mukesh Ghimire, 
Wenlong Zhang, 
Zhe Xu, 
Yi Ren<br>
Arizona State University

This is the implementation of the paper <a href="https://arxiv.org/abs/2207.01773"> "Approximating-Discontinuous-Nash-Equilibrial-Values-of-Two-Player-General-Sum-Differential-Games"</a>

## Get started
There exists two different environment, you can set up a conda environment with all dependencies like so:

For Toy Case, Collision_avoidance, Uncontrolled_intersection_complete_information_game and Uncontrolled_intersection_incomplete_information_game
```
conda env create -f environment.yml
conda activate siren
```
For BVP_generation
```
conda env create -f environment.yml
conda activate hji
```

## Code structure
There are five folders with different functions
### BVP_generation: use standard BVP solver to collect the Nash equilibrial (NE) values for uncontrolled intersection (case 1) and collision avoidance (case 2) 
The code is organized as follows:
* generate_intersection.py: generate 5D NE values under four player type configurations (a, a), (na, a), (a, na), and (na, na) for case 1.
* generate_collision_avoidance.py: generate 9D NE values for case 2.
* ./utilities/BVP_solver.py: BVP solver.
* ./example/vehicle/problem_def_intersection.py: dynamic, PMP equation setting for case 1.
* ./example/vehicle/problem_def_collision_avoidance.py: dynamic, PMP equation setting for case 2.

run `generate_intersection.py` or `generate_collision_avoidance.py` to collect NE values. Please notice there is four player types in case 1. You should give setting in `generate_intersection.py`. Data size can be set in `./example/vehicle/problem_def_intersection.py` or ./example/vehicle/problem_def_collision_avoidance.py.

### Collision_avoidance: train supervised(SL), self-supervised(SSL), hybrid(HL) and value hardening(VH) model to complete generalization and saftety performance test for case 2
The code is organized as follows:
* dataio.py: load training data for SL, SSL, HL and VH.
* training_supervised.py: contains SL training routine.
* training_selfsupervised.py: contains SSL training routine.
* training_hybrid.py: contains HL training routine.
* training_supervised.py: contains SL training routine.
* training_valuehardening.py: contains VH training routine.
* loss_functions.py: contains loss functions for SL, SSL, HL and VH.
* modules.py: contains layers and full neural network modules.
* utils.py: contains utility functions.
* diff_operators.py: contains implementations of differential operators.
* sim_draw_HD_lane_orientation.py: animation of one case for SL, SSL, HL and VH on paper, reader can dirctly run and watch. Reader needs to create folder `image_recodring` manually.
* sim_draw_transparent_lane_orientation.py: visualization of one case for SL, SSL, HL and VH on paper, reader can dirctly run and watch. Reader needs to create folder `image_recodring` manually.
* ./experiment_scripts/train_collision_HJI.py: contains scripts to train the model, which can reproduce experiments in the paper.
* ./validation_scripts/closedloop_traj_generation_HD_tanh.py: use value network (tanh as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/closedloop_traj_generation_HD_relu.py: use value network (relu as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/closedloop_traj_generation_HD_sine.py: use value network (sine as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/trajectory_with_value_HD_tanh.py: visualize generalization and saftety performance for value network (tanh as activation function).
* ./validation_scripts/trajectory_with_value_HD_relu.py: visualize generalization and saftety performance for value network (relu as activation function).
* ./validation_scripts/trajectory_with_value_HD_sine.py: visualize generalization and saftety performance for value network (sine as activation function).
* ./validation_scripts/model: experimental model in the paper.
* ./validation_scripts/train_data: training data in the paper.
* ./validation_scripts/test_data: testing data in the paper.
* ./validation_scripts/closed_loop: store data by using value network as closed-loop controllers, reader needs to create it manually.

### Toy Case: train supervised(SL), self-supervised(SSL), hybrid(HL) and value hardening(VH) model to visualize the toy case shown in the paper
The code is organized as follows:
* dataio.py: load training data for SL, SSL, HL and VH.
* training_supervised.py: contains SL training routine.
* training_selfsupervised.py: contains SSL training routine.
* training_hybrid.py: contains HL training routine.
* training_supervised.py: contains SL training routine.
* training_valuehardening.py: contains VH training routine.
* loss_functions.py: contains loss functions for SL, SSL, HL and VH.
* modules.py: contains layers and full neural network modules.
* utils.py: contains utility functions.
* diff_operators.py: contains implementations of differential operators.
* ./experiment_scripts/toy_case.py: contains scripts to train the model, which can reproduce experiments in the paper.
* ./validation_scripts/toy_case_value_plot.py: use this script to plot Fig 1(a) in the paper. 
* ./validation_scripts/toy_case_value_hardening_plots.py: use this script to plot Fig 1(b) in the paper. 

### Uncontrolled_intersection_complete_information_game: train supervised(SL), self-supervised(SSL), hybrid(HL) and value hardening(VH) model to complete generalization and saftety performance test for case 1 with complete information
The code is organized as follows:
* dataio.py: load training data for SL, SSL, HL and VH.
* training_supervised.py: contains SL training routine.
* training_selfsupervised.py: contains SSL training routine.
* training_hybrid.py: contains HL training routine.
* training_supervised.py: contains SL training routine.
* training_valuehardening.py: contains VH training routine.
* loss_functions.py: contains loss functions for SL, SSL, HL and VH.
* modules.py: contains layers and full neural network modules.
* utils.py: contains utility functions.
* diff_operators.py: contains implementations of differential operators.
* sim_draw_HD_lane_orientation.py: animation of one case for SL, SSL, HL and VH on paper, reader can dirctly run and watch.
* sim_draw_transparent_lane_orientation.py: visualization of one case for SL, SSL, HL and VH on paper, reader can dirctly run and watch.
* ./experiment_scripts/train_intersection_HJI.py: contains scripts to train the model, which can reproduce experiments in the paper.
* ./validation_scripts/closedloop_traj_generation_HD_tanh.py: use value network (tanh as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/closedloop_traj_generation_HD_relu.py: use value network (relu as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/closedloop_traj_generation_HD_sine.py: use value network (sine as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/closedloop_traj_generation_HD_gelu.py: use value network (gelu as activation function) as closed-loop controllers to generate data including generalization and saftety performance.
* ./validation_scripts/trajectory_with_value_HD_tanh.py: visualize generalization and saftety performance for value network (tanh as activation function).
* ./validation_scripts/trajectory_with_value_HD_relu.py: visualize generalization and saftety performance for value network (relu as activation function).
* ./validation_scripts/trajectory_with_value_HD_sine.py: visualize generalization and saftety performance for value network (sine as activation function).
* ./validation_scripts/trajectory_with_value_HD_gelu.py: visualize generalization and saftety performance for value network (gelu as activation function).
* ./validation_scripts/value_generation_tanh.py: measure the MAEs of value and control input predictions across the test trajectories.
* ./validation_scripts/action_compute_tanh_initial state.py: present measure the MAEs of control input prediction for initial state space.
* ./validation_scripts/action_compute_tanh_expanded state.py: present measure the MAEs of control input prediction for expanded state space.
* ./validation_scripts/value_compute_tanh_initial state.py: present measure the MAEs of value prediction for initial state space.
* ./validation_scripts/value_compute_tanh_expanded state.py: present measure the MAEs of value prediction for expanded state space.
* ./validation_scripts/model: experimental model in the paper.
* ./validation_scripts/train_data: training data in the paper.
* ./validation_scripts/test_data: testing data in the paper.
* ./validation_scripts/closed_loop: store data by using value network as closed-loop controllers, reader needs to create it manually.
* ./validation_scripts/value: store data to measure MAE of value and control input predictions, reader needs to create it manually.

### Uncontrolled_intersection_complete_information_game: use supervised(SL) and hybrid(HL) model to complete incomplete information games for case 1
The code is organized as follows:
* main.py: run the simulatio with initial setting including agent's belief, empathetic or non-empathetic.
* enviroment.py: simulation environment is generated here, using the parameters from main.py.
* savi_simulation.py: initial conditions are processed for the simulation here, such as agent parameters (beta) and action set. The initialization belief table is also done here through the function get_initial_belief().
* inference_model.py: inference is done after observing the state. There are several models implemented here: bvp, baseline, etc. The inference algorithm updates the belief table at each time step using the selected model defined in main.py.
* decision.py: decision model returns an action for each agent, depending on the type of agent defined in main.py. Models include bvp_empathetic, bvp_non_empathetic, baseline, etc.
* plot_loss_traj.py: convert .cvs file into .mat file to generate two-player trajectories projected into d1-d2 frame. 
* modules.py: contains layers and full neural network modules.
* utils.py: contains utility functions.
* diff_operators.py: contains implementations of differential operators.
* ./experiment/store the data of simulation.
* ./validation_scripts/model: experimental model in the paper.
* ./validation_scripts/Hamilton_generation.py: use value network to predict the state in the simulation.
* ./validation_scripts/trajectory_policy_consistent.py: plot two-player trajectories projected into d1-d2 frame when players' initla belief is consistent with their true parameter. 
* ./validation_scripts/trajectory_policy_consistent.py: plot two-player trajectories projected into d1-d2 frame when players' initla belief is not consistent with their true parameter. 

## Contact
If you have any questions, please feel free to email the authors.
