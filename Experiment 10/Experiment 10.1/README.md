select f_name,f_cost,f_type
from food 
where f_cost>(select AVG(f_cost) from food)