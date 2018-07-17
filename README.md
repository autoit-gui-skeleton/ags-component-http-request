AGS-component-http-request
==========================

> In order to send HTTP request, [AGS framework](https://autoit-gui-skeleton.github.io/) provides this component [@autoit-gui-skeleton/ags-component-http-request](https://www.npmjs.com/package/@autoit-gui-skeleton/ags-component-http-request). This library is used to send HTTP request in GET or POST method, and with or wihtout behind a corporate proxy.



<br/>

## How to install AGS-component-http-request ?

In order to simplify the management of the dependencies of an AutoIt project built with AGS framework, we have diverted form its initial use the dependency manager npm, and its evolution Yarn. This allows us to manage the dependencies of an AGS project with other AutoIt libraries, and to share these AutoIt packages from the npmjs.org repository. All AGS packages hosted in this npmjs repository belong to [@autoit-gui-skeleton organization](https://www.npmjs.com/org/autoit-gui-skeleton)

We assume that you have already install [Node.js](https://nodejs.org/) and [Yarn](https://yarnpkg.com/lang/en/), for example with [Chocolatey](https://chocolatey.org/), so to install AGS-component-http-request, just type in the root folder of your project where the `package.json` is saved :

```
λ  yarn add @autoit-gui-skeleton/ags-component-http-request --modules-folder web/vendor
```

This package is installed into the `./vendor` directory. To use it in your AutoIt program, you need to include this library with this instruction:

```autoit
#include 'vendor/@autoit-gui-skeleton/ags-component-http-request/ags-component-http-request.au3'
```


<br/>

## AGS's vendor directory

To install AutoIt dependencies in the `./vendor` directory, and not in the default directory of Node.js `./node_modules`, you must add the `--modules-folder vendor` option. We force this choice to avoid any confusion with a Node.js project. 

Note that with an AGS project, it is not necessary to explicitly write this option on the command line, thanks to the `.yarnrc` file stored at the root of the project. Yarn automatically use this file to add an additional configuration of options.

```
 #./.yarnrc 
 --modules-folder vendor
 ```
 
So with this file you can run `yarn add @autoit-gui-skeleton/ags-wrapper-json` to install the dependencies directly into the appropriate `./vendor` directory.


<br/> 

## AGS-component-http-request

### Available methods

This library provides few method to handle HTTP request.

 Methods    | Description 
---------------|-------------
`HttpGET($url, $data = "", $proxy = "")` | Send HTTP request with GET method.
`HttpPOST($url, $data = "", $proxy = "")` | Send HTTP request with POST method.
`URLEncode($urlText)` | URL encoding replaces unsafe ASCII characters.  
`URLDecode($urlText)` | Inverse operation of URLEncode.
`WinHttp_SetProxy_from_configuration_file($oHttp)` | Set timeouts by parsing the configuration file AGS project store in './config/parameters.ini'.
`WinHttp_SetProxy_from_configuration_file($oHttp)` | Set proxy by parsing the configuration file AGS project store in './config/parameters.ini'.


### Configuration

To configure the behaviour of this component, you can define its option into the file `./config/parameters.ini`. You can set a proxy for HTTP connexion, and severals time-out related to request and response. By default this component search into the configuration file if a proxy is defined in the `PROXY` variable of the section `AGS_HTTP_REQUEST`.

```ini
## ./config/parameters.ini ##

[AGS_HTTP_REQUEST]
; [OPTIONAL] Use a proxy for http connexion. Keep empty to disable it.
PROXY=http:/myproxy.com:20100

; [OPTIONAL] Time-out value applied when resolving a host name to an @IP,
; in miliseconds.
RESOLVE_TIMEOUT=1000

; [OPTIONAL] Time-out value applied when establishing a communication socket
; with the target server, in milliseconds.
CONNECT_TIMEOUT=1000

; [OPTIONAL] Time-out value applied when sending an individual packet of request
; data on the communication socket to the target server, in milliseconds. A
; large request sent to an HTTP server are normally be broken up into multiple
; packets. The send time-out applies to sending each packet individually.
SEND_TIMEOUT=1000

; [OPTIONAL] Time-out value applied when receiving a packet of response data
; from the target server, in milliseconds. Large responses are be broken up into
; multiple packets; the receive time-out applies to fetching each packet of data
; off the socket.
RECEIVE_TIMEOUT=1000
```


## Usages

### How to send HTTP request by using GET method ?

```autoit
Local $response = HttpGET("https://soundcloud.com/2080/my-megadrive")
    
ConsoleWrite($response.Status & @CRLF)
ConsoleWrite($response.ResponseText)
```


### How to send HTTP request behind a corporate proxy ?

By default this component search in the configuration file `./config/parameters.ini` if a proxy is defined in the `PROXY` variable of the section `AGS_HTTP_REQUEST`. But you can also provide a proxy directly in the method.

```autoit
Local $response = HttpGET( _ 
    "https://soundcloud.com/2080/my-megadrive", _ 
    default, _ 
    "http://myproxy.com:20100")
    
ConsoleWrite($response.Status & @CRLF)
ConsoleWrite($response.ResponseText)
```

### How to URL encode a string ?

URL encoding is a mechanism for encoding information in a Uniform Resource Identifier (URI). It is used in the preparation of data of the application/x-www-form-urlencoded media type, and in the submission of HTML form data in HTTP requests.

If you use HttpGET, you must clean the data to send with URL encoding. 

```autoit
Local $msg = "Welcome in AGS"
Local $url = "https://myServer.org/foo?msg=" & URLEncode($msg) & "&param=32"

ConsoleWrite($url)
; Output >> https://myServer.org/foo?msg=Welcome%20in%20AGS&param=32

ConsoleWrite(URLEncode("123abc!@#$%^&*()_+ ") & @crlf)
; Output >> 123abc!%40%23%24%25%5E%26*()_%2B%20
```


<br/>
 
## About
  
### Contributing
 
Comments, pull-request & stars are always welcome !
 
### License
 
Copyright (c) 2018 by [v20100v](https://github.com/v20100v). Released under the MIT license.