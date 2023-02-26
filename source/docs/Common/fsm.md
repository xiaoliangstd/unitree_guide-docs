## FSM
FSM(Finite state machines) are used to manage robot behavior and provide user services.
### Passive
In this state, all joints of the robot will go into damping mode and the robot will slowly get down if the robot is standing. This mode is also used to deal with emergency situations of the robot, such as falling down, c.f. FSM::checkSafty().
![Switch](../../images/gif/passive.gif)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">passive</div>
</center>
<br>

### FixedStand 
In this state, each joint of the robot will gradually rotate to a given angle and then lock. It is the intermediate state where the robot changes from the Passive state to the Trotting state.

![Switch](../../images/gif/fixstand.gif)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">FixedStand</div>
</center>
<br>

### FreeStand
In this state, the robot can change the orientation and height of the body according to the command of the joystick or keyboard.

![FreeStand](../../images/Practice/freeStand.gif)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">FreeStand</div>
</center>
<br>

### Trotting 
Trotting gait, when the robot will walk using a Trotting gait.
![Switch](../../images/gif/trot_new.gif)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">Trotting</div>
</center>
<br>

![Switch](../../images/gif/crawl.gif)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">crawl</div>
</center>
<br>

![Switch](../../images/gait.png)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">crawl</div>
</center>
<br>

### move_base
Navigation and obstacle avoidance mode, the robot will move according to the commands issued by ROS move_base.

### FSM Switch
![Switch](../../images/fsmSwitch.png)
<center>
<br>
<div style="color:orange; border-bottom: 0.1px solid #d9d9d9;
display: inline-block;
color: #999;
padding: 1px;">FSM state switching</div>
</center>
<br>