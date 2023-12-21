# SQL-Murder-Mystery
## Solution to the quest!

**Hi, I want to show you the solution to the quest.**

**The first step is to request a crime scene report. Here you will find screenshots of the execution and the necessary code**
```
SELECT * 
FROM crime_scene_report
WHERE type = 'murder'
AND city = 'SQL City'
AND date = 20180115
```
![1](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/eb3eab6c-27a1-46d8-a0b6-5497c082ba39)

**The second step is to look for information about Annabelle who lives on Franklin Street.** 

```
SELECT *
FROM person
WHERE address_street_name = 'Franklin Ave'
AND name LIKE '%Annabel%'
```
![3](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/190916e3-3fe7-44b1-8926-82b61293dc03)



**The third step is to look for information about the person who lives in the last house on Northwestern Dr.**

```
SELECT *
FROM person
WHERE address_street_name = 'Northwestern Dr'
ORDER BY address_number DESC
```
![2](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/9197af27-5b66-499b-be5c-0ff0414eb768)

**The fourth step is to look for information on their reports.**

```
SELECT *
FROM interview
WHERE person_id IN (14887, 16371)
```
![4](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/0ffe3696-acb8-462d-9101-b7999f398527)

**5 step.  We are looking for a car using the data from the reports.**

```
SELECT p.*
FROM drivers_license as dl
JOIN person as p on dl.id = p.license_id
WHERE plate_number LIKE '%H42%'
```
![5](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/febfd1f2-ca49-47ae-8ae2-51a4d1972218)


**6 steps.  I find this person thanks to the reports, making the necessary joins under certain conditions.**

```
SELECT p.*, gf.*, ci.*
FROM drivers_license as dl
JOIN person as p on dl.id = p.license_id
JOIN get_fit_now_member as gf on p.id = gf.person_id
JOIN get_fit_now_check_in as ci on gf.id = ci.membership_id
WHERE plate_number LIKE '%H42%'
AND check_in_date = 20180109
AND membership_status = 'gold'
```
![6](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/4dd5ecb2-5a86-4a5f-9563-f7163661b794)


**7 steps. I check this person as he fits, and you can see that not everything is as easy as we thought**

```
INSERT INTO solution VALUES (1, 'Jeremy Bowers');

SELECT value FROM solution;
```
![7](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/49c672a5-a839-463e-87aa-d54c2432012c)


**8 step. Checking this person's report.** 

```
select * from interview
WHERE person_id = 67318
```
![10](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/2dab4ec7-0f60-4de5-ad5f-e558931633fc)


**9 step. I take the necessary actions to search for a car and a person by its parameters.**
```
SELECT *
FROM drivers_license as dl
JOIN person as p on dl.id = p.license_id
JOIN facebook_event_checkin as fb on fb.person_id = p.id
WHERE hair_color = 'red'
AND height >= 65
AND height <= 67
AND car_make = 'Tesla'
AND car_model = 'Model S'
AND gender = 'female'
```
![8](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/cb701fd7-693b-4097-9a4f-fb6a0d27ac0e)


**10 step. Found the real killer**

![9](https://github.com/OK1719/SQL-Murder-Mystery/assets/152031226/67c8a6c2-f1b1-4e60-af53-fbc62c147487)
