The `catalina` script in Apache Tomcat (found in the `bin/` directory) is used to manage the Tomcat server from the command line. It provides several **command options** to control the server lifecycle.

### ✅ Common `catalina` Command Types

Here are the main command types you can use:

| Command       | Description                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `start`       | Starts the Tomcat server in the background                                  |
| `stop`        | Stops the running Tomcat server                                              |
| `run`         | Starts Tomcat and runs it in the **foreground** (logs visible in terminal)  |
| `debug`       | Starts Tomcat in debug mode                                                 |
| `version`     | Displays the Tomcat version information                                     |
| `configtest`  | Tests the validity of the `server.xml` configuration                        |
| `jpda start`  | Starts Tomcat with **JPDA debugging enabled** (used for remote debugging)   |
| `jpda run`    | Like `run`, but with JPDA enabled                                           |

### 🔧 Usage Example (Linux/macOS):
```bash
cd /path/to/tomcat/bin
./catalina.sh start        # Start server
./catalina.sh stop         # Stop server
./catalina.sh run          # Run in foreground
./catalina.sh configtest   # Validate config
./catalina.sh jpda start   # Start with remote debugging
```

### 🪟 On Windows:
Use `catalina.bat` instead:
```cmd
catalina.bat start
```
