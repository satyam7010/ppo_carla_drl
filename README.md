1 Carl-Lead: Lidar-based End-to-End Autonomous Driving with Contrastive Deep Reinforcement Learning
https://paperswithcode.com/paper/carl-lead-lidar-based-end-to-end-autonomous

2 Safe and Generalized End-to-end Autonomous Driving System with Reinforcement Learning and Demonstrations
https://paperswithcode.com/paper/safe-and-generalized-end-to-end-autonomous

A Bayesian Approach to Reinforcement Learning of Vision-Based Vehicular Control
https://paperswithcode.com/paper/a-bayesian-approach-to-reinforcement-learning



Hi Singh,

Thanks for your attention to our work! DRL is notorious for its low sample efficiency. Therefore, there is sure something to pay attention when you train Cadre.
1) Set `num_processes` under config_files/agent_config.py as 4 (at least) and use different route schedules (e.g., Nocrash_follow_lane_ture_route.xml for process0, Nocrash_right_turn_route.xml for process1 …) for each process. Using more subprocesses increases training efficiency. In our machine (8 RTX3090 GPUs, 750GB memory), achieving a good driving policy typically takes around one day with 4 subprocesses.
2) Use an ensembled policy for evaluation. In my test, training for 3000 episodes, using the latest 8 models (saving every 100 episodes), and averaging their output will increase the robustness of the driving policy. Here is the reproduced result of mine using the reorganized code. I’ll update an official model checkpoint after my paper deadline on the 15th. 

Feel free to contact me if you have other questions.

Best regards.
Yinuo Zhao.



