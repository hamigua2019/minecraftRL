# 大作业 minecraftRL

一、任务描述

本次作业是利用强化学习方法提高agent打Minecraft游戏的表现，至少需要实现两个baselines，并改进已有模型或创造自己的模型参赛。

二、所做的工作，成果及问题

总体来说，本次耗费了较多时间在配置环境上，导致最后真正训练模型和阅读论文的时间较少。

经过多时尝试，发现带docker的亚马逊环境不可用，在亚马逊中，不带docker自行配置的环境也出现了无法解决的bug，不带亚马逊的本机环境也出现bug，最后尝试，只有本机加docker的环境在ppo.py的情况下才可能成功。需要expert dataset数据集的三个py文件，在本机没有服务器的情况下很难run成功。由此，在有限的时间和机器配置下，仅运行了ppo.py文件，这个文件在没有gpu的条件下需要至少60个小时才能运行完，所以尚未得出最后的结果。此外，按照要求，应该至少实现两个baselines分别三个环境的调试，现在仅实现第一个模型的第一个环境。

虽然如此，仅有一个baselines可以实现，但结合竞赛的GitHub资料和几篇相关paper，也不妨碍我们能够把握baselines模型的作用和意义。

三、ppo算法与rainbow的理解及比较

阅读rainbow论文、ppo论文以及，可知这几种模型的创新提升点之所在。

PPO算法是一种新型的Policy Gradient算法，Policy Gradient算法对步长十分敏感，但是又难以选择合适的步长，在训练过程中新旧策略的的变化差异如果过大则不利于学习。PPO算法提出了新的目标函数可以再多个训练步骤实现小批量的更新，解决了Policy Gradient算法中步长难以确定的问题。其实，TRPO也是为了解决这个思想，但是相比于TRPO算法PPO算法更容易求解。TRPO算法的优化使用的是共轭梯度法（Conjugate Gradient），在计算梯度的时候要计算KL divergence的二阶导数，而PPO算法只需要计算一阶，这样大大减小了计算量。




MineRLNavigate-v0.txt
Rainbow: best_score: 13.0 +- 33.63034344160047 ("+-" denotes standard deviation)
PPO: best_score: 8.0 +- 27.129319932501073 ("+-" denotes standard deviation)
DDDQN: best_score: 4.0 +- 19.595917942265423 ("+-" denotes standard deviation)

MineRLTreechop-v0.txt
Rainbow: best_score: 62.44 +- 2.7434285119171578 ("+-" denotes standard deviation)
PPO: best_score: 56.31 +- 8.306256677950662 ("+-" denotes standard deviation)
DDDQN: best_score: 5.28 +- 2.867333255831976 ("+-" denotes standard deviation)

MineRLNavigateDense-v0.txt
Rainbow: best_score: 66.89166902255266 +- 41.23925514895555 ("+-" denotes standard deviation)
PPO: best_score: 87.82769563049078 +- 59.455629216295144 ("+-" denotes standard deviation)
DDDQN: best_score: 59.134177452623845 +- 52.43237430511946 ("+-" denotes standard deviation)

四、参考资料

1. Joseph Modayil，Hado van Hasselt，et al，Rainbow: Combining Improvements in Deep Reinforcement Learning，2017.10，Matteo Hessel，

2. John Schulman, Filip Wolski, Prafulla Dhariwal, Alec Radford, Oleg Klimov，OpenAI，Proximal Policy Optimization Algorithms，2017.8.
