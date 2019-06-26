
Gem's
------
- should give you all the info you need..
	- `gem environment`
- How do I determine the location of my ruby gems?
	- `gem which rails`
- to fetch home dir of your gems..
	- `echo $GEM_HOME`
-----------------------------------

Docker , port, ports. 
-----

* Note: The -p flag can be used multiple times to configure multiple ports.
* Port binding important! , When using dockerfile , build image, give it a name tag, then run, 
but give it a port binding with the local machine(`host`) so that you can ACCESS it

   * wrong usage !:
    
			docker run -it --name abrupt_gap sample_rails_app_docker:latest
            
   * correct : 
   
    		docker run -it -p 3000:3000 --name abrupt_gap sample_rails_app_docker:latest
        
   * `docker run` Usage:	docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
	* `-it`
    	* `-i`,		Keep STDIN open even if not attached
    	*  `-t`,		Allocate a pseudo-TTY
   * `--name`,  string,	Assign a name to the container
   * `-p`,	Publish a container's port(s) to the host
* `docker port` ,You also saw how you can bind a container’s ports to a specific port using the -p flag. Here port 80 of the host is mapped to port 5000 of the container:
	* `docker run -d -p 80:5000 training/webapp python app.py`
    	- `-p 80:5000` first one `80` is belongs to `host`, second one `8000` to `container`...
* debug cli v1 :
	* `docker run -it -p 3000:3000 -p 1234:1234 sample_rails_app_docker:latest`
        

