# PTC 

Performance test center. Docker based service to help user manage, organize, execute JMeter test and get detailed performance report. 

### Prerequisites

Docker is properly installed and configed

## Getting Started

Download docker image from docker hub:
  - [mongo](https://hub.docker.com/_/mongo/): Mongo db
  - [ptc](https://hub.docker.com/r/wankutuzi/ptc/): JMeter master along with PTC main service
  - [jmeterslave](https://hub.docker.com/r/wankutuzi/jmeterslave/):JMeter slave to execute test and send report back to master
  
### Note 
- [jmeterslave](https://hub.docker.com/r/wankutuzi/jmeterslave/) and [jmetermaster](https://hub.docker.com/r/wankutuzi/jmetermaster/) are built base on [jmeter3.0base](https://hub.docker.com/r/wankutuzi/jmeter3.0base/)
- [PTC](https://hub.docker.com/r/wankutuzi/ptc/) is built base on jmetermaster
- Feel free to edit the [Dockerfile](workbench/docker%20file) and build your own docker image with selected version of Java/JMeter/NodeJS etc.

### Deployment
1. Start mongo db. Bind default mongo db port **27017** to selected server port
```
docker run -dit -p 27017:27017 --name mongo mongo
```
2. Start as many JMeter slaves as needed
```
docker run -dit --name slave1 jmeterslave
docker run -dit --name slave2 jmeterslave
docker run -dit --name slave3 jemterslave
```
3. Inspect IP address of jmeter slave(s). 
```
docker inspect --format '{{ .Name }} => {{ .NetworkSettings.IPAddress }}' $(docker ps -a -q)
```
Start PTC(JMeter master) by passing in mongo and slave information. 
```
docker run -it -p <server port>:<container port 8080 by default> -e mongoAdd=<IP Address of mongo db> -e mongoPort=<Port of mongo db> -e slaves=<Slave IP seperated by comma> --name ptc ptc
```
[](workbench/command.png)

4. If you saw "db conncetion established", you are ready to go. Visite http://localhost:8080 to use PTC

## Running the tests

1. Register and login the system
2. Create a project if there isn't any
3. Go to Performance Testing->JMeter test page to add a test
- Choose a project
- Fill in test name
- Fill in host and port in needed
- Specify some critical parameters (like iteration, thread user etc.) by dragging the slider
- Click save button, test will be executed automaticlly.
[](/workbench/test.png)
4. After test status becomes to 'Finished', click log to check the [report](workbench/dashboard/index.html).

### Note
You can define parameters like thread user, rampup time... directly in JMeter test case, that way the parameters you specified on web page won't take effect. Otherwise, use `${__p()}` to take the parameter. Here is an [example](/)

## Manage your case
1. **Object** tests are orgnized under project. Open an object 
- All tests that under this project will be listed
- Object name and description can be updated
- Object can be deleted only if there is no test under it
2. **Test** A test contain a JMeter case and related configuration. Open a tset:
- Test execution history will be listed
- Test can be updated by changing the case and/or the configuration
- Test can be re-executed directly by click tht 'start' button
- Test can be deleted, and all its execution history will be deleted together
3. **Activity** to log some major event like test creation and updat
- You can check activity on homepage- dashboard
- If a test gets deleted, all its related activities will be deleted too

## Permission Control
1. Firt registered user is super user, and otheres will be normal user
- Super user can visit all the data. 
- Normal user can only visit the data created by himself/herself 


Explain what these tests test and why

```
Give an example
```

### And coding style tests

Explain what these tests test and why

```
Give an example
```

## Deployment

Add additional notes about how to deploy this on a live system

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

**Wenwen Yang** wenwen.yang88@gmail.com


## License
