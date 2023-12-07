# Introduction
This is the GitHub repository containing the jupyter notebook files that we used for our 175 final project. For our project, we experimented with three different approaches (REINFORCE, Double Deep Q-Learning, and Proximal Policy Optimization) to train an agent to complete a level in Super Mario Bros. As such, out project is split into three main Jupyter notebooks, one for each approach. We also experimented with modifying the reward function of the environment to encourage the agent to collect coins or kill enemies. We used the change in overall score multipled by a small constant added to the reward function to achieve this. Consequently, we trained models using either 1/10 or 1/50 as the constants and examined the differences in the behavior of the agent.  

# Notes
Unfortunately, we were unable to save the models that we trained themselves, due to either space limitations (the PPO models were collectively many gigabytes), or for the lack of implementation to save/load models to the disk. We trained the models in Jupyter Notebook and extracted the results on the same Kernel. Due to time constraints, we were unable to reimplement/retrain the models to a satisfying degree. However, we do have videos and graphs to showcase the models' performance.

# Project Components

| Filename | Description |
| ------ | :-----------|
| reinforce.ipynb | notebook for the REINFORCE approach |  
| ppo.ipynb | notebook for the PPO approach |
| DQL.ipynb | notebook for the Double Deep Q-Learning approach |
| dqn_logs | folder containing the log files (reward plot, loss plot, etc.) for each of the dqn models we trained. The internal folders dqn10, dqn50, and dqnfinal correspond to the models trained with a score multiplier of 1/10, 1/50, and the final dqn model we trained respectively. |
| logs | This folder contains the log files for the PPO models we trained. The internal folders PPO_10 and PPO_50 correspond to the models trained with a score multipler of 1/10 and 1/50 respectively. To view the log files for PPO, see below or the ppo.ipynb notebook for instructions. |
| replay_METHOD_VERSION.mp4 | These files are the recordings of an example run done by each of the models. METHOD corresponds to the method used to train the model (dqn, ppo, or reinforce), and VERSION corresponds to the score multipler used for training (10 for 1/10, 50 for 1/50, and final for the final dqn model) |
| ppo_avg_VERSION.txt | These are text files to store the outputs of the average rewards for each checkpoint model while training the PPO method. This file is used to generate the change in reward graph for the PPO models. |

# Setup
Although we were able to use the latest software libraries and dependencies for the REINFORCE and DDQL approaches, the PPO approach required a specific subset of versions to ensure compatability (`stable-baselines3` and `gym-super-mario-bros` were incompatible). The following commands will assume that you have a windows or mac machine with the latest version of miniconda (or anaconda).

## FOR REINFORCE AND DQL USE THE FOLLOWING ENVIRONMENT (ORDER MATTERS)
```
conda create -n myenv
conda activate myenv
conda install jupyter notebook matplotlib pandas numpy
***install pytorch based on your machine through CONDA***
pip install gym-super-mario-bros opencv-python imageio
pip install "imageio[ffmpeg]"
pip install tensordict torchrl
```

## FOR PPO USE THE FOLLOWING ENVIRONMENT (ORDER MATTERS)
```
conda create -n myenv2 python=3.9.16
conda activate myenv2
pip install setuptools==65.5.0 "wheel<0.40.0"
pip install stable-baselines3==1.6.0
pip install gym-super-mario-bros opencv-python imageio
pip install "imageio[ffmpeg]"
***install pytorch based on your machine through PIP***
pip install tensorboard
conda install jupyter notebook matplotlib pandas numpy
```

## TO VIEW PPO LOG FILES
`cd` into the path containing the PPO log file (/logs/PPO_#) and use the following command:  
`tensorboard --logdir=.`