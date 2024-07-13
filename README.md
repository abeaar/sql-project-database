halo nama ku Babol, mahasiswa statistika semester 4 
ini projek coursera ku yang sudah selesai

how to run this code
clone github
--
--

--
output nya 

#1
SELECT SUM(Value) FROM milk_production WHERE Year = 2023;

#2
SELECT State_ANSI FROM cheese_production WHERE Year = 2023 AND Period = 'APR' AND Value > 100000000;

#3
SELECT Year, SUM(Value) FROM coffee_production GROUP BY Year;

#4
SELECT AVG(Value) FROM honey_production WHERE Year = 2022;

#5
SELECT * FROM state_lookup;

#6
SELECT s.State, c.Value
FROM state_lookup s
LEFT JOIN cheese_production c ON s.State_ANSI = c.State_ANSI AND c.Year = 2023 AND c.Period = 'APR';

#7
SELECT SUM(yp.Value) AS total_yogurt_production_2022
FROM ucdavis.yogurt_production yp
WHERE yp.Year = 2022
AND yp.State_ANSI IN (
    SELECT DISTINCT cp.State_ANSI
    FROM ucdavis.cheese_production cp
    WHERE cp.Year = 2023
);

#8
SELECT COUNT(sl.State_Name) AS missing_states_count
FROM ucdavis.state_lookup sl
LEFT JOIN ucdavis.milk_production mp ON sl.State_ANSI = mp.State_ANSI AND mp.Year = 2023
WHERE mp.State_ANSI IS NULL;

#9
SELECT sl.State_Name, COALESCE(cp.Value, 0) AS Cheese_Production_Apr_2023
FROM ucdavis.state_lookup sl
LEFT JOIN ucdavis.cheese_production cp ON sl.State_ANSI = cp.State_ANSI AND cp.Year = 2023 AND cp.Period = 'APR';

#10
SELECT AVG(cp.Value) AS average_coffee_production
FROM ucdavis.coffee_production cp
WHERE cp.Year IN (
    SELECT DISTINCT hp.Year
    FROM ucdavis.honey_production hp
    WHERE hp.Value > 1000000
);
