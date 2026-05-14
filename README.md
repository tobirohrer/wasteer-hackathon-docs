# Waste Bunker Optimization Challenge

Waste incineration plays a crucial role in modern energy systems by converting non-recyclable waste into usable energy. However, efficient incineration is not just about burning waste. It requires smart bunker management to ensure stable operations and optimal energy yield.

At Wasteer, our mission is to make waste-to-energy operations more intelligent and data driven. One of the most critical components of this process is the waste bunker, where different waste streams are temporarily stored and mixed before incineration.

For this challenge, you will work with real industrial data to optimize waste bunker management.

# 1. Data

You are given the following data which is available here: <link to data>:

1. **LiDAR scans of the bunker**  
	3D surface scans showing the current fill level (visible waste surface) of the bunker.
2. **Truck delivery records**  
	Timestamped list of trucks delivering waste. Each entry includes the waste type and quantity (in kg) delivered into the bunker.
3. **Information per waste type (MISSING)**  
	Mapping from waste type to calorific value (kJ/kg).

**Note:**  
The dataset does not explicitly include information about material removed from the bunker through incineration. Participants are encouraged to make and justify reasonable assumptions where necessary. Partially observable systems and incomplete operational data are common in real industrial environments and are part of the challenge 😉.

# 2. Problem Statement

There are two related problem statements that reflect real challenges faced by Wasteer today. Solving them would have a real-world impact by making the process more efficient. It is recommended that you start with Problem 1 and apply your learnings to Problem 2.

## Problem 1: Bunker Fullness Estimation

The first task focuses on understanding how much waste the bunker can still accept until it is "full".

### Objectives

1. **Estimate how much waste can still be added to the bunker**
	- Calculate how much of each waste type (in kg) can still fit in the bunker until the full threshold is reached.
    	- The definition of "full" is shown by the red line in Figure X (missing).
	- Note that each waste type has different density and compression properties, so the same mass of different waste types will change bunker fullness differently.
    	- Use the LiDAR data along with truck delivery records to perform this estimation.
	- Showcase your approach at different points in time by selecting several LiDAR scans and demonstrating how much of each waste type could still be added at those times.

	**Bonus points:**
	- Investigate whether LiDAR data alone is sufficient for estimating bunker fullness, or whether the type of waste already present in the bunker should also be considered.
    	- Different waste types may affect compression differently (for example, heavy items on top of lighter materials can compress more). Explore whether this effect can be observed in the provided data.
	- Note: The starting point of the data is a "black box" regarding the exact waste composition in the bunker.

2. **Estimate material density per waste type**
	- Determine the density (kg/m^3) of each waste type based on the data, taking into account how it contributes to overall bunker volume and fullness.
	- This may be required to solve the first objective, but density estimation per waste type is also an explicit goal.


## Problem 2: Optimal Waste Mix

Building on problem 1, the second task focuses on optimizing the energy potential of the bunker. The bunker operates most efficiently when the average calorific value is around 10 kJ/kg. Some waste types have lower calorific values, while others have higher values.

Your task is to estimate the optimal mix of waste required to maintain a stable average calorific value close to 10 kJ/kg, while considering the remaining bunker capacity. Minimizing fluctuations is important, as variations in calorific value reduce bunker operation efficiency.

### Objective

Determine the optimal waste composition:

- Each waste type has an associated calorific value, as shown in Table X (missing).
- Identify which waste types should be added to the bunker, and in what quantity (kg), to maintain an average calorific value of 10 kJ/kg. Make sure to include your learnings from problem 1 to not exceed bunker capacity.
- Showcase your approach using truck delivery record data:
  - Assume that at the start of the data, the average calorific value inside the bunker is 10 kJ/kg.
  - You may define your own reasonable assumption for the initial bunker mass.
  - Select several truck delivery records from the dataset to showcase your approach. Estimate how individual deliveries change the average calorific value inside the bunker and determine which waste type(s) and quantities would be needed to bring it back toward 10 kJ/kg. Remember to consider your learnings from problem 1 to make sure the bunker does not exeed its limits.

# Infrastructure

You will be assigned a GPU server (NVIDIA L4 24GB) for the event to be able to train models if you would like to. Each team is assigned one server with a preconfigured JupyterLab environment (including torch and tensorflow)

## Connecting to your Server

1. Write an mail to XYZ with your teamname. You will receive your keypair and IP necessary to connect to the server as response.
2. Connect to your GPU server via SSH `ssh -i <path_to_private_key> hacker@<ip_address>`
3. Start your environment `start-jupyter`
4. Create SSH tunnel `ssh -i <private_key_file> -N -L 8888:localhost:8888 hacker@<ip_address>`
5. Connect to Jupyter Lab by opening your browser and go to `http://localhost:8888`
6. Start hacking

## Customizing the Server

- Note that your user `hacker` has passwordless sudo access to the server with your user. You are free to install additional tools and customize the environment as needed 😉
- The preconfigured environemnt is available as `ml` conda environment. Feel free to create a new one if you like.

## Server Availability

To manage compute resources efficiently, the GPU servers will be available during the following times:

- Thursday: XX:00 – XX:00
- Friday: YY:00 – YY:00

If you need it outsite this timeframes come and talk to us!
