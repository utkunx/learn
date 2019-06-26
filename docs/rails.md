21 jun 2019 
---


#### ruby on rails, vs-code, docker, debug.

* Project requirements ;
	* gems used for debuging needed on `Gemfile`; `ruby-debug-ide` , `debase`.
    
        ```Gemfile
		group :development, :test do
  		gem 'debase'
 		gem 'ruby-debug-ide'
		end
        ```
            
* vs-code settings ; 
	* `launch.jsom`  on `vs-code`
    
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
        
* docker settings ; 
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
