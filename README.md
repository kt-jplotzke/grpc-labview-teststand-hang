# grpc-labview-teststand-hang

This code shows a condition where the gRPC Client VI hangs at "Wait for Occurrence" when being called from TestStand using the LabVIEW Run Time adapter.

More information on this issue can be found here: (https://github.com/ni/grpc-labview/issues/330)[https://github.com/ni/grpc-labview/issues/330]

## Development Environment Setup
LabVIEW 2021 SP1 f4 64-bit
TestStand 2021 64-bit
grpc-labview 1.0.1.1

## gRPC Proto File
The proto file which was used to generate both the server and client example is in the `proto` directory

## Server
To run the gRPC server for the example, a built x64 EXE is located at `Server\builds\grpc_test_server.exe`.  One can also re-build the server from the LV project at `Server\test_service.lvproj`.

## Client
Both the gRPC client and TestStand sequence files are located in the `Client` directory.

The TestStand sequence `Client\Call VI - No PPL.seq` calls the gRPC Client VI which is not built in a PPL.  This sequence can only be run using the LabVIEW Development Environment adapter, as the run time engine will be unable to find the required gRPC dependencies.

The TestStand sequence `Client\Call VI - PPL.seq` calls the gRPC Client VI which is built in a PPL and is used to show the hang.  This sequence can be run using both the LabVIEW Development Environment adapter (which does not result in a hang) and the LabVIEW Run Time Engine adapter (which does result in a hang).