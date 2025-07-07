The evolution of smart cities and Industry 5.0 has necessitated the deployment of intelligent, secure, and autonomous transportation systems. Among the emerging technologies facilitating this shift are Unmanned Aerial Vehicles (UAVs), commonly referred to as drones. These autonomous agents are increasingly integrated into edge-cloud networks to handle tasks ranging from surveillance and delivery to emergency response. However, coordinating and securing the workflow of multiple drones in real-time introduces a host of challenges, including scalability, latency, authentication, and task verification.

To address these issues, this case study introduces a simulated dataset representing a Blockchain-Enabled Self-Autonomous Intelligent Transport System. The system employs edge-cloud orchestration and blockchain validation to coordinate 10,000 drone tasks under various conditions. The data captures multi-dimensional aspects of drone operations across a simulated urban environment with varied edge nodes and blockchain-backed authentication mechanisms.

2. Dataset Description
The dataset comprises 10,000 entries, each representing a drone’s task assigned and executed in a hybrid edge-cloud environment. Below is an overview of the key fields captured:

Timestamp: Records the time of the task assignment or update.

DroneID: Unique identifier for each drone (e.g., DRONE_0001).

Location: Urban sectors where the task is performed (e.g., Sector-A).

TaskType: Workflow tasks assigned, including Surveillance, Delivery, Traffic Monitoring, Emergency Response, and Mapping.

TaskDuration(mins): Time taken to complete the task.

Status: Task status — Pending, In Progress, Completed, or Failed.

EdgeNode: The edge server managing the drone (EdgeNode_1 to EdgeNode_5).

BlockchainValidated: Boolean flag indicating whether the task and data logs were successfully written and verified via a blockchain ledger.

BatteryLevel(%): Remaining battery percentage of the drone at the time of logging.

Payload(kg): Weight of the object the drone is carrying (if any).

This dataset is suitable for modeling intelligent task allocation, energy optimization, autonomous scheduling, anomaly detection, and secure data validation in edge-cloud and blockchain-integrated smart city infrastructures.

3. System Architecture and Simulation Environment
To generate meaningful insights from the dataset, a testbed was simulated using a container-based virtualization environment to mimic edge-cloud deployment. Five edge nodes were defined, each representing a different geographic area within a simulated smart city.

Key Components:

Drone Controller Simulator: Generated real-time drone behavior using a task distribution engine.

Edge Cloud Nodes: Handled initial task computation, preprocessing, and data aggregation.

Blockchain Layer (Simulated Hyperledger Fabric): Verified all logs and task completions. Each task with BlockchainValidated = "Yes" indicates a successful smart contract verification.

Centralized Cloud (Test Oracle): Used only for storing completed task summaries and logs.

The testbed was created in a Kubernetes environment with containerized microservices to simulate low-latency task allocation. Smart contracts were deployed on the Hyperledger test network to authenticate and log transactions related to drone tasks.

4. Experimental Scenarios and Evaluation Metrics
To evaluate the performance of the system, the dataset was analyzed under various scenarios including:

High-Load Task Simulation: Simulating peak task assignment rates (e.g., emergency response during natural calamities).

Battery-Aware Scheduling: Monitoring drone battery consumption patterns based on payload and task type.

Blockchain Validation Delays: Measuring time between task completion and blockchain confirmation.

Edge Node Load Distribution: Tracking how evenly tasks were distributed across nodes.

Evaluation Metrics Used:

Task Success Rate (%): Percentage of tasks marked as 'Completed'.

Blockchain Validation Rate (%): Ratio of tasks successfully validated over blockchain.

Latency (ms): Simulated time delay between task completion and blockchain validation.

Battery Efficiency Index: Average battery consumed per kg of payload per minute.

Edge Load Balance Score: Standard deviation of the number of tasks handled by each edge node.

5. Results and Insights
The system's overall performance from the dataset analysis yielded the following findings:

a. Task Completion and Success Rate
Out of 10,000 tasks, approximately 77% were successfully completed, with failure rates higher in areas with poor edge-node load balancing. Mapping and Surveillance tasks had the highest success rates due to lower payloads and shorter durations.

b. Blockchain Validation
Around 83% of tasks were successfully validated via blockchain. Tasks that failed validation were often linked with either communication delays, node congestion, or low battery shutdowns before log transmission. Emergency response tasks saw a slightly higher validation failure rate (19%), possibly due to their urgency and system stress under high load.

c. Battery and Payload Dynamics
A key finding was that battery levels below 30% significantly increased task failure rates, especially for delivery tasks with payloads exceeding 3kg. Tasks with high battery usage correlated with extended durations and larger payloads, underlining the need for predictive battery-aware task scheduling.

d. Edge Node Load Imbalance
EdgeNode_2 and EdgeNode_5 handled significantly more tasks (up to 2.5x) than the others, leading to localized delays and higher task failure rates. This highlights the importance of adaptive load balancing algorithms to maintain QoS (Quality of Service).

e. Task Latency and Validation Time
Average validation delay (simulated) was 1.8 seconds, but this rose to 3.2 seconds under high task load, especially in sectors with high delivery traffic. The results suggest blockchain integration is feasible but requires latency-aware smart contract optimization for critical real-time tasks.
