# Xdebug3 on Docker with vscode launch.json example

this setup allows you to debug PHP inside Docker via ***xdebug3***. tested with VS Code.

## Usage

The Xdebug3 config happens in the php.ini. these directives are updated for xdebug3.

 A sample `docker-compose.yml` comes along with it so you can get this up and running in one command: `docker-compose up --build -d`.

## VS Code configuration

use this extension [felixfbecker.php-debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug).

You can create a debug configuration by going to `Debug > Add Configuration... > PHP`, 
The setting file for vscode is included: `.vscode/launch.json`.
you can configure with port and adapting your directory structure in container mapping like that:
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9007,                               // port where you use for vscode
            "pathMappings": {
                "/var/www/html/": "${workspaceFolder}"  // directories in container : source code directory on docker host
            },
            :
```

port settings reveals too on php.ini
```
xdebug.client_port = 9007                               # port number which you set in launch.json
```

Add a breakpoint, and click on "Listen for XDebug" (you can change the name in .vscode/launch.json) in the top left hand corner. Load your page, and you should get debugging information:

![](https://i.imgur.com/B8dnAj7.png)


## this repositories started with forking angristan/php-xdebug-docker