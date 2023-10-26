# AlphaTensor - Discovering faster matrix multiplication algorithms with reinforcement learning
#### <i> Alhussein Fawzi, Matej Balog, Aja Huang, Thomas Hubert, Bernardino Romera-Paredes, Mohammadamin Barekatain, Alexander Novikov, Francisco J. R. Ruiz, Julian Schrittwieser, Grzegorz Swirszcz, David Silver, Demis Hassabis & Pushmeet Kohli </i>

## Summary:

Google Deepmind’s AlphaTensor is a model which can find provably correct algorithms (matrix decompositions) to multiply arbitrary matrices within a finite factor space.

## Contributions
•	AlphaTensor was built upon AlphaZero, a 2017 RL-based model which played games such as Go, Chess and Shogi at a superhuman level. </br>
•	Matrix multiplication traditionally involves lot of multiplication operations, which is not ideal. Matrix decompositions are used to multiply matrices using more addition operations than multiplication operations. </br>
•	One example of an algorithm is strassen’s algorithm which involves only 7 multiplication operations (for 2x2 matrices), compared to 8 multiplications in the traditional matrix multiplication process. </br>
•	This model can find decomposition algorithms efficiently, tailored to specific hardware.

## Method:
•	AlphaTensor used DRL (Deep Reinforcement Learning) to find the algorithm, which is composed of the TensorGame, the results of which are fed into a NN to update the rewards. </br>
•	First, the TensorGame takes place. Three factors u, v, and w are taken at random such that they form tensor T: </br>
 <imgsrc='../images/AlphaTensor_Tensorgame.png'> </br>
•	States are updated after each round. </br>
 <imgsrc='../images/AlphaTensor_States.png'> </br>
•	This step is repeated until the zero-tensor is reached. At each step there is a reward of -1, to encourage the least number of steps taken to reach the zero tensor. </br>
•	The next step is change of basis (it increases diversity) and data augmentation. </br>
•	Then, MCTS (Monte Carlo Tree Search) plans the next step. It has two ways to guide the decision-making process: a value head, which estimates the rewards, and a policy head, which decides the step to go down the tree. </br>
•	Deep Reinforcement Learning begins, where the output and synthetic data are fed into a neural network to update the policy and value functions. </br>
•	The model is then updated with the new policy and value functions which can start a new iteration. </br>
 <imgsrc='../images/AlphaTensor_model.png'> </br>


## Results:
•	Rediscovered the algorithms of the current state-of-the-art models, with improved complexities. </br>
•	Efficient model tailored to specific hardware, without prior hardware knowledge. </br>
•	One limitation of this model is noted to be the need to predefine a potential set of factor entries F, which can cause the model to miss out on efficient algorithms. </br>
•	One of the strengths is noted to be its flexibility support complex stochastic and non-differentiable rewards. </br>
 <imgsrc='../images/AlphaTensor_results.png'> </br>

 ## Two Cents:
 The model AlphaTensor, can find algorithms which are more efficient than current computer and human-designed algorithms. AlphaTensor has direct practical applications, as matrix multiplications are significant in computational tasks. This model can also be used to finding rank of a matrix, etc. We look forward to seeing future developments.
