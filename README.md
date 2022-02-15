# CT : CLI Helper tool

This tool is a simple wrapper allowing to :

- have aliases per project, aliases that can be called from whenever the project structure.
- spawn a web GUI to get listening ports on your machine (http://localhost:1500)

# Setup

If you want to use the port list feature, you will also need :

- lsof
- curl
- awk
- netcat (nc)

## Manual install

Get the current version of `ct` on the **releases** page. Then extract it with : `tar xzf FILENAME` and put it in your path (typical location is ~/bin or /usr/local/bin).

## installation

You can install the script by running the following commands in your shell (adapting the CT_TARGET value to a directory in your PATH).

### For GNU/Linux

     CT_TARGET=~/bin;mkdir $CT_TARGET; curl -L https://github.com/code-troopers/ct/releases/download/v0.1.5-pre/ct-v0.1.5-pre-x86_64-unknown-linux-gnu.tar.gz | tar -xzf - -C $CT_TARGET/ && chmod +x $CT_TARGET/ct

### For MacOS

    CT_TARGET=~/bin;mkdir $CT_TARGET; curl -L https://github.com/code-troopers/ct/releases/download/v0.1.5-pre/ct-v0.1.5-pre-x86_64-apple-darwin.tar.gz | tar -xzf - -C $CT_TARGET/ && chmod +x $CT_TARGET/ct

# Port list usage

Simply run the command `ct ports` to get the list of listening ports on your machine at http://localhost:1500.
You will need a working internet connection to retreive the CSS/JS from the CDN to use it.
But you can easily imagine other frontends calling the URI http://localhost:1500/scan which returns JSON.

![Port list example](images/listen.png)

# Aliaser feature usage

## Configure a project

Create a `.ctproject` file at the root of your project structure, this file will contain the aliases you want to set for your current project.
It have to look like the following :

    # comments are ignored
    run='mvn clean install jetty:run'
    dbg='mvnDebug clean install jetty:run'
    test='mvn test'

## Use it

Simply call `ct` followed by your alias to launch the command in your current directory. If you execute the command without specifying a command, help screen with the available commands will be printed.

## Protip

Use consistent aliases in your `.ctproject` files, this way, you can define global aliases for your shell that will allow you to use consistent shortcut regardless of the project type you're on.

For example, you can add an alias `alias run="ct run"` and in each project define such a command. In your shell, a `run` will launch your project, no matter if the underlying task is a Maven or a Grunt one.

## License

    ````````````````````````````````````````````````````````````````````````````````````````````````````
    `````````````````-/ossyyyyyyyso+:.``````````````````````````````````````````````````````````````````
    ``````````````-sddddddddddddddddddh+.```````````````````````````````````````````````````````````````
    ````````````.sdddo///////////////yddd+``````````````````````````````````````````````````````````````
    ```````````.hdddd-               +ddddo```````````````     Code-Troopers CLI helper    `````````````
    ```````````sdds..                `..ddd/``````````````         Copyright  2014         `````````````
    ``````````:dhho                     yhdh.`````````````          Code-Troopers          `````````````
    ``````````yd                          :d+`````````````     http://code-troopers.com    `````````````
    `````````:dd  -yhyyyyyyh` -yyyyyyyyy  :dd.``````````````````````````````````````````````````````````
    `````````ydd  -dddddy///  .///dddddd  :dd+``````````````````````````````````````````````````````````
    ````````-ddd  -dddddo         dddddd  :ddh``````````````````````````````````````````````````````````
    ````````/ddd  `.....`         ......  :ddd.`````````````````````````````````````````````````````````
    ````````ohhy                          :hhh:`````````````````````````````````````````````````````````
    ```````+o                                 h:````````````````````````````````````````````````````````
    `````.ydo               yh+               hd+```````````````````````````````````````````````````````
    `````sddo      `````````yho`````````      hdd/``````````````````````````````````````````````````````
    `````sddo     -ddddddddd` :ddddddddd      hdd/``````````````````````````````````````````````````````
    `````.ydo     `.........  `.........      hd+```````````````````````````````````````````````````````
    ```````/o...                          `...s-````````````````````````````````````````````````````````
    ````````.ydd                          :ddo``````````````````````````````````````````````````````````
    `````````-dd            sy+           :dh```````````````````````````````````````````````````````````
    ``````````/d````````````dds```````````/h-```````````````````````````````````````````````````````````
    ```````````.ohdddddddddddddddddddddddy+.````````````````````````````````````````````````````````````
    ``````````````.://++//:-``.-://++//-.```````````````````````````````````````````````````````````````
    ````````````````````````````````````````````````````````````````````````````````````````````````````

Copyright 2014 Code-Troopers.

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this work except in compliance with the License. You may obtain a copy of the License in the LICENSE file, or at:

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
