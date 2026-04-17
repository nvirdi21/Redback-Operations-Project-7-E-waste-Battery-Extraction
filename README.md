# SysSims-EwasteExtraction
Systems and Simulations Division for the E-waste extraction project.


## File Structure:

```
robotics-battery-extraction/
│
├── README.md
├── docs/
│   ├── architecture.md
│   ├── ros2_interfaces.md
│   ├── system_diagram.png
│   └── sprint_plan.md
│
├── interfaces/                          
│   ├── msg/
│   │   ├── Detection.msg
│   │   ├── RobotState.msg
│   │   ├── Command.msg
│   │   └── TaskState.msg
│   └── topic_definitions.md
│
├── perception/                          
│   ├── yolo_node.py
│   ├── inference.py
│   ├── camera_interface.py
│   ├── preprocessing/
│   └── utils/
│
├── control/                             
│   ├── simulink/
│   │   ├── controller.slx
│   │   ├── state_machine.slx
│   │   └── models/
│   │
│   ├── matlab_functions/
│   │   ├── pid_controller.m
│   │   ├── trajectory_generator.m
│   │   └── task_logic.m
│   │
│   └── tests/
│
├── simulation/                          
│   │
│   ├── physics/                         
│   │   ├── urdf/
│   │   │   ├── robot.urdf
│   │   │   ├── battery_environment.urdf
│   │   │   └── combined_scene.urdf
│   │   │
│   │   ├── simscape/
│   │   │   ├── model.slx
│   │   │   ├── dynamics.slx
│   │   │   └── parameters/
│   │   │
│   │   └── assets/
│   │       ├── meshes/
│   │       └── textures/
│   │
│   ├── synthetic_data/                   
│   │   ├── generators/
│   │   │   ├── frame_capture.m
│   │   │   ├── bbox_projector.m
│   │   │   ├── pose_to_label.m
│   │   │   └── dataset_builder.m
│   │   │
│   │   ├── camera_models/
│   │   │   ├── sim_camera.slx
│   │   │   ├── projection_model.m
│   │   │   └── calibration.m
│   │   │
│   │   ├── scene_randomisation/
│   │   │   ├── lighting_variation.m
│   │   │   ├── object_variation.m
│   │   │   └── camera_variation.m
│   │   │
│   │   ├── output/
│   │   │   ├── images/
│   │   │   ├── labels/
│   │   │   └── metadata.json
│   │   │
│   │   └── configs/
│   │       ├── dataset_config.yaml
│   │       └── generation_settings.m
│
├── ros2_bridge/                         
│   ├── launch/
│   ├── nodes/
│   │   ├── perception_bridge.py
│   │   ├── control_bridge.py
│   │   └── sim_bridge.py
│   └── configs/
│
├── integration/                         
│   ├── simulink_ros2.slx
│   ├── test_scenarios/
│   ├── rosbag_recordings/
│   ├── latency_tests/
│   └── isaac_sim_tests/
│
└── tools/                               
    ├── data_conversion/
    ├── visualization/
    ├── ros2_debug/
    └── logging_tools/

```
