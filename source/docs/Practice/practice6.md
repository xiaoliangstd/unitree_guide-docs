# Practice6: posture control of robots
In FixedStand state, you only need to press **"3"** key on the keyboard
or the **"L2+X"** key combination on the handle to enter the FreeStand state.
In this state, we can use the keyboard or the joystick to control the robot to change its position and attitude in the same place. When using keyboard, we use **WASD** key to simulate the left stick of joystick, and **IJKL** key to simulate the right stick. Meanwhile, the space bar represents returning the value of the left and right joysticks to 0.
![FreeStand](../../images/Practice/freeStand.gif)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">FreeStand</div>
</center>
<br>
The specific implementation of this state is through the
the algorithm introduced in section 6.1.1 of this chapter.
to calculate the position of each foot end in the target pose of the robot.
Then, the target position of each joint is calculated and the joint position is controlled.
Although the algorithm in section 6.1.1 can control the robot in three directions of translation and three directions of rotation
and rotation in three directions, but since there are only two joysticks on the handle
so we can only control four directions, so our program chooses to control the three Euler angles of the body pose
and the height of the fuselage.
Before we introduce the control program, we first introduce the program that contains the robot
class QuadrupedRobot, which contains calculations related to the kinematics of the whole machine.

## QuadrupedRobot Class
1. `getQ(vecP, frame)`:  The inverse kinematics is calculated to obtain the angles of all 12 joints of the current robot.where each column of `vecP` represents the position coordinates of the four foot ends, respectively.
frame represents the coordinate system in which the position coordinates in `vecP` are located.frame can only be `FrameType::HIP`or `FrameType::BODY`.

2. `getQd(pos, vel, frame)`: Inverse differential kinematics is calculated to obtain the angular velocities of all 12 joints of the current robot.where **pos** represents the positions of the four foot ends, the **vel** represents the velocities of the four foot ends, the frame is the same as the function `getQ`.

3. `getTau(q, feetForce)`: The robot statics is calculated to obtain the moments of all 12 joints of the current robot. where **q** represents the angles of the current 12 joints. **feetForce** is the external force of the four foot ends.

4. `getFootPosition(state, id, frame)`: The forward kinematics is calculated to obtain the robot's **id** leg in the **frame** coordinate system.**state** is a structure of type `LowlevelState` which contains all the joint angle information of the robot. **frame** can only be `FrameType::HIP` or `FrameType::BODY`.

5. `getFootVelocity(state, id)`:  Get the position coordinates of all foot ends relative to the center of the frame.The parameter **frame** can be `FrameType::HIP` and `FrameType::BODY`. It can also be `FrameType::GLOBAL`, which represents the world coordinate system.

6. `getFeet2BPositions(state, frame)`: