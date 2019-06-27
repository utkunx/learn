## how to use `ruby`, `gems` ... 

| Table of `ruby` | flag | flag | flag |
| --- | :---: | :---: | :---: |
  **[`ruby gems`](#gems)**  | ? | ? | ?

## ruby on rails, vs-code, docker, debug project

## pre;

|  **[pre settings for debug-ide](#project-requirements)**  | flag | 
| --- | :---: | 
  **[`1. ruby gems`](#1-gems)**  |  **[`2. Gemfile`](#2-gemfile)**  |
  **[`3. vs code launch.json`](#3-vs-code-launchjson-file)**  |  |
  **[`4. Dockerfile`](#4-in-dockerfile)**  |  **[`5.in-entrypoint.sh`](#5-in-entrypointsh)**  |

## post;

|  **[post settings debug-ide](#post-syntax-)** | flag | flag |
| --- | :---: | :---: |
**[first build image](#build)**  |  **[then run it to container](#run)**  | **[start anytime](#start)** |
`docker build`  | `docker run`  | `docker start`  |

---

## ruby

---

### Gem's

* should give you all the info you need..

        gem environment

* How do I determine the location of my ruby gems?

        gem which rails

* to fetch home dir of your gems..

        echo $GEM_HOME

---

### ruby on rails, vs-code, docker, debug

21 jun 2019

### Project requirements

---

#### 1. gems

* `ruby-debug-ide`
* `debase`

#### 2. `Gemfile`

```Gemfile
        group :development, :test do
        gem 'debase'
        gem 'ruby-debug-ide'
        end
```

#### 3. vs-code `launch.json` file

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
   ```

   ```json
            "cwd": "${workspaceRoot}" // important, your work space root must be
   ```

#### 4. in `Dockerfile`

   ```Dockerfile
            EXPOSE 1234 3000
            // 1234 port used for debug
   ```

#### 5. in `entrypoint.sh`

   ```sh
        #!/bin/bash
        set -e
        rm -f /sample_rails_application/tmp/pids/server.pid
        rdebug-ide --host 0.0.0.0 --port 1234 -- bin/rails server
        exec "$@"
   ```

---

### post syntax ;

### build

* step for using `Dockerfile` ;
* build, you build [image] from the `Dockerfile` ;

          docker build -t sample_rails_app_docker:latest .

### run

* run, you make a [container] from this image and give it a essantials of; `name tag`, `ports using`, with command `run`

        docker run -it -p 3000:3000 -p 1234:1234 --name XXY sample_rails_app_docker:latest

  * important config that you assign to the container are;
    * port, first one belongs to `host` second  one to `container`

                -p 3000:3000
                -p 1234:1234

    * name, give it name so you can easyly start it, 

                  --name XXY

### start

* start, after these steps, no need to use run, you can you it `start`

            docker start XXY

---