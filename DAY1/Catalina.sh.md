In Apache Tomcat, **Catalina** is the **servlet container** component responsible for handling servlets and JSP (JavaServer Pages). It is the **core engine** of Tomcat and implements the **Servlet Specification**.

sh catalina.sh start
sh catalina.sh stop

### Key Concepts of Catalina in Tomcat:

* **Catalina** is the heart of Tomcat. When you start Tomcat, it's actually the `org.apache.catalina.startup.Bootstrap` class that bootstraps Catalina.
* It processes **HTTP requests**, executes **Java servlets**, and serves **dynamic content**.
* It handles the **lifecycle** of servlets (init, service, destroy).
* Catalina uses various subcomponents like:

  * `Server`: The top-level element in `server.xml`
  * `Service`: Groups connectors and the container engine
  * `Connector`: Handles client requests (e.g., HTTP/1.1)
  * `Engine`: Processes requests via a pipeline of Valves
  * `Host`: Represents a virtual host (domain)
  * `Context`: A web application

### Example from `conf/server.xml`:

```xml
<Server port="8005" shutdown="SHUTDOWN">
  <Service name="Catalina">
    <Connector port="8080" protocol="HTTP/1.1" />
    <Engine name="Catalina" defaultHost="localhost">
      <Host name="localhost" appBase="webapps">
        <Context path="" docBase="myapp" />
      </Host>
    </Engine>
  </Service>
</Server>
```

Here, `Catalina` is the **engine** name and **service** name, tying together connectors and processing logic.
-----------------------------------------------------------------------------------------------------------------------------------------

The `catalina` script in Apache Tomcat (found in the `bin/` directory) is used to manage the Tomcat server from the command line. It provides several **command options** to control the server lifecycle.

### ✅ Common `catalina` Command Types

Here are the main command types you can use:

| Command      | Description                                                                |
| ------------ | -------------------------------------------------------------------------- |
| `start`      | Starts the Tomcat server in the background                                 |
| `stop`       | Stops the running Tomcat server                                            |
| `run`        | Starts Tomcat and runs it in the **foreground** (logs visible in terminal) |
| `debug`      | Starts Tomcat in debug mode                                                |
| `version`    | Displays the Tomcat version information                                    |
| `configtest` | Tests the validity of the `server.xml` configuration                       |
| `jpda start` | Starts Tomcat with **JPDA debugging enabled** (used for remote debugging)  |
| `jpda run`   | Like `run`, but with JPDA enabled                                          |

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
