## (nouse)alternatives(temp)(delete)

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
    ```
---