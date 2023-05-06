Download Link: https://assignmentchef.com/product/solved-eecs391-project-2-pathfinding
<br>
These programming exercises will use SEPIA (“Strategy Engine for Programming Intelligent Agents”), a game environment written by other CWRU students tailored to writing AI players. SEPIA is a real-time strategy (RTS) game (though we will not use the real-time aspects in these exercises). RTS games generally have “economic” and “battle” components. In the economic game, the goal is to collect different types of resources in the map. Typical resources are “Gold” and “Wood.” Resources are collected using units called “Peasants.” Having resources allows the player to build other buildings (Peasants can be used to build things) and produce more units. Some of these units are battle units that can be used to fight the opponent. Games generally end when one player has no more units left; however, in SEPIA, a variety of victory conditions can be declared through XML configuration files. For example we can declare a victory condition to be when a certain amount of Gold and Wood have been collected, some number of units of a certain type built, etc.

You need Java 1.8 to run SEPIA. Note that, although the components of SEPIA you will use have been fairly well tested by now, there is still a possibility of bugs remaining. If you encounter behavior that seems strange, please let me or the TAs know.




<strong><u>Programming 2: Pathfinding </u></strong>

The data for this exercise is in the ProgrammingExercise2.zip file on Canvas.

Write an agent that can move around a given map by implement the A* search algorithm discussed in class. In the file AstarAgent.java, find the function AstarSearch.java and fill it in. This function should return a path from the starting location to the goal. The rest of the agent code has already been filled in so that once you implement the search, the agent will execute it in the game. During this step, it will output its progress with helpful messages that should let you debug your code. You can also watch VisualAgent (the GUI window showing the map) to see how your found path is being followed. The terminal output will also show the total time taken by the process. You should try to reduce this as much as possible (i.e. write efficient code!). For a proper estimate of the time taken, you can stop VisualAgent from running by deleting or commenting out the corresponding &lt;agentclass&gt; lines from the configuration file.

For A*, you will need a heuristic function. The Chebyshev distance is a good heuristic for this purpose. This is defined as follows: D((x1,y1),(x2,y2))=max( |x2−x1| , |y2−y1| ). To test your algorithm, use the maze maps provided. In each map, a Footman is trapped in a maze. Somewhere in the maze is an enemy Townhall. The provided code will use your implementation to find a path that takes the Footman to the Townhall and attack it. When the Townhall is destroyed, the game will end. If it is not possible to guide the Footman to the Townhall, print “No available path.” in the terminal and quit (call System.exit(0)).

You can use VisualAgent to check that your agent is behaving correctly. You can run the maze maps just using VisualAgent, left click on the Footman and right click on the Townhall to see the solution according to the built in pathfinding routines.

A* allows to you to do basic pathfinding, but in more complex scenarios, many units will be wandering around, and pathfinding is complicated. We will now simulate this using a simple scenario.

One of the provided maps (maze_16x16h_dynamic) is an environment with an enemy footman, controlled by the wicked EnemyBlockerAgent. This agent will try to prevent your agent from destroying the enemy Townhall by blocking their path (it won’t attack you otherwise). To get around this, use the “shouldReplanPath()” function in AstarAgent. Here, you can check to see if the current path is blocked. If so, you should return true and the agent will redo the search from that point. Try to write a nice function which is smart about when it needs to redo the search so you minimize the total time spent in searching and execution.

We may award up to 10 bonus points if (i) your code is clean, elegant and comprehensible and (ii) your total runtimes are among the top three in the class. Please do NOT use mapspecific or heuristic-specific optimizations in your A* implementation. This means your implementation should be able to handle any map and any heuristic..