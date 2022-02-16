A look at common errors with running the app locally and how to fix them. If even are going through these steps you are unable to run the app, let us know over [Slack](https://teambookproject.slack.com/ssb/redirect) or by creating a new [Q&A GitHub discussion](https://github.com/Project-Books/book-project/discussions/categories/q-a).

## Cannot find log statements or the entities do not have constructors (Lombok errors)

You may find lots of errors for things like the log statements, or the entities not having constructors. Below, you can find instructions on how to fix this for IntelliJ and Eclipse.

### IntelliJ
    
  <p align="center">
    <img src="../../assets/intellij_annotation_processing.png" alt="Enable IntelliJ annotation processing"/>
  </p>
    
To remove the errors in IntelliJ, install the [Lombok plugin](https://plugins.jetbrains.com/plugin/6317-lombok) and enable annotation 
processing. This can be done either in the popup window that appears after installing the Lombok plugin or by checking the
'Enable annotation processing' checkbox in Settings > Build, Execution, Deployment > Compiler > Annotation Processors.

Note that in IntelliJ Ultimate 2021.1, Lombok comes pre-bundled so you don't need to install the plugin.

### Eclipse

In Eclipse, you will need to run Maven install before running the project (right click anywhere in the pom.xml and select Run as > Maven install).

## Flyway

### FlywayException: Validate failed

```
Caused by: org.flywaydb.core.api.FlywayException: Validate failed: 
Migration checksum mismatch for migration version
```

If you see the error above, then you need to run flyway clean:

- In IntelliJ, go to Maven > Plugins > flyway > flyway:clean

![image](https://user-images.githubusercontent.com/11173328/90000852-96affb80-dc88-11ea-9b4f-a79cf02811f0.png)

- Alternatively, run `./mvnw flyway:clean` (Unix) or `mvnw.cmd flyway:clean` (Windows) at the root of the project (or in the backend/ directory if it's 0.2.0)

## Docker

!!! note

    We are now using PostgreSQL instead of MySQL, but the fixes below may still apply

### SQL communications link failure

```
    SQL State : 08S01
    Error Code : 0
    Message : Communications link failure

    The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
```

If you see the SQL error above, please ensure that you have successfully ran the database before running the app (see ). For this, you will need to run Docker (better) or your own MySQL server locally (see the [instructions in the README](https://github.com/knjk04/book-project#setup)).

### Bind for 0.0.0.0:3306 failed: port is already allocated

If after running `docker-compose up` at the root of the project you get an error similar to the following:

```
C:\Users\karan\git\book-project>docker-compose up
Removing book-project_db_1
Recreating db425df37b9d_book-project_db_1 ...
Recreating db425df37b9d_book-project_db_1 ... error

ERROR: for db425df37b9d_book-project_db_1  Cannot start service db: Ports are not available: listen tcp 0.0.0.0:3306: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.

ERROR: for db  Cannot start service db: Ports are not available: listen tcp 0.0.0.0:3306: bind: Only one usage of each socket address (protocol/network address/port) is normally permitted.
ERROR: Encountered errors while bringing up the project.
```

then another service is using port 3306. 

If you see the `Found orphan containers` warning, then run `docker-compose up --remove-orphans`. Then, continue with the following steps.

**Check if a running container is using the port:**

![image](https://user-images.githubusercontent.com/11173328/152675157-b73ea24a-2c1f-43ba-bce4-ce1fe961d16b.png)

After running `docker container ls`, check to see if port 3306 is being used. If so, run `docker container rm -f` to stop and remove the container. In the above example, you would run `docker container rm -f 816`.

If this doesn't work, you can see some more troubleshooting tips below.

**A different service is running**

On Windows:
   - Open cmd with administrator privileges
   - Run `netstat -ano`
   - Use `ctrl + f` to find the process that is running on port `3306`. Make a note of the PID number (right-hand column)
   - Run `taskkill /PID <PID> /F`. For example, if the PID you noted above was `4504`, you would type in `taskkill /PID 4504 /F`

## Building the backend

If you're having issues with building the app, try deleting Maven's `.m2` folder. This can usually be found in `/home/<username>/.m2`

## Running the backend

### Failed to determine a suitable driver class

![image](https://user-images.githubusercontent.com/11173328/96374517-28e1ed80-116b-11eb-832f-ceb79cd98943.png)

If you're running the app from within your IDE and you get the 'Failed to determine a suitable driver class', ensure that you have passed in the profile you want to run (e.g. dev) into the VM options of your IDE. The screenshot above shows how to set the dev profile in IntelliJ.

### Application failed to start

This error occurs when another process (e.g. another Spring Boot application) is using port 8080.

```
***************************
APPLICATION FAILED TO START
***************************

Description:

Web server failed to start. Port 1234 was already in use.

Action:

Identify and stop the process that's listening on port 1234 or configure this application to listen on another port.
```

If you see an 'Application failed to start' error like the above, you can either try to kill the process that is using that port or, as a temporary measure, change the server port in `resources/application.properties` by adding the following line:

```
server.port=1234
```

You can choose whatever free port you want. If you follow this approach, please ensure you revert the change before committing.
