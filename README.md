# Monkey2 HTML WebSockets 🐵

This is the primary repository for HTML WebSocket compatibility in Monkey2. This grants you the ability to be able 
to communicate with a properly setup WebSocket server from a Monkey2 application. Currently, this module only supports
the Emscripten export and has only been tested with WASM selection. 

_video:_
[ ![WebSockets demo](https://cf-b2.streamablevideo.com/image/mpgf5.jpg?token=1514516418-lWnY%2FakjVLVdmNWu%2BvmC6sIyAwFm8QNXXbPcuBoKf%2FQ%3D.png) ](https://streamable.com/s/mpgf5/evnwka)
## Getting Started

- download this repository as a zip
- Move the zip into your monkey2 modules folder and unzip into its appropriate folder
- inside Ted2Go right click the folder and build this module for emscripten

#### [Join the converstation!](http://monkeycoder.co.nz/forums/topic/introducing-html-websockets-for-mx2/)

## Deployment
See [the demo for a quick usage test](bananas/websock_demo/websock_demo.monkey2)

1. Chose emscripten wasm for export 
2. After it has been built run a simple web server of your choice in the directory 
3. You can find a simple server to use [here](http://monkeycoder.co.nz/monkey2-files/). Just click on MServer
4. Open up your browser and navigate your browser to a localhost, I usually use localhost:8080

### Sample code
**Including sockets and extending the class**
```monkey2
#Import "<html-ws>"   ': HTML WebSockets now available
Using html.ws..       ': Access elements in global scope 

Class DemoSock Extends WebSocket
	Method New()
		Super.New("ws://echo.websocket.org/") ' we provide the WS url, we can also add some WS protocols later if we want
	End
```

**Message retrieval hooks**
```monkey2
Method OnData(data:String) Override ' this method passes us information recieved from the server
  AddMessage( "Recieved: " + data )
End

Method OnOpen() Override ' After we've established a connection we can do some setup
  AddMessage("Socket established connected!")
End

Method OnClose() Override ' We can start closing things up or reacting to a disconnection here
  AddMessage("Socket terminated!")
End
```


## Contributing

Nothing decided for now as far as a standard. I'm learning a style of my own as I go. 
Please do fork, please do comment, please do add tickets, please do offer suggestions. Everything's welcomed!

## Authors

* **Abe Noll** - *Initial work* - [Forgotten King](https://github.com/forgotten-king)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
