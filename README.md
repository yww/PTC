# PTC 

Performance test center. Docker based service to help user manage, organize, execute JMeter test and get detailed performance report. 

## Getting Started

Download docker image from docker hub:
  - [mongo](https://hub.docker.com/_/mongo/): Mongo db
  - [ptc](https://hub.docker.com/r/wankutuzi/ptc/): JMeter master along with PTC main service
  - [jmeterslave](https://hub.docker.com/r/wankutuzi/jmeterslave/):JMeter slave to execute test and send report back to master 
  
### Prerequisites

Docker is properly installed and configed

### Note 
- [jmeterslave](https://hub.docker.com/r/wankutuzi/jmeterslave/) and [jmetermaster](https://hub.docker.com/r/wankutuzi/jmetermaster/) are built base on [jmeter3.0base](https://hub.docker.com/r/wankutuzi/jmeter3.0base/)
- [PTC](https://hub.docker.com/r/wankutuzi/ptc/) is built base on jmetermaster
- Feel free to edit the [Dockerfile](docker%20file) and build your own docker image with selected version of Java/JMeter/NodeJS etc.

### Deployment
1. Start mongo db. Bind default mongo db port **27017** to selected server port
```
docker run -dit -p 27017:27017 --name mongo mongo
```
2. Start jmeter slaves  
```
docker run -dit --name slave1 jmeterslave
docker run -dit --name slave2 jmeterslave
docker run -dit --name slave3 jemterslave
```
3. Inspect IP address of jmeter slave(s). 
```
docker inspect --format '{{ .Name }} => {{ .NetworkSettings.IPAddress }}' $(docker ps -a -q)
```
[](public/images/inspect.png)
  
Start PTC(JMeter master) by passing in mongo and slave information. 
```
docker run -it -p <server port>:<container port 8080 by default> -e mongoAdd=<IP Address of mongo db> -e mongoPort=<Port of mongo db> -e slaves=<Slave IP seperated by comma> --name ptc ptc
```
[](public/images/ptc.png)

4. If you saw "db conncetion established", your ready to go. Visite http://localhost:8080 to use PTC

A step by step series of examples that tell you have to get a development env running

## Running the tests

1. Register and login the system
2. Create a project if there isn't any
3. Go to Performance Testing->JMeter test page to add a test
- Choose a project
- Fill test name
- Specify some critical info 

### Break down into end to end tests

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

* **Wenwen Yang** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License


## Acknowledgments

* Hat tip to anyone who's code was used
* Inspiration
* etc
