# Natar installation - version 0.1

## Getting started

In this guide we will be documenting the installation process of each of the 3 core components of **Natar**:

* The **Natar** services which are small independant programs implementing the **Natar** protocol. This is the core of Natar. 
* The **Eye** process manager that helps manage running services, memory and cpu usage of the overall system
* The **Sinatra** web application that provides the end users a visual interface to manage their Natar devices.

## Eye

\*\*\*\*[**Eye**](https://github.com/kostya/eye) is a **Ruby** written process management tool. **Eye** makes it easier to use the **Natar** services and manage their dependencies however it is not a strong dependency which means that **Natar** will still works if you decide not to install and use **Eye**.  
  
**Eye** is distributed as a **Ruby gem** and can be installed with the following command: `gem install eye`.

Once installed you can then clone the utilities repository containing every **Eye** related stuff such as configuration files and more. `git clone --recursive https://forge.pole-aquinetic.net/nectar-platform/utilities`

{% hint style="danger" %}
Be sure to clone the repository using the `--recursive` option to get every submodules associated with this repository. For more informations on submodules check out this [link](https://git-scm.com/book/fr/v2/Utilitaires-Git-Sous-modules).
{% endhint %}

The clone repository should looks like so:

* `dist/` contains all the required files to build distributed packages of the Natar services.
* `natar.eye` is an Eye configuration file containing the definitions of the services and especially how to run them and their runtime dependencies.
* `sources/` contains the source code of every **Natar** services.  Depending on the branch \(dist vs master\) you are on this folder is supposed to contains an executable for every service.
* `processes/`
  * `processes/apps/` contains all the processes that eye should be able to run
  * `processes/redis*` are **Redis** related stuff: configuration and database.
  * `processes/natar-webserver` contains the source code of the **Natar** Sinatra web application. 

You can then load the eye configuration `eye load natar.eye` and start managing **Natar** services from there.

Here is a small list of the mostly used eye commands:

* `eye load $configuration`
* `eye start|stop|restart|info $service_name`
* `eye info|watch`

## Natar

If you chosed to use **Eye**, go into the `sources/` folder and execute the installation scripts to get the **Natar** services repositories.  
However if you did not installed **Eye**, you will need to install the services by hand.  
Here is a non-exhaustive list of available services you might want to install:

* [core](https://forge.pole-aquinetic.net/nectar-platform/natar-core) **\(required\)**
* [apps](https://forge.pole-aquinetic.net/nectar-platform/natar-apps) **\(required\)**
* [redis-image-helper](https://forge.pole-aquinetic.net/nectar-platform/redis-image-helper) **\(required\)**
* [multi-camera-server](https://forge.pole-aquinetic.net/nectar-platform/natar-multi-camera-server) **\(required\)**
* [camera-client](../../natar-services/viewers/camera-client-java.md)
* [detections](https://forge.pole-aquinetic.net/nectar-platform/natar-detections)
* [aruco](https://forge.pole-aquinetic.net/nectar-platform/natar-tracker-aruco)
* [artoolkitplus](https://forge.pole-aquinetic.net/nectar-platform/natar-tracker-artoolkitplus)
* [chilitags](https://forge.pole-aquinetic.net/nectar-platform/natar-tracker-chilitags)
* ...

Once installed you should now be able to run your first service, let us try with the main service: the camera server.  
If you are using **Eye** try running the following command: `eye start camera`.  
If you are not using **Eye** go into the `natar-multi-camera-server/` folder you just downloaded and run the script `run.sh`  
Then run any camera client \(listed [here](../../natar-services/viewers/camera-client-java.md)\) to test if everything is working.

## Sinatra

\*\*\*\*[**Sinatra**](http://sinatrarb.com/) is a DSL for quickly creating web applications in **Ruby**.

If you chose to use **Eye** the web application is already downloaded into the `processes/natar-webserver/` folder.  
Else clone the following repository to get the web application:  
`git clone https://forge.pole-aquinetic.net/nectar-platform/natar-webserver.git` 

Go into the application folder and run `bundler install` . This command will install every gems required by the application as listed in the Gemfile.  
_If you do not have bundler installed run `gem install bundler` and try again._ 

Once the gems are installed you can then run the application `ruby natar.rb` and access it via [http://localhost:4567/](http://localhost:4567/)

{% hint style="danger" %}
The web application heavily depends on **Eye** therefore a lot of functionalities will be missing if you chosed to install it without having it.
{% endhint %}

## Distributed \(Arch linux only\)

You can always install a distributed version \(using distributed packages\) by adding to your **/etc/pacman.conf** the following lines:

```text
[natar]
SigLevel = Optional TrustAll
Server = http://dist.rea.lity.tech/arch/x86_64
```

### Required \(non distributed\) dependencies

* cxxopts
* hiredis

