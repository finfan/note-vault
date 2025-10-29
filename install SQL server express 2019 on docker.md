
# install SQL server express 2019 on docker 

SQL Server Express 2019 runs on Docker using the standard SQL Server 2019 image with specific configuration to enable Express edition. Here's the complete step-by-step process:[^1]

### Pull SQL Server 2019 Docker Image

First, pull the SQL Server 2019 Linux container image:

```bash
sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
```


### Run SQL Server Express Container

Run the container with Express edition configuration:

```bash
sudo docker run -e "ACCEPT_EULA=Y" \
  -e "MSSQL_SA_PASSWORD=IskiUtah2@6" \
  -e "MSSQL_PID=Express" \
  -p 1433:1433 \
  --name inventory-db \
  --hostname inventory-db \
  -d \
  mcr.microsoft.com/mssql/server:2019-latest
```


### Parameter Explanation

| Parameter | Description |
| :-- | :-- |
| `ACCEPT_EULA=Y` | Accept SQL Server End-User License Agreement (required) [^1] |
| `MSSQL_SA_PASSWORD` | Set the system administrator password (minimum 8 characters, complex) [^1] |
| `MSSQL_PID=Express` | Specify Express edition (this is the key difference from Developer edition) [^2] |
| `-p 1433:1433` | Map host port 1433 to container port 1433 [^1] |
| `--name` | Custom container name for easy management [^1] |
| `--hostname` | Set container hostname [^1] |
| `-d` | Run container in background (daemon mode) [^1] |

### Verify Container Status

Check that your container is running:

```bash
sudo docker ps -a
```

You should see output showing your container with `STATUS` as `Up`.[^1]

### Test Connection

Connect to the SQL Server container using sqlcmd:

```bash
sudo docker exec -it sqlserver2019-express /opt/mssql-tools18/bin/sqlcmd \
  -S localhost -U sa -P "IskiUtah2@6"
```


### Optional: Add Data Persistence

To persist your databases when the container restarts, add a volume mount:

```bash
sudo docker run -e "ACCEPT_EULA=Y" \
  -e "MSSQL_SA_PASSWORD=YourStrongPassword123!" \
  -e "MSSQL_PID=Express" \
  -p 1433:1433 \
  --name sqlserver2019-express \
  --hostname sqlserver2019-express \
  -v /host/data/path:/var/opt/mssql \
  -d \
  mcr.microsoft.com/mssql/server:2019-latest
```

Replace `/host/data/path` with your desired data directory on the Ubuntu server.[^1]

### Connect from External Applications

Use these connection details for external applications:

- **Server**: `localhost,1433` or your server's IP address
- **Authentication**: SQL Server Authentication
- **Username**: `sa`
- **Password**: Your specified password


### Security Best Practices

After initial setup, consider changing the SA password and creating dedicated user accounts for applications. The Express edition provides the same security features as other SQL Server editions but with usage limitations typical of Express editions.[^1]
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^21][^22][^23][^24][^25][^3][^4][^5][^6][^7][^8][^9]</span>

