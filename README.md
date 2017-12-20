# Project Title

PTC-Performance test center. Docker based service help use to manage, organize, excute JMeter test and get detailed performance report. 

## Getting Started

Download docker image from docker hub:
  - [Mongo](https://hub.docker.com/_/mongo/): Mongo db
  - [ptc](https://hub.docker.com/r/wankutuzi/ptc/): JMeter master along with PTC main service
  - [jmeterslave](https://hub.docker.com/r/wankutuzi/jmeterslave/):JMeter slave to execute test and send report back to master 
  
### Prerequisites

Docker is properly installed and configed

### Note 
- Both [jmeterslave](https://hub.docker.com/r/wankutuzi/jmeterslave/) and [jmetermaster](https://hub.docker.com/r/wankutuzi/jmetermaster/) are built base on [jmeter3.0base](https://hub.docker.com/r/wankutuzi/jmeter3.0base/)
- [PTC](https://hub.docker.com/r/wankutuzi/ptc/) is built base on jmetermaster
- Feel free to edit the [Dockerfile](docker file/JMeter Base/Dockerfile) and build your own docker image with your selected version of Java/JMeter/NodeJS etc.

### Installing

A step by step series of examples that tell you have to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

## Running the tests

Explain how to run the automated tests for this system

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

## Built With

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

## Authors

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone who's code was used
* Inspiration
* etc
