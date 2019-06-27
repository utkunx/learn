# docker commands v2

| Table of docker | flag | flag | flag |
| --- | :---: | :---: | :---: |
**[`docker images`](#docker-images)**  | ? | ? | ?
**[`docker pull`](#docker-pull)**  | ? | ? | ?
**[`docker run`](#docker-run)**  | **[`-it`](#-it)**  | **[`-p`](#-p)**  | **[`--name`](#--name)**  
**[`docker build`](#docker-build)**  | ? | ? | ?
**[`docker ps`](#docker-ps)**  | ? | ? | ?
**[`docker build`](#docker-build)**  | ? | ? | ?
**[`vscode-ide-rmt`](sample-settings-for-vscode-v2/rails-vscode-v2.md#Bonus)**  | ? | ? | ?
**[`extarnal links`](#extarnal-links)**  | ? | ? | ?

----

| Table of ruby | flag | flag | flag |
| --- | :---: | :---: | :---: |
  **[`ruby gems`](#gems)**  | ? | ? | ?

----

| Table of working config | flag | flag | flag |
| --- | :---: | :---: | :---: |
  **[`ruby gems`](#gems)**  | ? | ? | ?

----

## `docker images`

* `docker images` command to see a list of all images on your system.

* An important distinction with regard to images is between `base images` and `child images`.
    * `Base images` are images that have no parent images, usually images with an `OS` like `ubuntu`, `alpine` or `debian`.
    * `Child images` are images that `build` on `base images` and add additional functionality.

----

## `docker pull`

* `docker pull alpine` command fetches image and saves it in our system.

----

## `docker run`

* `docker run alpine ls -l`
  * When you call `run`,
    * `docker pull` > create the `container` > `docker run`

* `docker run alpine /bin/sh`
  * These `interactive shells` will exit after running any scripted commands,
* `docker run -it alpine /bin/sh`
  * unless they are run in an `interactive terminal`

### `-it`

----

* `-it` means `interactive terminal`
  * `-i`, `--interactive`; Keep STDIN open even if not attached
  * `-t`, `--tty`; Allocate a pseudo-TTY

* other commands, `ls -l`, `uname -a`

----

### `-p`

* port(s) binding,
  * `-p 3000:3001`
    * first one `3000` belongs to `host`
    * second  one `3001` to `container`

            for single port     -p 3000:3001 
            or
            for multi ports     -p 3000:3000 -p 1234:1234

* Port binding important! , When using dockerfile , build image, give it a name tag, then run, 
but give it a port binding with the local machine(`host`) so that you can ACCESS it

----

### `--name`

* name, give it name so you can easyly start it,

             --name XXY

----

## `docker build`

1. `build`, you build [image] from the `Dockerfile` ;

            docker build -t sample_rails_app_docker:latest .

2. `run`, you make a [container] from this image and give it a essantials of; `name tag`, `ports using`, with command `run`

            docker run -it -p 3000:3000 -p 1234:1234 --name XXY sample_rails_app_docker:latest

3. `start`, after these steps, no need to use `run`, you can you it `start`

            docker start XXY

----

## `docker ps`

* `docker ps` command shows you all `containers` that are currently running.
* `docker ps -a` command shows a list of all `containers` that you ran.

----

## extarnal links

* [docker-baby-steps](https://github.com/docker/labs/blob/master/beginner/chapters/webapps.md)

----

## ruby

----

### Gem's

----

* should give you all the info you need..

        gem environment

* How do I determine the location of my ruby gems?

        gem which rails

* to fetch home dir of your gems..

        echo $GEM_HOME

----

## ruby on rails, vs-code, docker, debug

21 jun 2019

### Project requirements

#### Gems

* `ruby-debug-ide`
* `debase`

#### `Gemfile`

        ```Gemfile
        group :development, :test do
        gem 'debase'
        gem 'ruby-debug-ide'
        end
        ```

#### vs-code `launch.json` file

        ```json
          {
            "name": "Attach to Docker1",
            "type": "Ruby",
            "request": "attach",
            "remotePort": "1234",
            "remoteHost": "0.0.0.0",
            "remoteWorkspaceRoot": "/",
            "cwd": "${workspaceRoot}", 
            "showDebuggerOutput": true
          },
        ````

        ````
        "cwd": "${workspaceRoot}" // important, your work space root must be
        ````

#### `Dockerfile`

	* `in dockerfile`
    
        ```Dockerfile
        	EXPOSE 1234 3000
        	// 1234 port used for debug
        ```            
    
	* in `entrypoint.sh`
    
        ```sh
		#!/bin/bash
		set -e 
		rm -f /sample_rails_application/tmp/pids/server.pid
		rdebug-ide --host 0.0.0.0 --port 1234 -- bin/rails server
		exec "$@"
        ``` 

* here we go;

* step for using `Dockerfile` ;

	* build 
	* run
    * start
    
	* build, you build [image] from the `Dockerfile` ;

          docker build -t sample_rails_app_docker:latest .
    
	* run, you make a [container] from this image and give it a essantials of; `name tag`, `ports using`, with command `run`
    
   		 	docker run -it -p 3000:3000 -p 1234:1234 --name XXY sample_rails_app_docker:latest
    
    	 * important config that you assign to the container are;
         		* port, first one belongs to `host` second  one to `container`
         
          		-p 3000:3000
         		-p 1234:1234
         
      		* name, give it name so you can easyly start it, 
          
          		  --name XXY
                
                
	* start, after these steps, no need to use run, you can you it `start`
    
    		docker start XXY


## (nouse)alternatives...

* `rdebug-ide --debug --host 0.0.0.0 --port 1234 --dispatcher-port 26162 -- bin/rails server`
 

* `launch.json`

    ```json
          {
        "version": "0.2.0",
        "configurations": [
    {
            "name": "Attach to Docker1",
            "type": "Ruby",
            "request": "attach",
            "remotePort": "1234",
            "remoteHost": "0.0.0.0",
            "remoteWorkspaceRoot": "/",
            "cwd": "${workspaceRoot}",    // working directrory is important....
            "showDebuggerOutput": true
        },
        {
            "name": "Rails server",
             "type": "Ruby",
             "request": "launch",
             "cwd": "${workspaceRoot}",
             "program": "/Users/mitch/.rvm/gems/ruby-2.3.0@gg_portal/bin/rails",
             "args": [
                 "server"
             ],
             "useBundler": true,
            "pathToBundler": "/usr/lib/ruby/gems/2.6.0/gems/bundler-2.0.2/exe/bundle",
            "pathToRDebugIDE": "/usr/lib/ruby/gems/2.6.0/gems/ruby-debug-ide-0.7.0/bin/rdebug-ide",
             "showDebuggerOutput": true
                 }
            ]
          },
        ````
