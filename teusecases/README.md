# TE-Use-Cases

### Modeling and Experimenting with Transactive Energy Use-Cases

This project aims to develop models of power grid and associated transactive energy distributed energy resources using WebGME modeling environment and build several use-cases for the application of transactive energy mechanisms in demonstrating its feasibility and effectiveness in managing the power demand and supply balance in the presence of intermittent energy generation sources and varying power demands.

The project will replicate the TE use-cases published by the National Institute of Standards and Technology (NIST) using Vanderbilt University's GridLAB-D Design Studio. The work involves developing the corresponding grid models for GridLAB-D, along with associated grid elements that support the individual use-cases. The six (6) use-cases are described in Appendix A of the following publication below:
* https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=921591

The following instructions for replicating the six(6) use-cases are structured as :

	1) GridLAB-D Design Studio
	
		a) What is the GridLAB-D Design Studio?
		
		b) Where is the GridLAB-D Design Studio?
		
		c) How to Use and Experiment Grid Models with GridLAB-D Design Studio?
		
		d) How to Edit Grid Models in glm File?
		
		e) How to Import the GridLAB-D Model into the Design Studio?
		
		f) How to Simulate the GridLAB-D Model in the Design Studio?
		
	2) Use Case 1: Peak Load Management
	
	3) Use Case 2: Wind Energy Balancing Reserves
	
	4) Use Case 3: High-Penetration PV and Voltage Control	
	
	5) Use Case 4: Electric Vehicle Charging Time Coordination
	
	6) Use Case 5: Island Mode Microgrid Balancing
	
	7) Use Case 6: Sudden Loss of Supply Management

1) About GridLAB-D Design Studio:

a) What is GridLAB-D Design Studio?

This design studio provides a web-based platform for modeling and simulating power-grids that allows working with GridLAB-D model files(.glm file) and simulates them. GridLAB-D design studio converts the textual code of the grid distribution system i.e the 'glm' files to elegant and easily manipulatable the GUI(Graphic User Interface) based distribution network. The tools and means provided in the design studio give a user the capability to edit the distribution system in the GUI format. Once the editing of the GUI based distribution system is completed. Users can invoke the plugin to generate code (i.e. glm file) as well as can simulate and get the output from the GridLAB-D software installed on the server. 

b) Where is the GridLAB-D Design Studio?

To access the GridLAB-D Design Studio, click the link: https://cps-vo.org/group/gridlabd. 

c) How to Use and Experiment Grid Models with GridLAB-D Design Studio?

A demo video is provided by the website for someone new to GridLAB-D Design 	Studio to get familiar with the process of creating a simple grid model. You can also experiment with all those template models implemented in the design studio to get familiar with all those configurations (market, controller, and triplex line, etc) provided by the platform. If you have any questions related to the parameters or functions of any element, for example, the controller, you can search on Google by directing typing ‘controller GridLAB-D Wiki’. The GridLAB-D Wiki page will tell you everything about the element.

d) How to Edit Grid Models in glm File?

After you are familiar with the meaning and functions of those commonly used configurations and getting to know how to make a simple grid model in the GridLAB-D Design Studio, you can generate the model you create in glm format. As you already know, glm file is the text form of the grid model. Instead of editing the grid models in GridLAD-D Design Studio, editing the glm file is recommended. This is because sometimes if your model is too large, making changes to your model in the Design Studio would be slow. So editing the glm file a much better choice. However, if you’re a Mac user, you can only open the glm file in Linux Ubuntu environment.

(The instruction for installing a Linux Ubuntu virtual machine and downloading GridLAB-D is here: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Instrucions%20for%20Gridlad-D%20installation%20on%20Mac.docx)

e) How to Import the GridLAB-D Model into the Design Studio?

As long as your Linux Ubuntu is all set, the Text Editor built-in Ubuntu will open the glm file for you. Then you can edit the source code of your model. After you’ve done the editing, you can import the new glm file in the GridLAB-D Design Studio by clicking ‘ImportGLM’  to gain an image view of your grid model.

f) How to Simulate GridLAB-D Model in the Design Studio?

