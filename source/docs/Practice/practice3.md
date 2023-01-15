# Practice3: Control real robots and configure networks
## Control program of the robot
&emsp;We take the motion mode of the A1 robot as an example to explain how the robot's control program controls the robot.
From [A1 Robot network architecture](../GettingStarted/common.md),we can see that the robot's motion mode program runs on the UP Board.
However, the UP Board is not connected to the joint motor by RS-485 communication, so it cannot send the joint commands obtained from the motion pattern calculation directly to the motor.
At this point, we need to use a switch to establish Ethernet communication between the UP Board and the main control board.
Then use the unitree_legged_sdk library to send the joint commands from the UP Board to the main control board.
The master board can then distribute the commands to each motor via RS-485.
Then the current status of each motor and the commands from the wireless remote control are returned to the UP Board.

## Join the user computer to the local area network
&emsp;Joining user computers to the LAN is a two-step process:<br>
&emsp;1.The first step is to connect our user computer to the robot's switch with a network cable.
As shown in Figure  [A1 Robot network architecture](../GettingStarted/common.md)
The robots have both Ethernet ports on their backs.
One of the A1 robots has two Ethernet ports, and both Ethernet ports are directly connected to the switch, so they are equivalent.
Connect one end of the network cable to either of the Ethernet ports on the robot's back and the other end to the computer.
If the only Ethernet port on the computer is already occupied by a wired network, then it is recommended to choose a USB Gigabit port to connect to the robot.<br>
&emsp;2.The second step is to configure the IP address of the computer network port.
The LAN on the robot belongs to the 123 network segment, and under the current network settings of the switch, the IP addresses of the devices on the LAN all need to be
192.168.123.xxx format.
When configuring the IP addresses of our own user computers, we also need to be careful not to duplicate the IP addresses of the computers on the robot.
Here we recommend that readers set their own computer IP to a fixed IP: 192.168.123.162.<br>
&emsp;First check the device name of the current computer Internet port。Open a terminal, type the `ifconfig` command and enter to execute it. You will get a result similar to the one shown in Figure \ref{fig:ifconfig view network port device name}.