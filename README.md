### mssql

You can attach a volume on the Microsoft SQL Server too, as described on the (Microsoft Documentation)[https://learn.microsoft.com/en-us/sql/linux/sql-server-linux-docker-container-deployment?view=sql-server-ver15&pivots=cs1-bash#persist]:

Using the above command to mount four folders of the container to a host directory and use a data volume container:

```ps
docker run --name container-name -e 'ACCEPT-EULA=Y' -e 'SA_PASSWORD=password' -p 1433:1433 -v <VOLUME>:/var/opt/mssql --volume='C:\Docker\Containers\SQL Server\Pix\Data\':/var/opt/mssql/data --volume='C:\Docker\Containers\SQL Server\Pix\Log\':/var/opt/mssql/log --volume='C:\Docker\Containers\SQL Server\Pix\Secrets\':/var/opt/mssql/secrets --volume='C:\Docker\Containers\SQL Server\Pix\Tmp\':/tmp -d mcr.microsoft.com/mssql/server
```
