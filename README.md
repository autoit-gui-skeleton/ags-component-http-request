AGS-component-http-request
==========================

> AGS components are a set of AutoIt libraries, that you can use in your AutoIt project built with the [AGS framework](https://v20100v.github.io/autoit-gui-skeleton/). AGS-component-http-request is a library used to send HTTP request in POST or GET method in an AutoIt project build with AGS framework.



<br/>

## Install

We assume that you have already install [Node.js](https://nodejs.org/) and [Yarn](https://yarnpkg.com/lang/en/), for example with [Chocolatey](https://chocolatey.org/). We recommend you to install it with Yarn. To do this, just type in the root folder of your project where the `package.json` is saved :

```
λ  yarn add @autoit-gui-skeleton/ags-component-http-request --modules-folder web/vendor
```

This package is installed into the `./vendor` directory. To use it in your AutoIt program, you need to include this library with this instruction:

```autoit
#include 'vendor/@autoit-gui-skeleton/ags-component-http-request/ags-component-http-request.au3'
```



<br/>

## AGS's vendor directory

By default Yarn and npm installs packages into the `./node_modules` directory. With an AGS project we want to install this kind of dependency package into the `./vendor/` directory, in order to avoid any confusion with a Node.js project. To do this we add the option `--modules-folder vendor`. 

You can omit this option normaly with an AGS project. Indeed, you are supposed to have the file `./.yarnrc` in the root folder of your AGS project, in the same place of your `pacakge.json` file. Yarn automatically looks into the `./.yarnrc` file for additional configuration options.

```
#./.yarnrc 
--modules-folder vendor
```

With this file, you can run `yarn add @autoit-gui-skeleton/ags-wrapper-json` to install it directly into the appropriate `./vendor` directory.



<br/> 

## Description

### Methods

This library provides few method to handle HTTP request.

 Methods    | Description 
---------------|-------------
`HttpGET($url, $data = "", $proxy = "")` | Send HTTP request with GET method.
`HttpPOST($url, $data = "", $proxy = "")` | Send HTTP request with POST method.
`URLEncode($urlText)` | URL encoding replaces unsafe ASCII characters.  
`URLDecode($urlText)` | Inverse operation of URLEncode.
`WinHttp_SetProxy_from_configuration_file($oHttp)` | Set timeouts by parsing the configuration file AGS project store in './config/parameters.ini'.
`WinHttp_SetProxy_from_configuration_file($oHttp)` | Set proxy by parsing the configuration file AGS project store in './config/parameters.ini'.


### Usages

#### Make a simple HTTP request in GET

```autoit
Local $response = HttpGET("https://soundcloud.com/2080/my-megadrive")
    
ConsoleWrite($response.Status & @CRLF)
ConsoleWrite($response.ResponseText)
```

#### Make a request with a given proxy

By default this component search in the configuration file `./config/parameters.ini` if a proxy is defined in the `PROXY` variable of the section `AGS_HTTP_REQUEST`. But you can also provide a proxy directly in the method.

```autoit
Local $response = HttpGET( _ 
    "https://soundcloud.com/2080/my-megadrive", _ 
    default, _ 
    "http://myproxy.com:20100")
    
ConsoleWrite($response.Status & @CRLF)
ConsoleWrite($response.ResponseText)
```


### Dependencies
   
 > Specifiy if this AGS component have dependencies with an third-party library AutoIt or with an anoter AGS component.
 
 AGS-component-http-request use Winhttprequest.5.1 object. It has no dependence with another AutoIt library or AGS component.
   


<br/>
 
## About
 
### Release history
 
 - ags-component-http-request v1.0.0-alpha - *2018.07.09*
 
### Contributing
 
Comments, pull-request & stars are always welcome !
 
### License
 
Copyright (c) 2018 by [v20100v](https://github.com/v20100v). Released under the MIT license.