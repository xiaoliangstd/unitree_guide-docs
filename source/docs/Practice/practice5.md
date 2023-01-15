# Practice5: Let the legs moving
The control of a quadruped robot is a combination of many sub-control systems.
So when there is a problem with the robot algorithm, or when parameters need to be adjusted
we often have no way to do so. This is because it is difficult to determine the source of the problem.
It is also difficult to observe the performance of the robot after modifying the parameters.
Therefore, we test and adjust the parameters of each subsystem of the robot.
To do this easily, we can add states to the finite state machine for testing.
For example, to facilitate our debugging of the motion of the robot's legs
we add the state \lstinline{SwingTest}.
The reader can see the code under the **src/FSM/State_SwingTest.cpp** file.
to see the relevant code.
##