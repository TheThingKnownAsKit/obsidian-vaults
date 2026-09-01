---

kanban-plugin: board

---

## Lunabotics



## QAC

- [ ] > [!example] Constitution First Draft
	- [x] Draft Article 1: Name & Purpose
	- [ ] Draft Article 2: Membership
	- [ ] Draft Article 3: Leadership Team/Officer Elections
	- [ ] Draft Article 4: Advisors
	- [ ] Draft Article 5: Committees & Officer Creations
	- [ ] Draft Article 6: Meetings & Signature Events
	- [ ] Draft Article 7: Finances
	- [ ] Draft Article 8: RSO Procedures
	- [ ] Draft Article 9: Amendments
	- [ ] Draft Article 10: Dissolution
- [ ] > [!example] New RSO Steps
	- [x] Need 5 official members and advisor
	- [ ] Submit draft of constitution to SLICE
	- [ ] Submit New RSO Registration form on NvolveU
- [ ] > [!example] Funding
	- [ ] Email OutNebraska, Pride Alumni Network, Kenji/TJ about funding
	- [ ] Email Mike Jackson about nonprofit status process


## oSTEM

- [ ] > [!todo] Summer List
	- [ ] Buy exec plane tickets
	- [ ] Buy early bird conference tickets
	- [ ] Chapter awards?


## Homework



## Personal

- [ ] > [!abstract] Learn Languages
	- [ ] Finish reading the RUST bible
	- [x] Read learncpp.com
- [ ] > [!abstract] Self Hosting
	- [ ] Watch budget home server video
	- [ ] Look at awesome self hosted
	- [ ] Install Ubuntu Server on laptop
- [ ] > [!abstract] Financial
	- [ ] Add money to ROTH
	- [x] File FAFSA for non income based loan
- [ ] > [!abstract] Modeling
	- [ ] Learn onshape
	- [ ] Finish the 3d printing modules for design hub


***

## Archive

- [ ] > [!example] Admin Tasks
	- [x] Set up google drive folder structure
	- [x] Move lav guide into there
	- [x] Move planning doc into there
	- [x] Import constitution template into there
	- [x] Full next steps and timeline in there
- [ ] > [!error] Wireless
	- [x] Get router working
	- [x] Configure router to NASA specifications
	- [x] Set up camera view through launch files
- [ ] > [!error] Autonomy
	- [x] Receive and fix updated URDF
- [ ] > [!Todo] Boom or Doom
	- [x] Business Strategy
	- [x] Boom
	
	@{2026-04-26}
- [ ] > [!error] Quality of Life
	- [x] Set up a script that runs CONSTANTLY on mini pc that sets wifi to team_## if available
	- [x] Set default wifi to team_##
	- [x] Set up script that goes through the shell setup process (doesn't ros2 launch)
	- [x] Enable permanent SSH platformio uploads
- [ ] > [!todo] ML2
	- [x] Business Model and Financial Projections
- [ ] > [!error] Autonomy
	- [x] Implement twist_mux
	- [x] Setup robot_localization in the EKF node
	- [ ] Set up MOLA SLAM to ingest the 2D RPLidar scans and broadcast map -> odom
	- [x] Nav2 launch files
	- [ ] Edit nav2_params.yaml to include the VoxelLayer
	- [ ] Add apriltag_ros into launch
	- [ ] Boot node?
	- [ ] Define dynamic mission coordinates for AprilTag
	- [ ] Build the nav2 behavior tree
- [ ] > [!error] Test List
	- [x] Test the service refactor branch before pull request
	- [x] Test wireless again with docker container
	- [ ] Teleop + MOLA SLAM to check for no jumps and correct map
	- [ ] RealSense + Costmap test
	- [ ] Nav2 with 2D Goal Pose (no bt or apriltag)
	- [ ] Full autonomy
- [ ] > [!error] Teleop
	- [x] Robot stores previous commands on teleop launch. It should not fix it
	- [x] Increase dead zone for drivetrain
	- [x] Change LA controls to start/stop not incr/decr velocity
	- [x] Adapt new URDF for ros2 control
	- [x] Wireless teleop does not work with docker groundstation. nodes not discoverable
	- [x] Refactor state machine to use a custom ROS2 service
	- [x] Verify that the robot publishes odom when running teleop
	- [x] Test wireless again
- [ ] > [!check] AirBnB
	- [x] Purchase AirBnB
	- [x] Submit reimbursement to eSAB
	- [x] Submit SOFs refund request
- [ ] > [!Todo] Requirements Final Deliverables
	- [x] Sponsor background
	- [x] Gantt chart
	- [x] Functional requirements + fit criteria
	- [x] Goal refinement graph
	- [x] AI disclosure
	
	@{2026-05-01}
- [ ] > [!error] Pre Comp Checklist
	- [ ] Check remote router range
	- [x] Antenna and cam mounts on bot
	- [x] Enough USB slots?
	- [x] Packing list
	- [x] Mini PC 2 up to date
- [ ] > [!error] Purchases
	- [x] USB expansion module (need 4 more USB-A at least)
- [ ] > [!error] Next Year Notes
	- [ ] Sensor mounting locations and wiring locations need to be in the trade studies sketches
	- [x] Kill gazebo switch to mujoco
	- [ ] Documentation scavenger hunt/race
	- [ ] Service needs to abstract all of the joystick stuff. I do not want to manually parse joystick indexes anymore
	- [x] Buy cheap logitech controller
	- [ ] 2d lidar as odometry library rfto laser odometry (easy to set up)
	- [ ] Daemons and scripts need to be cleaned up and formalized
	- [ ] Don't start the launch files with all the same thing pretty please
	- [ ] Foxglove better integration or maybe rerun
	- [ ] Solidworks -> onshape -> urdf export
	- [ ] Install dependencies scripts
	- [ ] Cheap camera to reduce bandwidth usage to 4 mbp/s?
	- [ ] Better microcontroller firmware
	- [x] Mock components for testing so teleop doesnt crash when no can or arduino
	- [ ] Full teleop operations or match operations flowchart (not just fluffy but the full hey this is broken so do this details)
	- [ ] Practice blind runs beforehand in the volleyball pit
	- [ ] Need better telemetry/camera angles to see wtf the bot is doing
	- [ ] Get a bin that ALL programming stuff can go in (maybe print or make a holding board)
	- [ ] Rotary encoders for everything
	- [ ] Make sure we have USB 3 cables for cams next year
	- [ ] Have a better interfaces list
	- [x] Fix the stupid ctre library error in the setup scripts or something so it stops annoying me
	- [x] Look into ignition by inductive automation

%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,true,false]}
```
%%