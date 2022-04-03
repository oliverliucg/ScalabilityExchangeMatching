# DUKE-ECE-568-Scalability: Exchange Matching

## Start server:

```shell
cd server
sudo docker-compose up
```

You can modify the number of cores in docker-compose.yml. For example, 

`command: bash -c "./run.sh db 4"`

would make the program run on four cores.

## How to run tests:

1. Go to the server directory ```server``` and ```./run.sh``` to start the server. Note that you will need to install libpqxx-dev
2. ```cd testing``` to go to the testing directory. Note that you will need to install libboost-all-dev
3. To do functionality testing, run ```make``` then run ```./test.out localhost 12345 20```. This program will load xmls from the ```xmls``` and ```expected``` directory and compare them for testing.
4. To do scalability testing, run ```make``` then run ```./scalability_test.out <#threads> <#epoch> localhost 12345``` while the server is running. The total response one thread will send to the server equals epochs x 20. When you start the server, you can indicate the cores and size of thread pool: ```./run.sh localhost <#cores> <thread-pool-size>```