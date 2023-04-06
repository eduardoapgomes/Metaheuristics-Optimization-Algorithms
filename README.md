# Metaheuristics-Optimization-Algorithms

This repository contains a collection of metaheuristic algorithms applied to optimization problems. Created for a metaheuristics class, it serves as a valuable resource for students looking to explore and implement these techniques in their own projects. Includes code, documentation, and links to relevant research papers and other resources.

8-Queens Optimization Solution using Variable Neighborhood Search (VNS)
=======================================================================

Solving the 8-Queens problem using Python’s VNS algorithm and chess package



### 8-Queens Optimization Solution using Variable Neighborhood Search (VNS)

The 8-Queens placement problem involves placing eight queens on an 8x8 chessboard so that no two queens threaten each other. This classic problem in computer science has been extensively studied in the field of optimization.

In this Jupyter notebook, we present a solution to the 8-Queens problem using the VNS algorithm. The chessboard and figures are modeled using the chess package, and the VNS algorithm is implemented using built-in functions from Python’s numpy and random packages.

[Explore my open source code on GitHub licensed under MIT](https://github.com/eduardoapgomes/Metaheuristics-Optimization-Algorithms/tree/develop)!

One notable feature of this notebook is the ability to visualize the iterative process of the VNS algorithm by displaying the chessboard at each step. This feature provides insight into the algorithm’s behavior and can help in understanding how it works.

In addition, we provide an analysis of the VNS algorithm’s performance on the 8-Queens problem. This analysis provides further insight into the algorithm’s behavior and its ability to find a solution efficiently. By demonstrating the VNS algorithm’s behavior and performance, this notebook offers a comprehensive solution to the 8-Queens problem using a widely studied optimization technique.

Our solution is organized into the following sections, implemented in the following order:

1.  N-Queens Chess Board Modeling
2.  VNS Optimization Modeling
3.  Optimization Algorithm
4.  Data Management
5.  Optimization Results and Analysis

#### N-Queens Chess Board Modeling

This section contains functions that interact with a chess board, specifically addressing the N-Queen placement problem.

Functions included:

> **set queens on board**(queens positions): returns a chess board with queens placed on the specified positions.

> **is queen**(pos, board): checks whether the position on the board contains a queen.

> **number of queens on board**(board): counts the number of queens currently on the board.

> **number of positions under attack**(board): _counts the number of board positions that are currently under attack by one or more queens._

> **number of queens under attack**(board): counts the number of queens currently under attack by one or more other queens.

> **number of queens per row**(board): counts the number of queens in each row of the board.

> **number of queens per col**(board): counts the number of queens in each column of the board.

### VNS Optimization Modeling

The VNS algorithm requires a set of functionalities to develop an optimization algorithm, including Neighborhood Automation, Objective function Automation, and Neighborhood Update modules.

#### Neighborhood Automation

The Neighborhood Automation module generates and modifies a set of binary vectors used as neighbors. It includes functions for generating random binary vectors with a specified number of ones and length, modifying neighbors by randomly changing the position of k 1’s in the vector, and converting neighbors to binary.

> **gen neighborhood**(NumberOfNeighbohrs, NuberofOnes,ProblemSize): generates a set of NumberOfNeighbohrs random binary vectors of length ProblemSize with NuberofOnes ones randomly placed within each vector. These vectors are used as the initial set of neighbors in the optimization algorithm.  
> **gen neighbor**(NuberofOnes,ProblemSize): generates a random binary vector of length ProblemSize with NuberofOnes ones randomly placed within the vector.

#### Neighborhood modifier

> **random neighborhood**(neighborhood,k): apply the random\_neighbor method in a loop for a set of neighbors. The number of bits to modify can be set with k.  
> **random neighbor**(bit,k): takes a binary vector (bit) as input and randomly changes the positions of k 1’s in the vector. For each of the k bits, it first selects a random index where a 1 currently exists in the vector, sets it to 0, and then selects another random index where a 0 currently exists and sets it to 1. The function preserves the total number of 1’s in the vector but changes the positions of k 1's.

#### Complementary Functions

> **gen neighbor int**(NuberofOnes,ProblemSize): define a random neighbor considering a list of integers that define the binary 1.  
> **neighbor to binary**(neighbor,ProblemSize): converts the integer solution to binary.

#### Objective Function Automation

The Objective function Automation module provides functions for computing the objective value for an optimization problem. It includes functions for computing the objective value for a given objective function, checking if new neighbors minimize the objective function globally or locally, and for checking if the solution has been found.


> **objective function**(bit): Compute the objective value for a given objective function to optimize the placement of N-Queens on a Chessboard.  
> neighborhood\_objective\_function(neighborhood): Compute the objective value for a VNS using a given objective function.  
> **is objective minimizing**(new\_objective,objective): Check if new neighbors minimize the objective function globally.  
> **is any local objective minimizing**(new\_objective,objective): Check if any neighbor is minimizing the objective function locally.  
> is stop criteria(objective): Check if the solution was found.

#### Neighborhood Update

The Neighborhood Update module provides a function for deciding on the updating of the neighborhood by comparing the objective function from the neighborhood with the new neighborhood. This function is used in the VNS algorithm to determine whether to accept the new neighborhood or keep the current one.

> **local neighborhood update** (new neighborhood,new objective, neighborhood, objective): this function decides on the updating of neighborhood by comparing the objective function from the neighborhood with the new neighborhood.

### Optimization Algorithm

The VNS is an optimization algorithm that can be used to solve the N-Queens placement problem. The algorithm works by iteratively searching for a better solution by exploring different neighborhoods of the current solution. The algorithm consists of the following steps:

1.  **Start**: The algorithm starts by generating an initial solution to the problem. In the case of the 8-Queens placement problem, this involves placing eight queens on the chessboard such that no two queens threaten each other. Additionally, the algorithm initiates optimization parameters, such as the maximum number of iterations, the number of neighbors, and the diversification parameter, _k\_máx_.
2.  **Shaking**: In this step, the algorithm generates a new solution by modifying the current solution. Specifically, each queen is moved to a new randomly chosen position within its own column. The number of queens that are moved is controlled by the diversification parameter, _k_. The shaking step is important because it allows the algorithm to escape local optima and explore different regions of the solution space.
3.  **Change Neighborhood Strategy**: The number of queens that are allowed to move is controlled by the diversification parameter, _k_. If the optimization criteria do not improve after a certain number of iterations, the algorithm modifies _k_ by setting _k ← k+1_. This strategy helps to balance exploration and exploitation of the solution space.
4.  **Local Search**: The algorithm updates the solution by modifying all neighbors that minimize the objective function locally. In the case of the N-Queens placement problem, the objective function is to minimize the number of pairs of queens that threaten each other. The local search step is important because it allows the algorithm to exploit promising regions of the solution space.
5.  **Optimal Solution**: The neighbor that minimizes the objective function returns as the algorithm’s solution. In the case of the 8-Queens placement problem, the optimal solution is a placement of eight queens on the chessboard such that no two queens threaten each other.
6.  **Stop Criteria**: The iterative optimization process stops if the minimization condition is achieved. In the case of the 8-Queens placement problem, this means that no two queens threaten each other in the final solution.

By following these steps, the VNS algorithm can efficiently optimize the objective function of the 8-Queens placement problem and find a placement of eight queens on the chessboard that satisfies the problem constraints.

### Data Management

In the Data Management section, we focus on the organization and integration of data obtained from the optimization procedures. Specifically, we convert the raw data generated by the VNS algorithm into a structured format that can be easily analyzed and visualized.

To achieve this, we use a dataframe, a widely used data structure in data science that allows for efficient manipulation and analysis of data. By integrating the optimization results into a dataframe, we can easily visualize the results in a variety of ways, including plots, tables, and statistical summaries.

Overall, the data management step is critical in ensuring that the results obtained from the optimization process can be properly analyzed and communicated, leading to better understanding of the problem and more informed decision making.

### Optimization Results and Analysis

This section presents a comprehensive analysis of the optimization outcomes, covering key aspects such as the iterative process visualization, an interactive N-Queens board, the objective function analysis, and neighborhood optimization. Through these analyses, we aim to gain a deeper understanding of the behavior of the algorithm and the factors that influence its performance.

#### Visualization of the Iterative Process

To illustrate the iterative process of the VNS algorithm for solving the 8-Queen problem, a series of five plots are presented. These plots show the board configuration at different stages of the algorithm, from the initial random placement of queens to the final optimal configuration. The plots use a simple and elegant representation of the board, with black and white squares arranged in an 8x8 grid, and each queen represented by a unique symbol.

By presenting the iterative process in a visual format, these plots offer a comprehensive and intuitive way to understand how the VNS algorithm arrives at the final solution. The gradual progression from an initial, suboptimal configuration to the final optimal placement of queens can be easily observed and analyzed. Additionally, the use of symbols to represent each queen adds a level of clarity and precision to the visualization.

Overall, these plots provide a valuable visual aid for understanding and communicating the results of the VNS algorithm in solving the 8-Queen problem.

![](https://cdn-images-1.medium.com/max/800/1*s5lHG2V5G3PhJL2LLGuMxA.png)

Figure 1. Iterative Process of the VNS in 8-Queen placement.

#### Interactive N-Queens Board

To enhance the visualization of the optimization process, an interactive 8-Queens board is provided. This feature allows users to dynamically observe the gradual optimization progress by exploring different iterations of the algorithm’s search process.

The interactive board includes a slider that enables the user to move through the iterations and visualize the progress of the algorithm. As the user moves the slider, the board configuration changes, highlighting the position of the queens at each iteration. This interactive feature offers a more comprehensive understanding of the optimization process and the steps taken to reach the optimal solution.

Overall, the interactive 8-Queens board adds an additional layer of analysis to the study, providing an innovative approach to visualizing the optimization process and improving the interpretation of the results.

![](https://cdn-images-1.medium.com/max/800/1*NbI-_49qEOfu754ZJdWMVA.png)

Figure 2. Slider Example

### Objective Function Analysis

In this section, we examine the behavior of the objective function _f\_obj_ during the optimization process. We focus on two key aspects:

1.  Comparing the performance of global optimum and optimum neighbor approaches in the optimization process using the VNS method.
2.  Analyzing the impact of the diversification parameter _k_ on the objective function for the neighborhood generated by the VNS algorithm.

These findings provide valuable insights for the development of optimization algorithms for similar problems.

#### Global Optimum vs. Optimum Neighbor

In this study, we investigated the performance of the global optimum and optimum neighbor approaches in the optimization process of the N-Queen problem using the VNS method. Our aim was to assess the impact of local optimization nesting and control its effects by setting a maximum diversification of _k\_max= 2_ queens and generating 10 neighbors to create the VNS neighborhood.

The results indicate that the global optimum curve does not follow the optimum neighbor curve initially, which is a direct result of the local optimization trapping effect. Figure 3 illustrates this effect by displaying the comparison between the global optimum and optimum neighbor curves over the number of iterations. However, after 300 iterations, the optimum neighbor curve converges to the global optimum curve, suggesting that the VNS method can effectively overcome local optimization trapping and achieve the global optimum solution with a sufficient number of iterations.

These findings suggest that a balance between global and local search strategies is necessary for achieving optimal solutions in the 8-Queen problem. Moreover, the VNS method is a promising approach for handling local optimization nesting and obtaining the global optimum solution. Our study provides useful insights for the development of optimization algorithms for similar problems.

![png](https://cdn-images-1.medium.com/max/800/1*lNWAv-M1eTro6D4p8vktIQ.png)

Figure 3. Global Optimum vs. Optimum Neighbor

#### Neighborhood Optimization

In this section, we analyze the behavior of the objective function for the neighborhood generated by the VNS algorithm, focusing on the impact of the diversification parameter _k_. To this end, we plot the changes in the objective function for different values of _k_ in Figure 4.

One interesting observation is that the VNS algorithm frequently changes the diversification parameter _k_ in an attempt to escape from local optima traps and accelerate the minimization process. Figure 4 illustrates this behavior by showing the transitions in the objective function for all neighborhoods.

The fact that _k_ diversification parameter varies significantly across the iterative process is indicative of the existence of several local minima in the problem. These local minima can be challenging for optimization algorithms as they can lead to the algorithm converging to a suboptimal solution.

Overall, this analysis highlights the importance of exploring different diversification parameters in the neighborhood optimization process and the challenges posed by local optima traps. The findings can inform the development of more effective optimization algorithms for similar problems.

![png](https://cdn-images-1.medium.com/max/800/1*aBmVe4Gbjk4LvLPHrQVnTg.png)

### Conclusions

Overall, this report provides a detailed analysis of the results obtained from applying VNS to the 8-Queen placement problem. The interactive visualization of the solution, the plot of the final board configuration, and the analysis of the objective function behavior offer valuable insights into the performance of the algorithm.

By [Eng Eduardoapg](https://medium.com/@eng.eduardoapg) on [April 6, 2023](https://medium.com/p/4b9bf60c4958).

[Canonical link](https://medium.com/@eng.eduardoapg/8-queens-optimization-solution-using-variable-neighborhood-search-vns-4b9bf60c4958)

Exported from [Medium](https://medium.com) on April 6, 2023.
