# dsmbootcamp.sample.semi_structured_hw tablosunda 2 kişinin sahip olduğu araç bilgileri ve bu araçları satın alma tarihleri yer almaktadır.
Beklenen dsmbootcamp.sample.semi_structured_hw tablosunu kullanarak dsmbootcamp.sample.semi_structured_hw_expected tablosundaki veriyi oluşturmaktır.

```SQL
select name,car.id as car_id, car.model as car_model,manufacture.year as manufacture_year,array(select as struct m.* replace(TIMESTAMP_ADD(m.date, INTERVAL 3 HOUR) as date) from unnest(purchase) as m) as purchase 
from fatma_gezer.semi_structured_hw
cross join unnest(car) as car
cross join unnest(manufacture) as manufacture on car.id = manufacture.id 
```
