# FCND - 3D Motion Planning
![Quad Image](./misc/enroute.png)

In this project, I have implemented various parts of planning problem including a* search, modelling search space as a graph and path pruning. 

## Project Tasks 

### Step 1: Inspect the relevant files
For this project, we are provided with two scripts, `motion_planning.py` and `planning_utils.py`. Here you'll also find a file called `colliders.csv`, 
which contains the 2.5D map of the simulator environment. 

### Step 1: Explain what's going on in  `motion_planning.py` and `planning_utils.py`

`motion_planning.py` is basically a modified version of `backyard_flyer.py` that leverages some extra functions in `planning_utils.py`. I
After comparing the files, we can see that motion_planning has a slight difference in state_callback method. This method is now planning for the path at ARMED state transition 
as opposed to takeoff. 


In planning_utils, there are many utility functions, few of the important ones are:

1. create_grid : This creates an in memory grid representation of the 2D world configuration using obstacle data.  
2. valid_actions: Identifies possible actions which drone can take at any given node of a graph. 
3. a_star : Implementation of heurestics based graph search algorithm which improves performance of search as compared to simple BFS or DFS.
4. prune_path : Merges multiple collienar point so as to reduce the number of waypoints. 

### Step 2: Write your planner

I wrote a planner which 
- Loads the 2.5D map in the `colliders.csv` file describing the environment.
- Discretize the environment into a grid or graph representation.
- I took a random start and goal points. The points were selected so that they are not in a straight line and fairly far away.  
- Performs a search using A*  
- Uses a collinearity test using area under triangle method. 
- Retursn waypoints in local ECEF coordinates  

I would like to experiment further to improve the waypoints, but I have run out of time as my course is finishing in next 2 days. 
