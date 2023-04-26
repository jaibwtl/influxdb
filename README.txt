# influxdb

## Start your influxdb container and run below commands 
docker ps 
docker exec -it CONTAINERID /bin/bash
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