In general, to simulate a grid model, you first click ‘SimulateWithGridlabD’ button right below the ‘ImportGLM’ need to first input dependency.zip file which contains weather or schedule information needed for your model before simulating. After that, you click For more detailed instruction, you can watch the demo video on the GridLAB-D Design Studio website. The link is here: https://cps-vo.org/group/gridlabd. The simulation will generate .csv file(s) which record(s) any elements or parameter you want to record. Then you can analyze the data by drawing a line chart to show the changes in the designated parameter.

2) Use Case 1: Peak Load Management

a) Use Case Description:

In a typical summer day, a large amount of energy is consumed by HVAC systems (which include air conditioning and cooling systems) installed in every household in the power grid. Suddenly, the thick clouds block the sunlight, causing solar panels installed in the grid system to not generate any energy. While the supply of energy declines, the demand for energy does not decrease. So the gap between demand and supply of energy emerges. There would also be a peak demand load situation that makes the whole grid unstable. For a more detailed description of Use Case one (1), click the following link: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Six%20TE%20Use%20Case.pdf.

b) Goal(s) for the Simulation: 
We want to use whatever strategy to mitigate the burden of the grid when it encounters such a peak demand load scenario. We expect to see the burden of the grid is eliminating and the demand curve of total power consumed by the grid inclines and declines smoothly, without any sudden drastically increasing or decreasing tendency.

c) Strategies for Managing the Peak Load:

In this use case, because the grid is lack of the supply of energy, we need to stimulate DERs (Distributed Energy Resources) to send excessive energy back to the main grid to mitigate the burden of the grid. We also want prosumers to participate in the market to bid the price with consumers, so that consumers can decide whether they are going to buy the energy based on the price. As we are facing a lack of energy situation, the price increases, causing a lot of consumers to not buy the energy. And those prosumers that participate in the market can further mitigate the burden by selling energy. To achieve this goal, we need to implement a double-auction market that allows buyer bidders and seller bidders (prosumers and consumers) to bid the price. 

Technical Steps:

First, we set the parameter special_mode of the market to NONE so that both buyers and sellers can come into the market. Second, for controllers to bid into the market and decide whether the utilities they control need more energy based on the price, we need to set the parameter bid_mode of  all controllers to ON. 

d) Steps for the Simulation:

We first create a grid model in GridLAB-D Design Studio to simulate the peak load scenario, and that is what we call the base case. Then we edit the model following the Technical Steps described above and re-run the test. That is what we call the test case. After that, we generate two line charts that describe the total amount of power consumed by the grid in two csv files and analyze the data.

The link for base case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_1/model/uc1_base_test_model.glm.

The link for test case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_1/model/uc1_simulation_test_model.glm. 

The dependencies.zip file needed for this simulation: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_1/model/dependencies_files/use_case_1_dependencies.zip)

e) Simulation Results:

By comparing two line charts which depict the parameter measred_real_power that shows the Toal amount of power consumed by the grid in every time step (every 5 minutes) in the base case and the test case. We can see the peak load curve is eliminated in the test case scenario. So by implementing our strategies, we successfully managed the peak load situation. For detailed simulation results, view the link: https://github.com/SimIntToolkit/teusecases/tree/master/usecase_1/uc1%20simulation%20results.

3) Use Case 2: Wind Energy Balancing Reserves

a) Use Case Description:

A grid system is implemented wind turbines to generate energy. However, energy generation by wind cannot be stable because wind power generation is largely depending on the weather. In this grid system, the main source of energy generation is by the wind. As the wind power is insufficient to support the whole grid system(the supply of energy decreases), how do we rebalance the supply and demand of energy to re-stabilize the grid. For a more detailed description of Use Case two (2), click the following link: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Six%20TE%20Use%20Case.pdf.

b) Goal(s) for the Simulation: 

The goal we want to achieve in Use Case two(2) is quite alike that in Use Case one(1). We want to use whatever strategy to stabilize the whole power grid when it encounters a lack of energy scenario caused by the instability of wind energy. We expect to see the demand curve of total power consumed by the grid inclines and declines smoothly, without any sudden drastically increasing or decreasing curve.

c) Strategies for Managing the Instability of Wind Energy:

In this use case, the grid may encounter a lack of the supply of energy situations because of the instability of wind energy. As supply of energy decreases, the price increases. We want consumers to participate in the market to bid the energy price to decide whether they are going to buy the energy based on the price. To achieve this goal, we use the same strategies in Use Case 1.

Technical Steps:

