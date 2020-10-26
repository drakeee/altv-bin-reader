# altV Bin Reader

Hey there! I just made some basic reader which can read vehmodels.bin and vehmods.bin file inside your server data folder.

Please note that you should change the SDK.h location in the header file to your correct location:
https://github.com/drakeee/altv-bin-reader/blob/6f4c9f375595e778be361da822ad5d1b12b6e77f/CVehModels.h#L3

# Usage

The usage of this reader is very simple:
```cpp
auto &dataReader = VehicleModels::Instance(); //instantiate the reader

VehicleModels::VehicleInfo* bison_name = dataReader.GetVehicleInfo("bison"); //you can get vehicle informations by name
VehicleModels::VehicleInfo* bison_hash = dataReader.GetVehicleInfo(202226976); //also you can get vehicle informations by hash

auto bison_by_name = dataReader["bison"]; //you can also use the [] operator for both cases as well
auto bison_by_hash = dataReader[202226976];

if (bison_name == nullptr)
{
	//vehicle information not found
}
else
{
	VehicleMods::ModKit* modKit = bison_name->vehicleModkits[0]; //it will return INVALID_MODKIT if there is no modkit in the given index
	//vehicle information found
}

//if you want you can loop through all of the vehicle information by hashes
for (auto vehicleInfo : dataReader.GetVehicleInfosByHash())
{
	//vehicleInfo.first -> this will hold the vehicle hash number
	//vehicleInfo.second -> will point to a VehicleInfo*
}

//also you can loop through all of the vehicle informations by vehicle names
for (auto vehicleInfo : dataReader.GetVehicleInfosByString())
{
	//vehicleInfo.first -> this will hold the vehicle name
	//vehicleInfo.second -> will point to a VehicleInfo*
}
```
