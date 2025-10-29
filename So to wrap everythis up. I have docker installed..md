
# So to wrap everythis up. I have docker installed. its running a container with sql server express 2019. how do i list all the settings for docker and sql server.

Here's how to get a complete overview of your Docker container and SQL Server configuration:

## Docker Container Settings

### Basic Container Information

```bash
# List running containers with key details
sudo docker ps -a

# Get detailed container configuration (JSON format)
sudo docker inspect sqlserver2019-express
```


### Container Environment Variables

```bash
# View all environment variables
sudo docker exec sqlserver2019-express env

# View SQL Server specific environment variables
sudo docker exec sqlserver2019-express env | grep MSSQL
```


### Container Resources and Networking

```bash
# View container resource usage
sudo docker stats sqlserver2019-express --no-stream

# View container network settings
sudo docker inspect sqlserver2019-express | grep -A 20 "NetworkSettings"

# View port mappings
sudo docker port sqlserver2019-express
```


### Volume Mounts and Storage

```bash
# View volume mounts
sudo docker inspect sqlserver2019-express | grep -A 10 "Mounts"

# View container size
sudo docker system df
```


## SQL Server Configuration Settings

### Connect and View SQL Server Settings

```bash
# Connect to SQL Server
sudo docker exec -it sqlserver2019-express /opt/mssql-tools18/bin/sqlcmd \
  -S localhost -U sa -P "YourStrongPassword123!" -C
```


### Essential SQL Server Configuration Queries

Once connected to sqlcmd, run these queries:

#### 1. Server Information

```sql
SELECT 
    @@VERSION as SQLVersion,
    @@SERVERNAME as ServerName,
    SERVERPROPERTY('ProductLevel') as ProductLevel,
    SERVERPROPERTY('Edition') as Edition,
    SERVERPROPERTY('EngineEdition') as EngineEdition;
GO
```


#### 2. All Configuration Settings[^1]

```sql
SELECT 
    name,
    value as ConfigValue,
    value_in_use as RunValue,
    minimum,
    maximum,
    is_dynamic,
    is_advanced,
    description
FROM sys.configurations
ORDER BY name;
GO
```


#### 3. Memory and Performance Settings[^2]

```sql
SELECT 
    name,
    value_in_use as CurrentValue,
    CASE name
        WHEN 'max server memory (MB)' THEN 'Maximum memory for SQL Server'
        WHEN 'min server memory (MB)' THEN 'Minimum memory for SQL Server'
        WHEN 'max degree of parallelism' THEN 'Max parallel processors'
        WHEN 'cost threshold for parallelism' THEN 'Parallelism threshold'
    END as Description
FROM sys.configurations
WHERE name IN (
    'max server memory (MB)',
    'min server memory (MB)',
    'max degree of parallelism',
    'cost threshold for parallelism'
);
GO
```


#### 4. Database Files Location

```sql
SELECT 
    database_id,
    name as DatabaseName,
    physical_name as FilePath,
    type_desc as FileType,
    size * 8 / 1024 as SizeMB
FROM sys.master_files
ORDER BY database_id, type;
GO
```


#### 5. Current Connections

```sql
SELECT 
    login_name,
    program_name,
    client_interface_name,
    login_time,
    last_request_start_time
FROM sys.dm_exec_sessions
WHERE is_user_process = 1;
GO
```


## Complete Configuration Summary Script

Create this bash script to get everything at once:

```bash
#!/bin/bash
echo "=== DOCKER CONTAINER CONFIGURATION ==="
echo "Container Status:"
sudo docker ps -f name=sqlserver2019-express

echo -e "\nEnvironment Variables:"
sudo docker exec sqlserver2019-express env | grep MSSQL

echo -e "\nPort Mappings:"
sudo docker port sqlserver2019-express

echo -e "\nVolume Mounts:"
sudo docker inspect sqlserver2019-express | grep -A 10 "Mounts"

echo -e "\nResource Usage:"
sudo docker stats sqlserver2019-express --no-stream

echo -e "\n=== SQL SERVER CONFIGURATION ==="
echo "Connecting to SQL Server for configuration details..."

sudo docker exec sqlserver2019-express /opt/mssql-tools18/bin/sqlcmd \
  -S localhost -U sa -P "YourStrongPassword123!" -C -Q \
  "SELECT @@VERSION as SQLVersion, @@SERVERNAME as ServerName, SERVERPROPERTY('Edition') as Edition;"

echo -e "\nKey Configuration Settings:"
sudo docker exec sqlserver2019-express /opt/mssql-tools18/bin/sqlcmd \
  -S localhost -U sa -P "YourStrongPassword123!" -C -Q \
  "SELECT name, value_in_use FROM sys.configurations WHERE name IN ('max server memory (MB)', 'max degree of parallelism') ORDER BY name;"
```


## Key Settings to Review

### Docker Level:

- **Container Status**: Running/stopped
- **Port Mappings**: 1433:1433
- **Environment Variables**: MSSQL_PID=Express, ACCEPT_EULA=Y
- **Volume Mounts**: Data persistence location
- **Resource Limits**: Memory/CPU constraints


### SQL Server Level:

- **Edition**: Express (limited to 10GB database size, 1GB RAM)
- **Version**: SQL Server 2019 build number
- **Memory Settings**: Usually defaults in Express
- **Security**: SA account enabled, authentication mode
- **Database Files**: Location and sizes

This comprehensive approach gives you complete visibility into both your Docker container configuration and the SQL Server instance running inside it.[^3][^4][^1]
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^5][^6][^7][^8][^9]</span>

<div align="center">⁂</div>


