AGS-component-http-request
==========================

> AGS components are a set of AutoIt libraries, that you can use in your AutoIt project build with the [AGS framework](https://v20100v.github.io/autoit-gui-skeleton/). AGS-component-http-request is a library used to send HTTP request in POST or GET method in an AutoIt project build with AGS framework.


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
 

<br/>

## Configure and install it

### Requirements 

To install this AGS component, we use [Yarn](https://yarnpkg.com/en/docs/install#windows-stable) as a package manager for AutoIt code of AGS framework. We divert the orignal use of Yarn, a tool in Node.js ecosystm use to handle Javascript module. We assume that you already install `Node.js` and `Yarn`, and if it's not the case, we suggest you to take a [chocolatey](https://chocolatey.org/), in ordre to install them. Chocolatey is THE package manager for Windows. It easily manage all aspects of Windows software (installation, configuration, upgrade, and uninstallation). 

In order to install `Node.js` and `Yarn` just run your prefered windows command ; cmd, cmder or powershell ; as an administrator and type:

```bash
λ choco install nodejs
λ choco install yarn
```

### Install

To install `AGS-component-http-request`, just type this instruction in the root folder of your project ; i.e. where the `package.json` of your project is store

```
λ  yarn add @autoit-gui-skeleton/ags-component-http-request --modules-folder web/vendor
```

By default yarn or npm installs packages into the `node_modules` directory in the root of the project. With an AGS project, we want to install packages into `./vendor/` directory. To do this we add the option `--modules-folder vendor`. Normaly, you are supposed to have the file `./.yarnrc` in the root folder of your project, in the same directory as your `package.json` file. Yarn automatically looks in this file for additional configuration options. We add into it, this configuration :
 
```
# ./.yarnrc
--modules-folder vendor
```
 
Now just run `yarn add @autoit-gui-skeleton/ags-component-http-request` to install it into `./vendor` directory.


### Configure in AGS project

In the main entry program of your project, you need to include this library.

```autoit
#include 'vendor/@autoit-gui-skeleton/ags-component-http-request/ags-component-http-request.au3'
```

    
<br/>
 
## Dependencies
  
> Specifiy if this AGS component have dependencies with an third-party library AutoIt or with an anoter AGS component. 
  
 - AutoIt library dependencies : none.
 - AGS-components dependencies : none.
  
 
<br/>
 
## About
 
### Release history
 
 - ags-component-http-request v1.0.0-alpha - *2018.07.09*
 
### Contributing
 
Comments, pull-request & stars are always welcome !
 
### License
 
Copyright (c) 2018 by [v20100v](https://github.com/v20100v). Released under the MIT license.