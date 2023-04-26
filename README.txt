# influxdb

## Start your influxdb container and run below commands 
docker run -d -p 8086:8086       -e DOCKER_INFLUXDB_INIT_MODE=setup       -e DOCKER_INFLUXDB_INIT_USERNAME=my-user       -e DOCKER_INFLUXDB_INIT_PASSWORD=my-password       -e DOCKER_INFLUXDB_INIT_ORG=my-org       -e DOCKER_INFLUXDB_INIT_BUCKET=my-bucket       -e DOCKER_INFLUXDB_INIT_RETENTION=1w       -e DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=my-super-secret-auth-token       influxdb
docker ps 
docker exec -it CONTAINERID /bin/bash
influx config create --config-name my-org --host-url "http://localhost:8086"  --org "my-org"  --token "my-super-secret-auth-token"  --active
influx bucket create --name demo010 -c my-org
influx write -c my-org --bucket demo010 --url https://raw.githubusercontent.com/jaibwtl/influxdb/main/air-sensor-data-annotated.csv
influx v1 shell
> show databases;
> use demo010
> show measurements
> select * from "airSensors"
> select * from "airSensors" where time <= '2023-04-26'
> select * from "airSensors" where time <= '2023-04-25' AND time <= '2023-04-26'
> select * from "airSensors" where time <= '2023-04-25T05:00:00Z' AND time <= '2023-04-26'
> select * from "airSensors" where time <= '2023-04-25T05:00:00Z' AND time <= '2023-04-26T05:00:00Z'
> select * from "airSensors" where time <= '2023-04-25T05:00:00Z' AND time <= '2023-04-26T05:00:00Z'
> select * from "airSensors" where sensor_id = 'TLM0100'
> select * from "airSensors" where sensor_id = 'TLM0100' AND humidity > 35
> select max(humidity) from "airSensors" where sensor_id = 'TLM0100' 
> select min(humidity) from "airSensors" where sensor_id = 'TLM0100' 
> select mean(humidity) from "airSensors" where sensor_id = 'TLM0100' 
> select count(*) from "airSensors" where sensor_id = 'TLM0100'

## Start Grafana 
docker ps 
docker run -d --name=grafana -p 3000:3000 grafana/grafana
# Open http://IP:3000
# User: admin Password: admin