First, we set the parameter special_mode of the market to NONE so that both buyers and sellers can come into the market. Second, for controllers to bid into the market and decide whether the utilities they control need more energy based on the price, we need to set the parameter bid_mode of  all controllers to ON. 

d) Steps for the Simulation:

We first create a grid model that takes wind energy as its only source of energy generation in GridLAB-D Design Studio. Then we follow the Technical Steps described above to edit the model by setting the parameter special_mode of the market to NONE and parameter bid_mode of  all controllers to ON.

The link for the test case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_2/model/uc2%20_test_model.glm.

The dependencies.zip file which contains the weather data TN-Nashville.tmy2 needed for this simulation: 

https://github.com/SimIntToolkit/teusecases/blob/master/usecase_2/model/dependency_files/uc2_dependencies%20.zip.

e) Simulation Results

By simulating on GridLAB-D Design Studio, we could generate the line chart which shows the total amount of power consumed by the grid every time step (every 5 minutes) in the test case, we can see the consecutive changes of the total amount of power used in the grid during our simulation time. For detailed simulation results, view the link: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_2/simulation_results/uc2%20result.xlsx.

4) Use Case 3: High-Penetration PV and Voltage Control

a) Use Case Description:

Nowadays, many families have solar panels (PV systems) installed either on the root roof or the ground in their households. On a summer day, a large amount of PV systems can provide excessive energy. If the amount of excessive energy produced by those PVs is extremely large, reverse power flow will occur, making the whole grid unstable. So we need to find a way to restore the excessive energy and prevent the reverse power flow. For a more detailed description of Use Case three (3), click the following link: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Six%20TE%20Use%20Case.pdf.

b) Goal(s) for the Simulation: 

The goal we want to achieve in this use case is that we want to use whatever devices to restore the excessive energy generated by the PVs. And hopefully it could release the energy when the grid is lack of electricity. We expect to see the demand “gap” shown in the demand curve of total power consumed by the grid is filled by excessive energy that is released from our storage device in the test case.

c) Strategies for Restoring and Releasing the Excessive Energy :

Many devices could be used to restore energy. In this use case, I choose the object battery as our storage device. When the PV generates excessive energy, the battery restores the energy. At night, when PV cannot provide any energy back to the grid, the battery releases the energy into the grid system and compensate for the energy loss. Under this circumstance, there would be no reverse power flow.

Technical Steps:

We implement the battery object by setting the parameters state_of _charge to 0.5, generator_mode to supply_driven so that it can detect whether there is excessive energy in the grid. If there is, the battery absorbs the excessive power. Otherwise, it releases energy to fill the demand gap in the grid.

d) Steps for the Simulation:

We first create a grid model that only contains PV systems(solar panels and inverters, etc) as our base case. We run the base case simulation in GridLAB-D Design Studio with dependencies.zip file. We generate the base case csv file and the line chart which records both the solar panel energy output and the total amount of power consumed by the grid. Then we follow the Technical Steps described above to edit the base case model and re-run the simulation.

The link for the base case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_3/model/uc3_base_model.glm. 

The link for the test case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_3/model/uc3_test_model.glm. 

The link for the dependencies.zip in this simulation: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_3/model/dependency_files/uc3_dependencies.zip.

e) Simulation Results:

By running the simulation of base and test cases on GridLAB-D Design Studio, we could generate two line charts which show the changes of the total amount of power consumed by the resident, total power output of solar panels, and the total power output of battery every time step (every 5 minutes) in both cases. After we analyze the data and compare the line charts, we can see how the battery helps to restore the excessive energy and fill the demand gap in the base case. For detailed simulation results, view the following link: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_3/simulation_results/uc3_result.xlsx.
		
5) Use Case 4: Electric Vehicle Charging Time Coordination

a) Use Case Description:

As more and more people choose electric vehicles as their transportation tool to work, more EV(electric vehicles) chargers are installed in the power grid. Normally, all the EVs get charged as soon as they arrive home from work at around 7:00 pm and stopped charging either when they leave home or the battery’s already fully charged. However, given the scenario that people consume a large amount of energy during the night, charging more and more EVs in the same period staring from 7:00 pm causes severe burden to the grid. In this TE use case, we need to find out a way to coordinate the charging time of all the EVs to avoid the peak load that destabilizes the system. For a more detailed description of Use Case four (4), click the following link: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Six%20TE%20Use%20Case.pdf.

