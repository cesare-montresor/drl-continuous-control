[//]: # (Image References)

[scores]: img/score.png "Scores"


## Learning Algorithm

The algorithm chosen is DDPG, it an actor-critic method.  
The actor network is responsible for chosing actions based on the state and the critic network try to estimate the reward for the given state-action pair.  
DDPG in continuous control is particularly useful as, unlike discrete actions, all the actions are "choose" at every timestep with a continuous value making non-trivial to build a loss function based on these values.  
Instead, the actor network is indirectly trained using gradient ascent on the critic network, reducing the problem of building a loss function to a more classic RL problem of maximize the expected reward.  
The algorithm also leverages the fixed-Q target, double network, soft-updates and experience replay.   

## Plot of Rewards

The currently trained agent passed the goal in about 106 episodes, however, in the many attempts I must say that this number may vary sensibly.
While the code is provided with a fixed random seed for result replicability, the unity environment is not.
From my observation sometimes happen that the agent has some difficulties in the early training, filling up the replay buffer with poor training examples, which ultimately delay up to 20-30 episodes the solution of the environment.

![Scores][scores]

In the last section can be found a detailed log for each episode. 

## Ideas for Future Work  
  

Other attempts I would have liked to try to improve the learning but I didn't had the time to try them out.

- Prioritized experience replay: for previous experiences showed that can be very useful to speedup the early training of the algorithm.  
- Layer noise instead of action noise
- Several of the improvements coming from PPO: Gradient clipping, credit assignment and reward normalization.
  

## Other considerations

Variations I've tried which didn't result in a success:  

- Cosines learning rate annealing
- SGD with warm restart
- Action noise annealing 
- 20 separate local networks (actor+critic) and 1 global network (actor+critic)

Other variations which didn't improve the results significantly:

- batch normalization 
- dropout
- deeper networks
- wider networks


## Training history


```
Episode 1	 Score: 0.67 	Average Score: 0.67
Episode 2	 Score: 0.67 	Average Score: 0.67
Episode 3	 Score: 0.79 	Average Score: 0.71
Episode 4	 Score: 0.82 	Average Score: 0.74
Episode 5	 Score: 0.64 	Average Score: 0.72
Episode 6	 Score: 0.97 	Average Score: 0.76
Episode 7	 Score: 1.11 	Average Score: 0.81
Episode 8	 Score: 1.21 	Average Score: 0.86
Episode 9	 Score: 1.34 	Average Score: 0.91
Episode 10	 Score: 1.67 	Average Score: 0.99
Episode 11	 Score: 1.59 	Average Score: 1.04
Episode 12	 Score: 1.55 	Average Score: 1.09
Episode 13	 Score: 2.03 	Average Score: 1.16
Episode 14	 Score: 2.41 	Average Score: 1.25
Episode 15	 Score: 3.68 	Average Score: 1.41
Episode 16	 Score: 3.15 	Average Score: 1.52
Episode 17	 Score: 3.65 	Average Score: 1.64
Episode 18	 Score: 5.00 	Average Score: 1.83
Episode 19	 Score: 8.51 	Average Score: 2.18
Episode 20	 Score: 8.37 	Average Score: 2.49
Episode 21	 Score: 13.34 	Average Score: 3.01
Episode 22	 Score: 13.80 	Average Score: 3.50
Episode 23	 Score: 16.79 	Average Score: 4.08
Episode 24	 Score: 18.81 	Average Score: 4.69
Episode 25	 Score: 20.06 	Average Score: 5.31
Episode 26	 Score: 21.12 	Average Score: 5.91
Episode 27	 Score: 23.51 	Average Score: 6.57
Episode 28	 Score: 24.35 	Average Score: 7.20
Episode 29	 Score: 27.39 	Average Score: 7.90
Episode 30	 Score: 26.57 	Average Score: 8.52
Episode 31	 Score: 31.31 	Average Score: 9.25
Episode 32	 Score: 32.92 	Average Score: 9.99
Episode 33	 Score: 35.12 	Average Score: 10.76
Episode 34	 Score: 36.01 	Average Score: 11.50
Episode 35	 Score: 36.80 	Average Score: 12.22
Episode 36	 Score: 36.74 	Average Score: 12.90
Episode 37	 Score: 37.23 	Average Score: 13.56
Episode 38	 Score: 36.62 	Average Score: 14.17
Episode 39	 Score: 36.79 	Average Score: 14.75
Episode 40	 Score: 36.47 	Average Score: 15.29
Episode 41	 Score: 37.69 	Average Score: 15.84
Episode 42	 Score: 37.11 	Average Score: 16.34
Episode 43	 Score: 37.77 	Average Score: 16.84
Episode 44	 Score: 36.91 	Average Score: 17.30
Episode 45	 Score: 37.39 	Average Score: 17.74
Episode 46	 Score: 37.47 	Average Score: 18.17
Episode 47	 Score: 37.02 	Average Score: 18.57
Episode 48	 Score: 36.39 	Average Score: 18.94
Episode 49	 Score: 36.88 	Average Score: 19.31
Episode 50	 Score: 37.01 	Average Score: 19.66
Episode 51	 Score: 37.36 	Average Score: 20.01
Episode 52	 Score: 37.32 	Average Score: 20.34
Episode 53	 Score: 37.48 	Average Score: 20.67
Episode 54	 Score: 37.24 	Average Score: 20.97
Episode 55	 Score: 37.25 	Average Score: 21.27
Episode 56	 Score: 37.65 	Average Score: 21.56
Episode 57	 Score: 37.35 	Average Score: 21.84
Episode 58	 Score: 36.31 	Average Score: 22.09
Episode 59	 Score: 36.65 	Average Score: 22.34
Episode 60	 Score: 36.49 	Average Score: 22.57
Episode 61	 Score: 35.57 	Average Score: 22.79
Episode 62	 Score: 35.99 	Average Score: 23.00
Episode 63	 Score: 35.94 	Average Score: 23.20
Episode 64	 Score: 35.33 	Average Score: 23.39
Episode 65	 Score: 36.32 	Average Score: 23.59
Episode 66	 Score: 36.60 	Average Score: 23.79
Episode 67	 Score: 34.65 	Average Score: 23.95
Episode 68	 Score: 33.27 	Average Score: 24.09
Episode 69	 Score: 35.14 	Average Score: 24.25
Episode 70	 Score: 34.92 	Average Score: 24.40
Episode 71	 Score: 35.65 	Average Score: 24.56
Episode 72	 Score: 35.69 	Average Score: 24.71
Episode 73	 Score: 35.19 	Average Score: 24.86
Episode 74	 Score: 36.42 	Average Score: 25.01
Episode 75	 Score: 35.06 	Average Score: 25.15
Episode 76	 Score: 34.98 	Average Score: 25.28
Episode 77	 Score: 35.68 	Average Score: 25.41
Episode 78	 Score: 35.68 	Average Score: 25.54
Episode 79	 Score: 34.66 	Average Score: 25.66
Episode 80	 Score: 35.86 	Average Score: 25.79
Episode 81	 Score: 36.58 	Average Score: 25.92
Episode 82	 Score: 36.91 	Average Score: 26.05
Episode 83	 Score: 36.11 	Average Score: 26.18
Episode 84	 Score: 36.97 	Average Score: 26.30
Episode 85	 Score: 36.59 	Average Score: 26.42
Episode 86	 Score: 37.54 	Average Score: 26.55
Episode 87	 Score: 37.47 	Average Score: 26.68
Episode 88	 Score: 37.45 	Average Score: 26.80
Episode 89	 Score: 37.02 	Average Score: 26.92
Episode 90	 Score: 35.17 	Average Score: 27.01
Episode 91	 Score: 36.88 	Average Score: 27.12
Episode 92	 Score: 36.14 	Average Score: 27.21
Episode 93	 Score: 35.75 	Average Score: 27.31
Episode 94	 Score: 36.19 	Average Score: 27.40
Episode 95	 Score: 36.46 	Average Score: 27.50
Episode 96	 Score: 36.21 	Average Score: 27.59
Episode 97	 Score: 37.30 	Average Score: 27.69
Episode 98	 Score: 35.52 	Average Score: 27.77
Episode 99	 Score: 37.41 	Average Score: 27.86
Episode 100	 Score: 35.14 	Average Score: 27.94
Episode 101	 Score: 36.36 	Average Score: 28.29
Episode 102	 Score: 35.37 	Average Score: 28.64
Episode 103	 Score: 35.77 	Average Score: 28.99
Episode 104	 Score: 35.26 	Average Score: 29.34
Episode 105	 Score: 36.46 	Average Score: 29.69
Episode 106	 Score: 37.23 	Average Score: 30.06

Environment solved in 106 episodes!	Average Score: 30.056
Episode 107	 Score: 37.93 	Average Score: 30.42

Environment solved in 107 episodes!	Average Score: 30.424
Episode 108	 Score: 37.05 	Average Score: 30.78

Environment solved in 108 episodes!	Average Score: 30.783
Episode 109	 Score: 35.40 	Average Score: 31.12

Environment solved in 109 episodes!	Average Score: 31.123
Episode 110	 Score: 34.30 	Average Score: 31.45

Environment solved in 110 episodes!	Average Score: 31.450
Episode 111	 Score: 34.90 	Average Score: 31.78

Environment solved in 111 episodes!	Average Score: 31.783
Episode 112	 Score: 35.42 	Average Score: 32.12

Environment solved in 112 episodes!	Average Score: 32.122
Episode 113	 Score: 37.04 	Average Score: 32.47

Environment solved in 113 episodes!	Average Score: 32.472
Episode 114	 Score: 36.52 	Average Score: 32.81

Environment solved in 114 episodes!	Average Score: 32.813
Episode 115	 Score: 35.46 	Average Score: 33.13

Environment solved in 115 episodes!	Average Score: 33.131
Episode 116	 Score: 35.14 	Average Score: 33.45

Environment solved in 116 episodes!	Average Score: 33.451
Episode 117	 Score: 34.44 	Average Score: 33.76

Environment solved in 117 episodes!	Average Score: 33.758
Episode 118	 Score: 36.06 	Average Score: 34.07

Environment solved in 118 episodes!	Average Score: 34.069
Episode 119	 Score: 35.99 	Average Score: 34.34

Environment solved in 119 episodes!	Average Score: 34.344
Episode 120	 Score: 36.12 	Average Score: 34.62

Environment solved in 120 episodes!	Average Score: 34.621
Episode 121	 Score: 36.00 	Average Score: 34.85

Environment solved in 121 episodes!	Average Score: 34.848
Episode 122	 Score: 36.33 	Average Score: 35.07

Environment solved in 122 episodes!	Average Score: 35.073
Episode 123	 Score: 35.88 	Average Score: 35.26

Environment solved in 123 episodes!	Average Score: 35.264
Episode 124	 Score: 36.50 	Average Score: 35.44

Environment solved in 124 episodes!	Average Score: 35.441
Episode 125	 Score: 37.17 	Average Score: 35.61

Environment solved in 125 episodes!	Average Score: 35.612
Episode 126	 Score: 36.18 	Average Score: 35.76

Environment solved in 126 episodes!	Average Score: 35.763
Episode 127	 Score: 35.39 	Average Score: 35.88

Environment solved in 127 episodes!	Average Score: 35.882
Episode 128	 Score: 36.11 	Average Score: 36.00

Environment solved in 128 episodes!	Average Score: 35.999
Episode 129	 Score: 36.05 	Average Score: 36.09

Environment solved in 129 episodes!	Average Score: 36.086
Episode 130	 Score: 36.69 	Average Score: 36.19

Environment solved in 130 episodes!	Average Score: 36.187
Episode 131	 Score: 35.86 	Average Score: 36.23

Environment solved in 131 episodes!	Average Score: 36.232
Episode 132	 Score: 37.11 	Average Score: 36.27

Environment solved in 132 episodes!	Average Score: 36.274
Episode 133	 Score: 35.81 	Average Score: 36.28

Environment solved in 133 episodes!	Average Score: 36.281
Episode 134	 Score: 35.81 	Average Score: 36.28

Environment solved in 134 episodes!	Average Score: 36.279
Episode 135	 Score: 37.91 	Average Score: 36.29

Environment solved in 135 episodes!	Average Score: 36.290
Episode 136	 Score: 37.12 	Average Score: 36.29

Environment solved in 136 episodes!	Average Score: 36.294

Episode 137	 Score: 37.49 	Average Score: 36.30

Environment solved in 137 episodes!	Average Score: 36.297
Episode 138	 Score: 36.90 	Average Score: 36.30

Environment solved in 138 episodes!	Average Score: 36.299
Episode 139	 Score: 36.37 	Average Score: 36.30

Environment solved in 139 episodes!	Average Score: 36.295
Episode 140	 Score: 37.17 	Average Score: 36.30

Environment solved in 140 episodes!	Average Score: 36.302
Episode 141	 Score: 36.29 	Average Score: 36.29

Environment solved in 141 episodes!	Average Score: 36.288
Episode 142	 Score: 37.04 	Average Score: 36.29

Environment solved in 142 episodes!	Average Score: 36.288
Episode 143	 Score: 37.30 	Average Score: 36.28

Environment solved in 143 episodes!	Average Score: 36.283
Episode 144	 Score: 36.64 	Average Score: 36.28

Environment solved in 144 episodes!	Average Score: 36.280
Episode 145	 Score: 36.31 	Average Score: 36.27

Environment solved in 145 episodes!	Average Score: 36.269
Episode 146	 Score: 36.55 	Average Score: 36.26

Environment solved in 146 episodes!	Average Score: 36.260
Episode 147	 Score: 36.40 	Average Score: 36.25

Environment solved in 147 episodes!	Average Score: 36.254
Episode 148	 Score: 35.83 	Average Score: 36.25

Environment solved in 148 episodes!	Average Score: 36.248
Episode 149	 Score: 34.28 	Average Score: 36.22

Environment solved in 149 episodes!	Average Score: 36.222
Episode 150	 Score: 35.73 	Average Score: 36.21

Environment solved in 150 episodes!	Average Score: 36.210
Episode 151	 Score: 35.29 	Average Score: 36.19

Environment solved in 151 episodes!	Average Score: 36.189
Episode 152	 Score: 35.30 	Average Score: 36.17

Environment solved in 152 episodes!	Average Score: 36.169
Episode 153	 Score: 34.30 	Average Score: 36.14

Environment solved in 153 episodes!	Average Score: 36.137
Episode 154	 Score: 34.97 	Average Score: 36.11

Environment solved in 154 episodes!	Average Score: 36.114
Episode 155	 Score: 36.53 	Average Score: 36.11

Environment solved in 155 episodes!	Average Score: 36.107
Episode 156	 Score: 37.39 	Average Score: 36.10

Environment solved in 156 episodes!	Average Score: 36.104
Episode 157	 Score: 37.61 	Average Score: 36.11

Environment solved in 157 episodes!	Average Score: 36.107
Episode 158	 Score: 37.85 	Average Score: 36.12

Environment solved in 158 episodes!	Average Score: 36.122
Episode 159	 Score: 36.73 	Average Score: 36.12

Environment solved in 159 episodes!	Average Score: 36.123
Episode 160	 Score: 36.92 	Average Score: 36.13

Environment solved in 160 episodes!	Average Score: 36.128
Episode 161	 Score: 37.84 	Average Score: 36.15

Environment solved in 161 episodes!	Average Score: 36.150
Episode 162	 Score: 36.66 	Average Score: 36.16

Environment solved in 162 episodes!	Average Score: 36.157
Episode 163	 Score: 36.89 	Average Score: 36.17

Environment solved in 163 episodes!	Average Score: 36.167
Episode 164	 Score: 35.88 	Average Score: 36.17

Environment solved in 164 episodes!	Average Score: 36.172
Episode 165	 Score: 36.30 	Average Score: 36.17

Environment solved in 165 episodes!	Average Score: 36.172
Episode 166	 Score: 37.26 	Average Score: 36.18

Environment solved in 166 episodes!	Average Score: 36.178
Episode 167	 Score: 36.36 	Average Score: 36.20

Environment solved in 167 episodes!	Average Score: 36.196
Episode 168	 Score: 37.41 	Average Score: 36.24

Environment solved in 168 episodes!	Average Score: 36.237
Episode 169	 Score: 36.85 	Average Score: 36.25

Environment solved in 169 episodes!	Average Score: 36.254
Episode 170	 Score: 36.67 	Average Score: 36.27

Environment solved in 170 episodes!	Average Score: 36.272
Episode 171	 Score: 36.35 	Average Score: 36.28

Environment solved in 171 episodes!	Average Score: 36.279
Episode 172	 Score: 37.49 	Average Score: 36.30

Environment solved in 172 episodes!	Average Score: 36.297
Episode 173	 Score: 37.11 	Average Score: 36.32

Environment solved in 173 episodes!	Average Score: 36.316
Episode 174	 Score: 36.45 	Average Score: 36.32

Environment solved in 174 episodes!	Average Score: 36.316
Episode 175	 Score: 37.48 	Average Score: 36.34

Environment solved in 175 episodes!	Average Score: 36.340
Episode 176	 Score: 37.26 	Average Score: 36.36

Environment solved in 176 episodes!	Average Score: 36.363
Episode 177	 Score: 36.45 	Average Score: 36.37

Environment solved in 177 episodes!	Average Score: 36.371
Episode 178	 Score: 37.55 	Average Score: 36.39

Environment solved in 178 episodes!	Average Score: 36.389
Episode 179	 Score: 36.33 	Average Score: 36.41

Environment solved in 179 episodes!	Average Score: 36.406
Episode 180	 Score: 36.89 	Average Score: 36.42

Environment solved in 180 episodes!	Average Score: 36.416
Episode 181	 Score: 36.87 	Average Score: 36.42

Environment solved in 181 episodes!	Average Score: 36.419
Episode 182	 Score: 37.22 	Average Score: 36.42

Environment solved in 182 episodes!	Average Score: 36.422
Episode 183	 Score: 36.61 	Average Score: 36.43

Environment solved in 183 episodes!	Average Score: 36.427
Episode 184	 Score: 35.49 	Average Score: 36.41

Environment solved in 184 episodes!	Average Score: 36.413
Episode 185	 Score: 33.00 	Average Score: 36.38

Environment solved in 185 episodes!	Average Score: 36.377
Episode 186	 Score: 36.02 	Average Score: 36.36

Environment solved in 186 episodes!	Average Score: 36.361
Episode 187	 Score: 35.37 	Average Score: 36.34

Environment solved in 187 episodes!	Average Score: 36.340
Episode 188	 Score: 36.69 	Average Score: 36.33

Environment solved in 188 episodes!	Average Score: 36.333
Episode 189	 Score: 37.15 	Average Score: 36.33

Environment solved in 189 episodes!	Average Score: 36.334
Episode 190	 Score: 36.65 	Average Score: 36.35

Environment solved in 190 episodes!	Average Score: 36.349
Episode 191	 Score: 37.75 	Average Score: 36.36

Environment solved in 191 episodes!	Average Score: 36.358
Episode 192	 Score: 37.03 	Average Score: 36.37

Environment solved in 192 episodes!	Average Score: 36.367
Episode 193	 Score: 37.47 	Average Score: 36.38

Environment solved in 193 episodes!	Average Score: 36.384
Episode 194	 Score: 37.04 	Average Score: 36.39

Environment solved in 194 episodes!	Average Score: 36.392
Episode 195	 Score: 36.25 	Average Score: 36.39

Environment solved in 195 episodes!	Average Score: 36.390
Episode 196	 Score: 36.22 	Average Score: 36.39

Environment solved in 196 episodes!	Average Score: 36.390
Episode 197	 Score: 36.48 	Average Score: 36.38

Environment solved in 197 episodes!	Average Score: 36.382
Episode 198	 Score: 34.15 	Average Score: 36.37

Environment solved in 198 episodes!	Average Score: 36.369
Episode 199	 Score: 36.15 	Average Score: 36.36

Environment solved in 199 episodes!	Average Score: 36.356
Episode 200	 Score: 37.06 	Average Score: 36.38

Environment solved in 200 episodes!	Average Score: 36.375
```