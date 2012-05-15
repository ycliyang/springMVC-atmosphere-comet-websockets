#### About this demo applications:

**Frameworks**
* SpringMVC
* Atmosphere Framework https://github.com/Atmosphere/atmosphere
* Twitter/Spring social https://github.com/SpringSource/spring-social

**Purpose**
*To demo an implementation of Websockets and Comet, when working with an existing SpringMVC web application.*

This project was intended for testing on Tomcat7.0.27 which is the only current version of tomcat supporting websockets.

Configure your HTTP connector in Tomcat's conf/server.xml as such:

```xml
<Connector port="8080" protocol="org.apache.coyote.http11.Http11NioProtocol"
               connectionTimeout="600000"
               redirectPort="8443" />
```

**there is a current bug in the websocket implementation on tomcat. 
The websocket client will lose connection, whenever the connectionTimeout value has been reached for websocket connections.
*So configure your timeout to a really high value.*

**Other Notes**
* **AJP protocol does not support websockets.**
* The Http11NioProtocol does not kill off atmosphere resources when unsubscribe is fired and using a Comet transport
    (long-polling, streaming). This can cause duplicate results when refreshing the page.