b) Goal(s) for the Simulation: 

The goal we want to achieve in this use case is that we want to avoid the peak load demand situation after we successfully coordinate the charging time of EVs. We expect to see the demand curve of total power consumed by the grid inclines and declines smoothly in test case during our simulation time, without any sudden drastically increasing or decreasing curve that occurs in the base case.

c) Strategies for Coordinating EVs Charging Time:

Many strategies can be used to coordinate the EVs’ charging time. In this use case, I set the start time of charging all EVs from mid-night(00:00 am). This means even if EVs arrive home at 7:00 pm, it will not get charged until midnight. This strategy can largely mitigate the burden of the system because the energy consumption during mid-night is really low. Even if all EVs are charged in the same period at midnight, the grid will not encounter peak load demand problem.

Technical Steps:

We implement the evcharger_det object under house object in our model to simulate the charger for EV. By default, the evcharger_det starts charging the EV as soon as the EV arrives home. In the base case, we set the parameters arrival_at_home to be 1900 (7:00 pm) and duration_at_home to be 12h (12 hours). In the test case, we set the arrival time of all cars to be 0000 (00:00 am) so that all the EVs get charged at mid-night.

d) Steps for the Simulation:

We first create a grid model that contains evcharger_det objects in GridLAB-D Design Studio. 
We first simulate the base case. Then we follow the Technical Steps described above to edit the base case model and re-run the simulation. After we analyze the data and compare the line charts which record the total amount of power consumed by the grid during the simulation time in two csv files, we can see the “peak load curve(s)” are mitigated. 

The link for the base case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_4/model/uc4_base_model.glm. 

The link for the test case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_4/model/uc4_test_model%20.glm. 

The dependencies.zip file needed for this simulation: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_4/model/dependency_files/uc4_dependencies.zip.

e) Simulation Results:

By running the simulation of base and test cases on GridLAB-D Design Studio, we could generate the line charts in two csv files which show the total amount of power consumed by the grid every time step (every 5 minutes) in both cases. We can see the “peak load curve(s)” that emerges around 8:00 pm are mitigated. 
For detailed simulation results, view the following link: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_4/simulation_results/uc4%20result.xlsx.

6) Use Case 5: Island Mode Microgrid Balancing

a) Use Case Description:

A microgrid is a small-scaled grid that has all elements including DERs, ZIPloads, Houses, etc. The microgrid can operate in either island mode or connected mode. Normally, it is connected with the main grid(operating in connected mode). The energy generated by DERs in the microgrid can be transmitted to the main grid. However, if some disruptive events happen in the main grid, the microgrid will automatically disconnect itself from the main grid and operate in island mode. This use case requires us to simulate an island mode microgrid while trying to balance the demand and the supply of energy to avoid peak load situation. 
For a more detailed description of Use Case five (5), click the following link: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Six%20TE%20Use%20Case.pdf.

b) Goal(s) for the Simulation: 

The goal we want to achieve in this use case is that we want to create an island mode microgrid that is automatically switching from its connected mode caused by the disturbance in the main grid. Also, we need to implement the same supply and demand balancing strategy we used in Use Case one(1) to balance the supply and demand of energy inside the microgrid to avoid the peak load demand situation. If the above two goals are achieved, the microgrid can operate in island mode stably and self-sufficiently.

c) Strategies for Simulating an Island Mode Microgrid

Between our microgrid and main grid, there is a switch line that connects both grids. When the microgrid first operates in connected mode, the status of the switch object is CLOSED. If the main grid encounters some disruptive events, the status of switch object will be OPEN so that the microgrid can disconnect from the main grid and operates in island mode. For the switch object to change its status automatically, we can use a player file to control it, so that the switch can help to change the microgrid’s operating mode from connected to island. To balance supply and demand within the microgrid, we need to implement a double auction market and controllers that control the behavior of appliances based on the market_clearing_price. 

Technical Steps:

We implement the switch object which connects two center nodes in both grids. The switch.player file controls the status of the switch and it decided when the microgrid is switching to island mode. After that, we implement a market object and controllers for each house. We set the parameter special_mode of the market to NONE so that both buyers and sellers can bid the price in the market. And for controllers to bid into the market and decide whether the utilities they control need more energy based on the price, we need to set the parameter bid_mode of  all controllers to ON. 

