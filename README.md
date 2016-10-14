# red5-web-rtc-demo

Red5 WEB RTC DEMO APPLICATION (CLIENT AND SERVER)



### Introduction

This application sample demosntrates a simple one to one web-rtc audio / video chat, while using Red5 as its signaling backbone. While  red5 has always been the champion of open source streaming, the inclusion of websockets makes it an efficient open source candidate for realtime communication in the modern web structure.

In this example app we see how Red5 websocket helps in managing sinple chat rooms that host and mediate web-rtc sessions between html/js clients.


### Server side application (web-rtc-demo)

The red5 web-rtc-demo application is a websocket host, which allws you to connect to it via standard HTML5 websocket connections. The application lsitens on the default red5 websocket port **8081**, so your server needs to allow access to this port if its being accessed from outside. This means that the localhost and port must be configured in the red5/conf/jee-container.xml file.

```
<bean id="webSocketTransport" class="org.red5.net.websocket.WebSocketTransport">
    <property name="addresses">
        <list>
            <value>localhost:8081</value>
        </list>
    </property>
</bean>

```

>> This is not required if you are testing thinsg locally.


BUILDING THE APP


You can build the application usign maven.

```
mvn package
```

Deploy your application by copying the war file into your red5/webapps directory.

After deploy is complete, restart red5 and go to http://localhost:5080/web-rtc-demo/user=<username> in your browser 


>> The application accepts connections with a username and a room parameter which are supplied via query string of the WebSocket url. User name must be unique for each connection.




### Client side application (index.html)


The client side application is a simple WebRTC sample built using javascript and WebRTC api. No third party libraries are used other than Jquery. The client application connects to Red5 server app over websocket for signaling, through the page : http://localhost:5080/web-rtc-demo/user=<username>

`username` parameter is mandatory and must be unique when you testing this in two different browser windows. The application code default to a room name `shared`. This can be edit in the index.html file.


```
var room = "shared";
```



