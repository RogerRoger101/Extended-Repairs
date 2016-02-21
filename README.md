# Extended repair functions	

Installation

Add these files to your mission folder.

Inside your init.sqf add -

JohnO_fnc_repairWheels = compileFinal preprocessFileLineNumbers "JohnO_fnc_repairWheels.sqf";
JohnO_fnc_repairchopper = compileFinal preprocessFileLineNumbers "JohnO_fnc_repairchopper.sqf";
JohnO_fnc_repairchopperhalf = compileFinal preprocessFileLineNumbers "JohnO_fnc_repairchopperhalf.sqf";
JohnO_fnc_vehicleRepairCar = compile preprocessFileLineNumbers "JohnO_fnc_vehicleRepairCar.sqf";

Inside your mission config.cpp

find -
	
			class Repair: ExileAbstractAction
			{
				title = "Repair";
				condition = "call ExileClient_object_vehicle_interaction_show";
				action = "_this call ExileClient_object_vehicle_repair";
			};
			
			
Relace with
			
			class Repair: ExileAbstractAction
			{
				title = "Repair Body";
				condition = "call ExileClient_object_vehicle_interaction_show";
				action = "_this call JohnO_fnc_vehicleRepairCar";
			};
			class RepairWheels: ExileAbstractAction
			{
				title = "Repair Wheels";
				condition = "call ExileClient_object_vehicle_interaction_show";
				action = "_this call JohnO_fnc_repairWheels";
			};
			
Find -

			class Repair: ExileAbstractAction
			{
				title = "Repair";
				condition = "call ExileClient_object_vehicle_interaction_show";
				action = "_this call ExileClient_object_vehicle_repair";
			};
			
Replace with -
		
			class RepairMajor: ExileAbstractAction
			{
				title = "Full Repair";
				condition = "call ExileClient_object_vehicle_interaction_show";
				action = "_this call JohnO_fnc_repairchopper";
			};
			class RepairMinor: ExileAbstractAction
			{
				title = "Minor Repair";
				condition = "call ExileClient_object_vehicle_interaction_show";
				action = "_this call JohnO_fnc_repairchopperhalf";
			};
Thats it!
			