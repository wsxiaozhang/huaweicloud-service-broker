# Huawei Cloud Service Broker
[![Go Report Card](https://goreportcard.com/badge/github.com/huaweicloud/huaweicloud-service-broker?branch=master)](https://goreportcard.com/badge/github.com/huaweicloud/huaweicloud-service-broker)
[![Build Status](https://travis-ci.org/huaweicloud/huaweicloud-service-broker.svg?branch=master)](https://travis-ci.org/huaweicloud/huaweicloud-service-broker)
[![LICENSE](https://img.shields.io/badge/license-Apache%202-blue.svg)](https://github.com/huaweicloud/huaweicloud-service-broker/blob/master/LICENSE)

This is a [Cloud Foundry Service Broker](https://docs.cloudfoundry.org/services/overview.html) for Huawei Cloud.
Currently it includes the following services support:
* [Distributed Cache Service (DCS)](http://www.huaweicloud.com/en-us/product/dcs.html) 
* [Distributed Message Service (DMS)](http://www.huaweicloud.com/en-us/product/dms.html) 
* [Object Storage Service (OBS)](http://www.huaweicloud.com/en-us/product/obs.html) 
* [Relational Database Service (RDS)](http://www.huaweicloud.com/en-us/product/rds.html) 

## Installation

### Locally

Using the standard `go install` (you must have [Go](https://golang.org/) already installed in your local machine):

```
$ go install github.com/huaweicloud/huaweicloud-service-broker
$ huaweicloud-service-broker -port=3000 -config=<path-to-your-config-file>
```

### Cloud Foundry

The broker can be deployed to an already existing [Cloud Foundry](https://www.cloudfoundry.org/) installation:

```
$ git clone https://github.com/huaweicloud/huaweicloud-service-broker.git
$ cd huaweicloud-service-broker
```

Modify the [configuration file](https://github.com/huaweicloud/huaweicloud-service-broker/blob/master/config.json) to include your RDS authentication configurations and some parameters or configurations for providing the DB Instances in the [sample configuration file](https://github.com/huaweicloud/huaweicloud-service-broker/blob/master/config.json). Then you can push the broker to your [Cloud Foundry](https://www.cloudfoundry.org/) environment:

```
$ cf push huaweicloud-service-broker
```

## Usage

### Managing Service Broker

Configure and deploy the broker. Then:

1. Check that your Cloud Foundry installation supports [Service Broker API](https://docs.cloudfoundry.org/services/api.html)
2. [Register the broker](https://docs.cloudfoundry.org/services/managing-service-brokers.html#register-broker) within your Cloud Foundry installation;
3. [Make Services and Plans public](https://docs.cloudfoundry.org/services/access-control.html#enable-access);
4. Depending on your Cloud Foundry settings, you might also need to create/bind an [Application Security Group](https://docs.cloudfoundry.org/adminguide/app-sec-groups.html) to allow access to the RDS DB Instances.

### Integrating Service Instances with Applications

Application Developers can start to consume the services using the standard [CF CLI commands](https://docs.cloudfoundry.org/devguide/services/managing-services.html).

Depending on the [broker configuration](https://github.com/huaweicloud/huaweicloud-service-broker/blob/master/CONFIGURATION.md#rds-broker-configuration), Application Developers can use the Credentials information from the
response of broker Bind call for accessing DB Instances from RDS.


## Contributing

In the spirit of [free software](http://www.fsf.org/licensing/essays/free-sw.html), **everyone** is encouraged to help improve this project.

Here are some ways *you* can contribute:

* by using prerelease versions or master branch.
* by reporting bugs
* by suggesting new features
* by writing or editing documentation
* by writing specifications
* by writing code (**no patch is too small**: fix typos, add comments, clean up inconsistent whitespace)
* by refactoring code
* by closing [issues](https://github.com/huaweicloud/huaweicloud-service-broker/issues)
* by reviewing patches

### Submitting an Issue

We use the [GitHub issue tracker](https://github.com/huaweicloud/huaweicloud-service-broker/issues) to track bugs and features. Before submitting a bug report or feature request, check to make sure it hasn't already been submitted. You can indicate support for an existing issue by voting it up. When submitting a bug report, please include a [Gist](http://gist.github.com/) that includes a stack trace and any details that may be necessary to reproduce the bug, including your Golang version and operating system. Ideally, a bug report should include a pull request with failing specs.

### Submitting a Pull Request

1. Fork the project.
2. Create a topic branch.
3. Implement your feature or bug fix.
4. Commit and push your changes.
5. Submit a pull request.

## License

huaweicloud-service-broker is under the Apache 2.0 license. See the [LICENSE](LICENSE) file for details.
