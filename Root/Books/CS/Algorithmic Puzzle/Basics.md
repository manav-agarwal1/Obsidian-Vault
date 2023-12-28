- Input defines *instance* of the puzzle: **Specific** or **General**.
- **Exhaustive Search** - Try all possible candidates.
	- Number of solutions grow **exponentially** with problem size.
	- **Difficulties**:
		- Generating all possible solutions. Sometimes we have a well structured set (*Say, for magic square case ie; **Permutation***), and sometimes we don't.
		- Number of possible solutions blows up in our faces.
- **Backtracking** - It is extension to *exhaustive search*.
	- You start with generating all possible solutions then along the road you strike off some unnecessary candidates which you haven't generated yet.
	- **Idea**: You partially construct a solution to the problem, then check problem constraints on that.
		- **Evaluation**: If we can develop further without constraint violation then we take first remaining legitimate candidate for next component. If there is none, then we stop constructing that candidate further. Then we **Backtrack**, ie; you go back in time to the point when previous component was added and check for any other legitimate options there.
		- So, in **Backtrack** we undo wrong choices, and smaller the number of those choices, faster we reach goal.
		- For **Backtrack**, we call the tree *state-space tree*.
			- *Non-promising leaves*: Wrong choices we look for options for parent of leave and undo parent.
			- *Dead End*: The ones where we get the possible solution candidate. You test them for solution criteria, if good enough then stop algorithm.
	- [[N-Queens]]
- **Decrease-and-Conquer** - Construct solution of current instance in term of smaller instance, which turn into a recursive relation, which reduces until instance becomes so small, that you can solve directly.
	- Sometime we may need solve smaller instance first, to ease things up, this is called *incremental approach*.
	- [[Celebrity Problem]], [[Ferrying Soldier]], [[Number Guessing]], [[Fake Among Eight Coins]], [[Rectangle Dissection Puzzle]]
- **Divide-and-Conquer** - Partition problem into several smaller subproblems, solve each of them and then combine the solution. Many efficient algorithms are out there due to this, but not many puzzles.
	- In **decrease-and-conquer** on each step you only solve only one subproblem but here it can be multiple.
	- [[Tromino Puzzle Cover]], [2n-Counters Problem], [[Straight Tromino Tiling]].
- **Transform-and-Conquer** - 2 Stage process:
	- *1st stage* - Transformation
	- *2nd stage* - Conquering
	- 3 Flavors-
		- *Instance Simplification* - Transform an instance to another instance.
		- *Representation Change* - Transform instance to different representation. Eg: **Sorting** string, **binary** or **ternary** number system, etc.
		- *Problem Reduction* - Transform instance into instance of a different problem altogether. Eg: Question about **graphs** (*state-space graph)*, **Mathematical equations**, etc.
			- Sometimes one representation can be bit complicated and when we arrive at other then it seems like *graph unfolding* or **buttons and strings method**.
	- [[Anagram Detection]], [[Number Placement Puzzle]], [[Cash Envelopes]], [[Bachet's Weights]], [[Two Jealous Husbands]], [[Missionaries and Cannibals Puzzle]], [[Guarini's Puzzle]], [[Coins on a Star Puzzle]], [[Optimal Pie Cutting]].
- **Greedy** - Solves an optimization problem by sequence of steps, each expanding a partially completed solution until complete solution is reached. At each step we achiever *largest **immediate** gain* without harming problem constraints.
	- **Hope** - Set of **local optima** leads to a **global optima**.
	- Simple strategy.
	- [[Non-Attacking Kings]], [[Bridge Crossing at Night]]. [[Coins on a Star Puzzle]].
- **Iterative Improvement** - Starts with some easy approximations to solution and improves by changing the approximation at each step.
	- Need to make sure, algo stops after **finite** steps, and final approximation indeed solves the problem.
	- *monovariant*: Quantity with following properties:
		- It could change its value only in a desired direction.
		- It could attain only a finite number of values, which guaranteed a stop after a finite number of steps.
		- When it reached its final value, the problem was solved.
		- Tough to find a *monovariant*.
		- Important algorithms like *Simplex Methods* are based on this.
	- [[Lemonade Stand Placement]], [[Site Selection Puzzle]], [[Positive Changes]].
- **Dynamic Programming** - Technique to handle overlapping subproblems.
	- [[Shortest Path Counting]], [[Blocked Paths Puzzle]], [[Maximum Sum Descent]], [[Picking Up Coins]].