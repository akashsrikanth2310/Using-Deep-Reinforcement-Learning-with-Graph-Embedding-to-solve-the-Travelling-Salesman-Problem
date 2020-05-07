# Using-Deep-Reinforcement-Learning-with-Graph-Embedding-to-solve-the-Travelling-Salesman-Problem
Using Deep Reinforcement Learning with Graph Embedding to solve the Travelling Salesman Problem

Travelling Salesman Problem with Deep Reinforcement Learning 
 
Introduction to the problem:  
 
Our problem is trying to solve the travelling salesman problem using deep reinforcement learning. We try to solve the problems where we need to visit every node in the graph with a constraint on fuel where we have a pre-set mileage on the truck that will need to refuel once the mileage distance runs out. We use the deep Q-learning approach with the struct2vec approach for graph embeddings to solve the problem

Description of the datasets : 
 
Symmetric DataSet : [ Train and Test] 
 
For training the data we use a synthetic dataset with the help of the numpy random function. Using numpy random we build a Coordinate matrix of latitude and longitude values that represent the various nodes of the graph and based on this Coordinate Matrix we build a Distance Matrix that will hold the distance values between the various nodes of the Coordinate matrix. 

 
We set the Episode values to 4000 which will train the model on 4000 different random generated graphs. 
 
Real Data Set : [Test] 
 
For testing, we have a test that can be run on a synthetic data set or a real dataset of cities. The real dataset has the following specifics: 1) 22 coordinates of Mediterranean cities 2) 52 coordinates of Berlin   3)  100 coordinates of real city(ref: http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/)


Description of the specific problem: 
 
Travelling Salesman Problem description: 
 
The problem description involves solving the Travelling Salesman Problem of visiting every node in the graph in the shortest possible distance with a constraint of fuel. When the mileage restriction occurs there will be a search for the nearest fuel filling station which will be added to the tour to complete its path. 
 
We are trying to solve the travelling salesman problem using the Deep Reinforcement learning approach that will be using the​ Q-learning algorithm​ to solve the problem. 
 We will be using the unsupervised version of learning for this approach. 
 
 
Description of the specific algorithm [Q-learning with Struct2vec] : 
 
We consider that the agent that we are building will have the full information of the environment and the states corresponding to its environment. This is achieved by having a state in the graph that will hold the values of the coordinates matrix in place, the distance matrix that will be produced out of this coordinate matrix and the set of nodes that are already been visited. This makes the environment fully observable and trivial. We will be using this state representation in the build of our Q-learning network. 
 
 
 
 Q-learning​: 
 We try to develop a function Q(s,a) that will help choose the specific action for a particular state and return the rewards that would be obtained on doing this at the end of the episode. 
 

 
Performing this for several episodes we would gather a good number of rewards and since it is a neural net we can differentiate based on the parameter of the function and use it to build a gradient of errors. 
 
Using these gradient values we can improve our parameters of the entire function. The basic approach of the function is to enable running of this function for several episodes and improve our parameters, on each run the algorithm will be able to choose its next best action using a greedy approach to help improve the functions parameters. 
 
Occasionally based on the epsilon value the greedy approach would be replaced by a exploration of the graph randomly to help get out of a situation that will lead to a local optimal solution. 
 
We also use the experience as a tuple to store values that help us in model learning. The experience will store  the current state, the next action, the observer reward, and the next state that we can reach.




