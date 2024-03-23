
![](./Assets/docker-logo.png)

## mssql



You can attach a volume on the Microsoft SQL Server too, as described on the (Microsoft Documentation)[https://learn.microsoft.com/en-us/sql/linux/sql-server-linux-docker-container-deployment?view=sql-server-ver15&pivots=cs1-bash#persist]:

Using the above command to mount four folders of the container to a host directory and use a data volume container:

```ps
docker run 
--name container-name 
--env 'ACCEPT-EULA=Y' 
--env 'SA_PASSWORD=password' 
--publish 1433:1433 
--volume <VOLUME>:/var/opt/mssql 
--volume='C:\Docker\Containers\SQL Server\Pix\Data\':/var/opt/mssql/data 
--volume='C:\Docker\Containers\SQL Server\Pix\Log\':/var/opt/mssql/log 
--volume='C:\Docker\Containers\SQL Server\Pix\Secrets\':/var/opt/mssql/secrets 
--volume='C:\Docker\Containers\SQL Server\Pix\Tmp\':/tmp 
--detach mcr.microsoft.com/mssql/server
```

Example:

```ps
docker run --name mssql-container --env 'ACCEPT-EULA=Y' --env 'SA_PASSWORD=!1q@2w#3e%5t' --publish 1433:1433 --volume mssql-volume:/var/opt/mssql --volume='C:\Docker\Containers\SQL Server\Pix\Data\':/var/opt/mssql/data --volume='C:\Docker\Containers\SQL Server\Pix\Log\':/var/opt/mssql/log --volume='C:\Docker\Containers\SQL Server\Pix\Secrets\':/var/opt/mssql/secrets --volume='C:\Docker\Containers\SQL Server\Pix\Tmp\':/tmp --detach mcr.microsoft.com/mssql/server
```

### Container

![](./Assets/asset001.png)

![](./Assets/asset002.png)

### Volume

![](./Assets/asset003.png)

![](./Assets/asset004.png)

![](./Assets/asset005.png)