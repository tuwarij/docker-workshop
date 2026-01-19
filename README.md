# docker-workshop

HW1 Answer
1. pip ---version

3.select count(*) 
from green_tripdata
where trip_distance <= 1 and to_char(lpep_pickup_datetime, 'YYYY-MM') = '2025-11' 
;

4.SELECT lpep_pickup_datetime, trip_distance
FROM green_tripdata
WHERE trip_distance = (
    SELECT MAX(trip_distance) 
    FROM green_tripdata 
    WHERE trip_distance < 100
);

5.select sum(g."PULocationID"),min(z."Zone") from green_tripdata g 
join zone z on g."PULocationID" = z."LocationID"
group by z."Zone" 
order by 1 desc 
;

6.select max(g."tip_amount"),min(zpu."Zone"),min(zdo."Zone") from green_tripdata g 
join zone zpu on g."PULocationID" = zpu."LocationID" join zone zdo on g."DOLocationID" = zdo."LocationID"
where zpu."Zone" LIKE '%East Harlem North%'
group by zdo."Zone"
order by 1 desc 
;
