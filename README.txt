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
> exit
