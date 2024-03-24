
![](./Assets/docker-logo.png)

<details><summary>/BIN/BASH</summary>

<br/>

Login as root:

```docker exec -t -i -u root:root mssql-pix /bin/bash```

</details>

<details><summary>CP</summary>

<br/>

Copy files from a container

```docker cp <Container ID>:<Container path> <host path>```

Copy files into a container

```docker cp <Host path> <Container ID>:<Container path>```

</details>

<details><summary>MSSQL</summary>

<br/>

A volume can be attached on the Microsoft SQL Server too, as described on the [Microsoft Documentation](https://learn.microsoft.com/en-us/sql/linux/sql-server-linux-docker-container-deployment?view=sql-server-ver15&pivots=cs1-bash#persist):

[Configurar e personalizar contêineres do SQL Server no Docker](https://learn.microsoft.com/pt-br/sql/linux/sql-server-linux-docker-container-configure?view=sql-server-ver16&pivots=cs1-bash)

Using the above command to mount four folders of the container to a host directory and use a data volume container:

```
docker run 
--name container-name 
--env 'ACCEPT_EULA=Y' 
--env 'SA_PASSWORD=password' 
--publish 1433:1433 
--volume <VOLUME>:/var/opt/mssql 
--volume='C:\Docker\Containers\SQL Server\Data\':/var/opt/mssql/data 
--volume='C:\Docker\Containers\SQL Server\Log\':/var/opt/mssql/log 
--volume='C:\Docker\Containers\SQL Server\Secrets\':/var/opt/mssql/secrets 
--volume='C:\Docker\Containers\SQL Server\Tmp\':/tmp 
--detach mcr.microsoft.com/mssql/server
```

Example:

```
docker run --name mssql-container --env 'ACCEPT_EULA=Y' --env 'SA_PASSWORD=!1q@2w#3e%5t' --publish 1433:1433 --volume mssql-volume:/var/opt/mssql --volume='C:\Docker\Containers\SQL Server\Data\':/var/opt/mssql/data --volume='C:\Docker\Containers\SQL Server\Log\':/var/opt/mssql/log --volume='C:\Docker\Containers\SQL Server\Secrets\':/var/opt/mssql/secrets --volume='C:\Docker\Containers\SQL Server\Tmp\':/tmp --detach mcr.microsoft.com/mssql/server
```

### Container

![](./Assets/asset001.png)

![](./Assets/asset002.png)

### Volume

![](./Assets/asset003.png)

![](./Assets/asset004.png)

![](./Assets/asset005.png)

</details>

<details><summary>VIRTUAL HARD DISK (VHDX)</summary>

<br/>

The windows utility **diskpart** can be used to shrink **Virtual Hard Disk** (vhdx) files provided freed up space inside it by deleting any unnecessary files.

> [How to Shrink a WSL2 Virtual Disk](https://stephenreescarter.net/how-to-shrink-a-wsl2-virtual-disk/)

First make sure all WSL instances are shut down by opening an administrator command window and typing:

```wsl --shutdown```

Verify everything is stopped by:

```wsl.exe --list --verbose```

Then start diskpart:

```diskpart``` 

Inside diskpart type:

```DISKPART> select vdisk file="<path to vhdx file>"```

For example:

```DISKPART> select vdisk file="c:\users\user\appdata\local\docker\wsl\data\ext4.vhdx"```

It should respond by saying **DiskPart successfully selected the virtual disk file** 

Then to shrink:

```DISKPART> compact vdisk```

After this de **vhdx** file should in usage. Type **exit** to quit diskpart.

--- 

Another way: [Cleaning Up Docker Disk Space In WSL2](https://marcroussy.com/2020/12/01/cleaning-up-docker-disk-space-in-wsl2/)

> Im my case the images were deleted too.

</details>

