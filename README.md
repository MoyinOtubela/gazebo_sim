README Document for Robbie V2.0 Simulation Scripts

**notes on inertial definition changes:
1) the params.xacro file is now no longer used - properties commented out so still useful for referencing
2) all xacro properties now in local .xacro files (i.e. arm_length is in arm.xacro)
3) the box_inertial macro was modified -> original had an error in Izz term
4) updated the robot mass/lengthscale params with help of solidworks
***

Common commands for running simulation:	

	roslaunch robbie_gazebo robbie_world.launch	# launch gazebo simulation
	roslaunch robbie_control robbie_control.launch # add controllers and rviz compatability
	rosrun rqt_gui rqt_gui	# enable slidebar joint control 
	rosrun turtlebot_teleop turtlebot_teleop_key /turtlebot_teleop/cmd_vel:=/robbie/cmd_vel # enable teleoperated control

Notes:
torso.xacro -> both visual and collision meshes need to be the same (visual mesh)
arm.xacro -> both visual and collision meshes need to be the same (visual mesh)

FILE STRUCTURE
robbie_description
	meshes							% contains sdl files for meshes used
	urdf
		macros.xacro
		params.xacro				% not used							
		robbie.gazebo	
		robbie.urdf					% not used
		robbie.xacro 				% main xacro file which calls links/joints
		shank
			shank.xacro
			shank.transmission.xacro
		stabiliser
			stabiliser.xacro
			stabiliser.transmission.xacro
		thigh
			thigh.xacro
			thigh.transmission.xacro
		torso
			torso.xacro
			torso.transmission.xacro
		arm
			arm.xacro
			arm.transmission.xacro		
		lhm
			lhm.xacro
			lhm.transmission.xacro		
		sensors
			lhm.xacro
o
		
###############################
# UPDATE April 2016:
Some issues porting Gazebo from Hydro to Gazebe. Started getting these errors:

[ERROR] [1460154930.748227861, 11.877000000]: Exception thrown while initializing controller rightWheel_effort_controller.
Could not find resource 'wheel_right_joint' in 'hardware_interface::EffortJointInterface'.
[ERROR] [1460154930.748277785, 11.877000000]: Initializing controller 'rightWheel_effort_controller' failed

[ERROR] [1460154931.752633767, 12.878000000]: Exception thrown while initializing controller leftWheel_effort_controller.
Could not find resource 'wheel_left_joint' in 'hardware_interface::EffortJointInterface'.
[ERROR] [1460154931.752682037, 12.878000000]: Initializing controller 'leftWheel_effort_controller' failed

[ERROR] [1460154932.812174201, 13.937000000]: Exception thrown while initializing controller knee_position_controller.
Could not find resource 'knee_joint' in 'hardware_interface::EffortJointInterface'.
[ERROR] [1460154932.812220972, 13.937000000]: Initializing controller 'knee_position_controller' failed

[ERROR] [1460154933.965577588, 15.089000000]: Exception thrown while initializing controller lhm_left_wheel_effort_controller.
Could not find resource 'lhm_wheel_left_joint' in 'hardware_interface::EffortJointInterface'.
[ERROR] [1460154933.965626316, 15.089000000]: Initializing controller 'lhm_left_wheel_effort_controller' failed

[ERROR] [1460154934.969630462, 16.092000000]: Exception thrown while initializing controller lhm_right_wheel_effort_controller.
Could not find resource 'lhm_wheel_right_joint' in 'hardware_interface::EffortJointInterface'.
[ERROR] [1460154934.969676382, 16.092000000]: Initializing controller 'lhm_right_wheel_effort_controller' failed

[ERROR] [1460154935.996274996, 17.117000000]: Exception thrown while initializing controller lhm_position_controller.
Could not find resource 'lhm_torso_joint' in 'hardware_interface::EffortJointInterface'.
[ERROR] [1460154935.996318720, 17.117000000]: Initializing controller 'lhm_position_controller' failed

Cause and answer given in this link: http://answers.ros.org/question/186681/no-valid-hardware-interface-element-found-in-joint/





