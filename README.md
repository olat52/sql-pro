select * from donation_data;
--How much is the total donation?
SELECT  sum("donation") AS TOTAL_DONATION
FROM donation_data;
-- What is the total donation by gender?
select gender,sum(donation)
from donation_data
group by gender;
select * from donor_data;
--Show the total donation and number of donations by gender
select gender, count(*) as number_of_donation, sum(donation)
from donation_data
group by gender;
-- d) Total donation made by frequency of donation
select distinct(donation_frequency),sum(donation) as total_donation
from donation_data
join donor_data on donation_data.id=donor_data.id
group by donation_frequency
order by total_donation;
-- e) Total donation and number of donation by Job field
select distinct(job_field),sum(donation) as total_donation,count(*) as number_of_donation
from donation_data
full join donor_data on donation_data.id=donor_data.id
group by job_field;
-- f) Total donation and number of donations above $200
SELECT  sum("donation"),count ("donation") as Number_of_donation
FROM donation_data
where donation >200;
-- g) Total donation and number of donations below $200
SELECT  sum("donation"),count ("donation") as Number_of_donation
FROM donation_data
where donation <200;
-- h) Which top 10 states contributes the highest donations
select distinct("state"),sum (donation) as total_donation 
from donation_data
group by "state"
order by total_donation desc
limit 10;
-- i) Which top 10 states contributes the least donations
select distinct("state"),sum (donation) as total_donation 
from donation_data
group by "state"
order by total_donation 
limit 10;
-- j) What are the top 10 cars driven by the highest donors
select concat(first_name,' ',last_name),donation,car
from donation_data
full join donor_data on donation_data.id=donor_data.id
order by donation desc
limit 10;
select concat(first_name,' ',last_name),donation,car,"state",job_field,donation_frequency
from donation_data
full join donor_data on donation_data.id=donor_data.id
order by donation desc
limit 10;# sql-pro
