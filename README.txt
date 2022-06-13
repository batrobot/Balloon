This directory contains the modeling, simulation and real-time files for the UGV guided balloon project at Caltech CAST.

System model
->The underlying model derivation and referenced function for the MPC controller are found under the file "Model functions"

Control and simulation 
-> The simulation model is implemented in Simulink, the file is given in the directory "Simulink Simulation Model"
-> The closed loop simulation is configured using "CTRL_Param_def", and calls the control computation and simulink model loops
-> The controller is simulated using the Matlab MPC Toolbox. Its implementation is given in "MPC_Control_exec_fcn_scaled"
	-> This file depends on: All files under Model functions, the parameters in "Model_parameter_script_PVC_Balloon.m"
	-> This file is called by "CTRL_Param_def"

 
Real-Time Control (Directory SDRT Real-Time Control)
-> Models compatible with Simulink Desktop Real-Time are created to allow for realt-time actuation and control in directory SDRT Real-Time Control

	Open loop actuation (SDRT Open loop directory)
		-> If the ESP8266 connection details are changed, the ports must be adapted in "Connection_definitions.m"
		-> The file "UDP_test_3_rob_OT_Record.slx" allows for feedforward actuation of inertial UGV velocity commands and receives state feedback from the OptiTrack processing machine (Using UDP Send/UDP Receive blocks)
		-> Under Validation/Testing_validation_Plot.m, a script for comapring the results between simulation and testing is given

	Closed loop actuation (SDRT Closed loop directory)
		-> The current SDRT Model for closed loop control is implemented in "MPC_implementation_ML_function.slx"
		-> This model calls the extrinsic Matlab function (slow) "MPC_Real_time_control_EXTRINSIC.m" that performs the control calculation at every control step


File references may require refactoring depending on directory structure!