# Visual code launch settings

* Visual code settings to connect remote debugger ;
* all under settings belongs to `launch.jsom`  on `vs-code`

* [these example settings are imported from vscode-recipes](https://github.com/microsoft/vscode-recipes/tree/master/debugging-Ruby-on-Rails)

## Bonus

1. If you are using `Docker` to run your application, you need to append the below configuration in `lanunch.json#configutations` to debug it. 

    ```json
    {
        "name": "Attach to Docker",
        "type": "Ruby",
        "request": "attach",
        "remotePort": "1234",
        "remoteHost": "0.0.0.0",
        "remoteWorkspaceRoot": "/",
        "cwd": "${workspaceRoot}",
        "showDebuggerOutput": true
    },
    ```

2. So, you need to start rails server from the docker in debug mode as like below in the configuration

    ```yml
    # based on the 'compose' version you could change your config, but the 'command' and 'ports' should be same as like below. (You can change the ports 3000, 1234 but you want to update the same in launch.json too.)
    version: "3"
    services:
        web:
            build:
                context: .
            command: bundle exec rdebug-ide --debug --host 0.0.0.0 --port 1234 -- rails s -p 3000 -b 0.0.0.0
            volumes:
                - .:/app
            ports:
                - "1234:1234"
                - "3000:3000"
                - "26162:26162"
    ```

3. If you are running multiple docker rails applications at a same time, you want make sure your ports should be uniq. (26162 is a dispatcher-port).

    ```yml
    command: bundle exec rdebug-ide --debug --host 0.0.0.0 --port 1235 --dispatcher-port 26163 -- rails s -p 4000 -b 0.0.0.0
    ports:
        - "1235:1235"
        - "4000:4000"
        - "26163:26163"
    ```

4. `EXPOSE` all the ports in your `Dockerfile`

5. Start the docker by running command `docker-compose up`

6. Select the **'Attach to Docker'** configuration in VS Code, then press F5 or click the green play button.

7. If you want to debug your code, set a breakpoint in any `*.rb` file otherwise leave it.

8. VS Code should now show the rails server logs. (Use [Docker](https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker) extension).

9. Party 🎉🔥 
