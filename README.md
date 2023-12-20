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

**The second step is to look for information about Annabelle who lives on Franklin Street.** 

```
SELECT *
FROM person
WHERE address_street_name = 'Franklin Ave'
AND name LIKE '%Annabel%'
```

**The third step is to look for information about the person who lives in the last house on Northwestern Dr.**

```
SELECT *
FROM person
WHERE address_street_name = 'Northwestern Dr'
ORDER BY address_number DESC
```

**The fourth step is to look for information on their reports.**

```
SELECT *
FROM interview
WHERE person_id IN (14887, 16371)
```

**5 step.  We are looking for a car using the data from the reports.**

```
SELECT p.*
FROM drivers_license as dl
JOIN person as p on dl.id = p.license_id
WHERE plate_number LIKE '%H42%'
```

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

**7 steps. I check this person as he fits, and you can see that not everything is as easy as we thought**

```
INSERT INTO solution VALUES (1, 'Jeremy Bowers');

SELECT value FROM solution;
```

**8 step. Checking this person's report.** 

```
select * from interview
WHERE person_id = 67318
```


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

**10 step. Found the real killer**
