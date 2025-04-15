# Setting up MS SQL Server on Docker and IntelliJ

Link:

https://medium.com/@navdeepsinghbedi/setting-up-ms-sql-server-on-docker-and-intellij-2c0a803e41c1



This article demonstrate a straight forward approach to setup Microsoft SQL Server on a Mac system with the use of Docker and further setting the Database in IntelliJ IDE.

# Install Docker :

Docker containers wrap up software and its dependencies into a standardised unit for software development that includes everything it needs to run: code, runtime, system tools and libraries. Download Docker from [**https://www.docker.com/get-started**](https://www.docker.com/get-started)**.**

Once installed, launch docker and set memory to 4GB. To do so select *Preferences* from docker icon on title bar. Then select *Advanced* on top and set the slider for memory to 4 GB and click *“Apply and Restart”*. Now Docker is ready for use.

# Download SQL Server :

To download SQL Server we will use docker . To do that open *terminal* and run following command:

```
docker pull microsoft/mssql-server-linux
docker run -d — name sql_server_demo -e ‘ACCEPT_EULA=Y’ -e ‘SA_PASSWORD=Pa55w0rd’ -p 1433:1433 microsoft/mssql-server-linux
```

This will take few minutes and latest SQL Server would be downloaded and would be used for Docker image in your system.

# Launch Docker image :

Run the following command to launch an instance of the Docker image you just downloaded:

```
docker run -d — name sql_server_demo -e ‘ACCEPT_EULA=Y’ -e ‘SA_PASSWORD=Pa55w0rd’ -p 1433:1433 microsoft/mssql-server-linux
```

Now to check if the image is running run the following command :

```
docker ps
```

If it is running and up, following will show up:

```
CONTAINER ID        IMAGE                          COMMAND                  3ba2722e72a1    microsoft/ms
```

# **Install SQL-CLI:**

If you dont have *node* installed, download it from https://nodejs.org/en/ and install it. Once install run this command:

```
npm install -g sql-cli
```

***Note\***: If you receive a permission denied error add sudo before the command.

# Run SQL-CLI:

Now you can access the server using SQL-CLI . Run the following command to access SQL-CLI:

```
mssql -u sa -p Pa55w0rd
```

------

# Connecting the SQL Server to IntelliJ:

Launch the IntelliJ and open *Preferences* from toolbar. Select or search Docker in left pane:

![img](https://miro.medium.com/max/22/1*kDUZ_wsxcZTATehO7EaarA.png?q=20)

![img](https://miro.medium.com/max/310/1*kDUZ_wsxcZTATehO7EaarA.png)

Then click + button on the right pane and select Docker for Mac and click OK.

![img](https://miro.medium.com/max/60/1*dwdJgrN_wZ-y032FwxtZHA.png?q=20)

![img](https://miro.medium.com/max/1164/1*dwdJgrN_wZ-y032FwxtZHA.png)

Now in the lower pane you could see Docker tab and on selecting it you could see the SQL Server image.

![img](https://miro.medium.com/max/60/1*5f287mn-Tf5nXuCI7LMqhQ.png?q=20)

![img](https://miro.medium.com/max/2810/1*5f287mn-Tf5nXuCI7LMqhQ.png)

# **Connect the intelliJ database to Docker image:**

Select database on the right panel of the ide:

![img](https://miro.medium.com/max/14/1*6SFomzylhpnqfeM2BTj7Wg.png?q=20)

![img](https://miro.medium.com/max/122/1*6SFomzylhpnqfeM2BTj7Wg.png)

Now click + and select *Data Source* from drop down . A setting window will pop up like this:

![img](https://miro.medium.com/max/60/1*w1OjckWiBW4_ewcMjB8k8Q.png?q=20)

![img](https://miro.medium.com/max/1608/1*w1OjckWiBW4_ewcMjB8k8Q.png)

Enter the details like User, Password and Port, and then click OK. Now it will take a moment to connect to the server and then Server will show up under the Database panel.

![img](https://miro.medium.com/max/60/1*dxhyOInTIvhDjJrTMIYfGw.png?q=20)

![img](https://miro.medium.com/max/668/1*dxhyOInTIvhDjJrTMIYfGw.png)

This guarantees that Server is set up successfully . Now you could do access database from here really easily.

As seen setting up a new Docker container for SQL Server is very easy and allows developers to create work on windows apps easily. For further details please reply.