d) Steps for the Simulation

We first create a grid model which has a microgrid and the main grid, and these two grids are connected by the switch line. Then we follow the Technical Steps described above to edit the original model. Before running the simulation, a recorder object is implemented in our model to record the change of the total amount of energy consumed by microgrid from its connected mode to island mode. Then we simulate the model in GridLAB-D Design Studio. After that, we can draw out the line chart from the csv file and can see the changes in the total amount of power consumed by the microgrid residents.

The link for the test case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_5/model/uc5_test_model.glm. 

The dependencies.zip file needed for this simulation: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_5/model/dependency_files/uc5_dependencies.zip.

e) Simulation Results:

By simulating the test case on GridLAB-D Design Studio, we could generate the line chart from the csv file which records the total amount of power consumed by the grid every time step (every 5 minutes) in the test case. We can see the changes in the total amount of power consumed by the microgrid residential houses from connected mode to island mode. 
For detailed simulation results, view the following link: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_5/simulation_results/uc5%20result.xlsx.

7) Use Case 6: Sudden Loss of Supply Management

a) Use Case Description:

In a typical winter day, transmission lines may encounter malfunctioning problems caused by the cold weather. Under this situation, the amount of energy that can be transmitted to all the houses in the grid decreases drastically. In our grid model, we need to simulate the energy loss caused by the transmission line malfunctioning. Facing this energy supply shortage problem, we still need to balance the supply and demand for energy using the price to avoid the peak load situation in the grid. 

For a more detailed description of Use Case six (6), click the following link: https://github.com/SimIntToolkit/teusecases/blob/master/scr/Six%20TE%20Use%20Case.pdf.

b) Goal(s) for the Simulation: 

The goal we want to achieve in this use case is that we first want to create a grid model that is experiencing the energy loss caused by the cold weather. Also, we need to implement the same supply and demand balancing strategy we used in Use Case one(1) to balance the supply and demand of energy inside the grid to avoid the peak load demand situation. If the above two goals are achieved, the grid can operate stably and self-sufficiently.

c) Strategies for Simulating Energy Loss:

To simulate the malfunctioning of transmission lines, we implement two parameters of the transformer line object: full_load_loss and no_load_loss. Full_load_loss describes the energy losses of the transformer when at rated load, and the no_load_losss describes the energy losses through the transformer when there is no load. After that, to balance supply and demand within the grid, we need to implement a double auction market and controllers that control the behavior of appliances based on the market_clearing_price just like what strategy in Use Case one(1);

Technical Steps:

We implement the transformer object which can be used to simulate the energy loss caused by the transmission line. Every transformer is extended from the transformer_configuration. So we implement those two parameters full_load_loss and no_load_loss in transformer_configuration. We set the value of full_load_loss to be 0.06, and the value of no_load_loss to be 0.03. Two player files are implemented to control these two parameters to simulate the process when the transformer is experiencing energy loss. After that, we implement a market object and controllers for each house. We set the parameter special_mode of the market to NONE so that both buyers and sellers can bid the price in the market. And for controllers to bid into the market and decide whether the utilities they control need more energy based on the price, we need to set the parameter bid_mode of  all controllers to ON. 

d) Steps for the Simulation:

We first create a grid model which has houses and transformers, and market, etc. Then we follow the Technical Steps described above to edit the original model. Before running the simulation, a recorder object is implemented in our model to record the change of the total amount of energy consumed by all houses in the whole grid. Then we simulate the model in GridLAB-D Design Studio. After that, we can draw out the line chart from the csv file and can see the changes in the total amount of power consumed by all the residents.

The link for the test case model: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_6/model/UC6_test_model.glm. 

The dependencies.zip file needed for this simulation: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_6/model/dependency_fies/uc6_dependencies.zip.

e) Simulation Results:

By simulating the test case on GridLAB-D Design Studio, we could generate the line chart from the csv file which records the total amount of power consumed by the grid every time step (every 5 minutes) in the test case. We can see the changes in the total amount of power consumed by the grid residential houses when the grid is experiencing energy loss. For detailed simulation results, view the following link: https://github.com/SimIntToolkit/teusecases/blob/master/usecase_6/simulation_results/uc6%20result.xlsx.
