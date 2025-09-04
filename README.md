REQ1:CREATE A TABLE FOR FEED1,FEED2,FEED3 AND INSERTED THE DATA INTO THE TABLES.

CREATE TABLE FEED1:
CREATE TABLE Feed1 (
    col1 INT,
    col2 VARCHAR(50),
    col3 VARCHAR(50),
    col4 VARCHAR(50),
    col5 VARCHAR(50),
    col6 VARCHAR(50),
    col7 VARCHAR(50),
    col8 VARCHAR(50),
    col9 VARCHAR(50),
    col10 VARCHAR(50)
);

INSERT INTO Feed1 (col1, col2, col3, col4, col5, col6, col7, col8, col9, col10)
SELECT n,
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6),
       left(md5(random()::text), 6)
FROM generate_series(1, 10) AS n;

CREATE TABLE FOR FEED-2:
REATE TABLE Feed2 (
    col1 INT,
    col2 VARCHAR(50), col3 VARCHAR(50), col4 VARCHAR(50), col5 VARCHAR(50),
    col6 VARCHAR(50), col7 VARCHAR(50), col8 VARCHAR(50), col9 VARCHAR(50), col10 VARCHAR(50),
    col11 VARCHAR(50), col12 VARCHAR(50), col13 VARCHAR(50), col14 VARCHAR(50), col15 VARCHAR(50)
);

INSERT INTO Feed2 (col1,col2,col3,col4,col5,col6,col7,col8,col9,col10,col11,col12,col13,col14,col15)
SELECT n,
       left(md5(random()::text), 6), left(md5(random()::text), 6), left(md5(random()::text), 6),
       left(md5(random()::text), 6), left(md5(random()::text), 6), left(md5(random()::text), 6),
       left(md5(random()::text), 6), left(md5(random()::text), 6), left(md5(random()::text), 6),
       left(md5(random()::text), 6), left(md5(random()::text), 6), left(md5(random()::text), 6),
       left(md5(random()::text), 6), left(md5(random()::text), 6)
FROM generate_series(1, 15) AS n;

SELECT * FROM FEED2

-- Create table with 20 columns


CREATE TABLE Feed3 (
    col1 INT,
    col2 VARCHAR(50), col3 VARCHAR(50), col4 VARCHAR(50), col5 VARCHAR(50),
    col6 VARCHAR(50), col7 VARCHAR(50), col8 VARCHAR(50), col9 VARCHAR(50), col10 VARCHAR(50),
    col11 VARCHAR(50), col12 VARCHAR(50), col13 VARCHAR(50), col14 VARCHAR(50), col15 VARCHAR(50),
    col16 VARCHAR(50), col17 VARCHAR(50), col18 VARCHAR(50), col19 VARCHAR(50), col20 VARCHAR(50)
);

create table for feed-3
-- ✅ Insert exactly 20 columns
INSERT INTO Feed3 (
    col1,col2,col3,col4,col5,
    col6,col7,col8,col9,col10,
    col11,col12,col13,col14,col15,
    col16,col17,col18,col19,col20
)
SELECT n,
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6),  
       left(md5(random()::text), 6)   
FROM generate_series(1,20) AS n;

SELECT * FROM FEED3

REQ-2:Automate the Req 1 input file generation using SQL scripts and the parameter will be "Feed name" & Number of Rows to populate Data
REATE OR REPLACE PROCEDURE populate_feed(feed_name TEXT, num_rows INT)
LANGUAGE plpgsql
AS $$
DECLARE
    i INT := 1;
BEGIN
    WHILE i <= num_rows LOOP
        IF feed_name = 'Feed1' THEN
            INSERT INTO Feed1 (col1, col2, col3, col4, col5,
                               col6, col7, col8, col9, col10)
            VALUES (
                i,
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6),
                left(md5(random()::text), 6)
            );

        ELSIF feed_name = 'Feed2' THEN
            INSERT INTO Feed2 (col1, col2, col3, col4, col5,
                               col6, col7, col8, col9, col10,
                               col11, col12, col13, col14, col15)
            VALUES (
                i,
                left(md5(random()::text), 6), left(md5(random()::text), 6),
                left(md5(random()::text), 6), left(md5(random()::text), 6),
                left(md5(random()::text), 6), left(md5(random()::text), 6),
                left(md5(random()::text), 6), left(md5(random()::text), 6),
                left(md5(random()::text), 6), left(md5(random()::text), 6),
                left(md5(random()::text), 6), left(md5(random()::text), 6),
                left(md5(random()::text), 6), left(md5(random()::text), 6)
            );

       ELSIF feed_name = 'Feed3' THEN
    INSERT INTO Feed3 (col1, col2, col3, col4, col5,
                       col6, col7, col8, col9, col10,
                       col11, col12, col13, col14, col15,
                       col16, col17, col18, col19, col20)
    VALUES (
        i,  -- col1
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6),
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6), 
        left(md5(random()::text), 6)  
    );
END IF;

        i := i + 1;
    END LOOP;
END;
$$;


CALL populate_feed('Feed1', 10);
CALL populate_feed('Feed2', 15);
CALL populate_feed('Fee

REQ-3:Write SQL script to identify the duplicate (rows) in each of the table Feed-1, 2, 3
DROP TABLE IF EXISTS duplicates;
CREATE TABLE duplicates AS
(
    SELECT 'Feed1' AS source_table,
           col1, col2, col3, col4, col5,
           col6, col7, col8, col9, col10,
           NULL AS col11, NULL AS col12, NULL AS col13, NULL AS col14, NULL AS col15,
           NULL AS col16, NULL AS col17, NULL AS col18, NULL AS col19, NULL AS col20,
           COUNT(*) AS dup_count
    FROM Feed1
    GROUP BY col1, col2, col3, col4, col5,
             col6, col7, col8, col9, col10
    HAVING COUNT(*) > 1

    UNION ALL

    SELECT 'Feed2' AS source_table,
           col1, col2, col3, col4, col5,
           col6, col7, col8, col9, col10,
           col11, col12, col13, col14, col15,
           NULL AS col16, NULL AS col17, NULL AS col18, NULL AS col19, NULL AS col20,
           COUNT(*) AS dup_count
    FROM Feed2
    GROUP BY col1, col2, col3, col4, col5,
             col6, col7, col8, col9, col10,
             col11, col12, col13, col14, col15
    HAVING COUNT(*) > 1

    UNION ALL

    SELECT 'Feed3' AS source_table,
           col1, col2, col3, col4, col5,
           col6, col7, col8, col9, col10,
           col11, col12, col13, col14, col15,
           col16, col17, col18, col19, col20,
           COUNT(*) AS dup_count
    FROM Feed3
    GROUP BY col1, col2, col3, col4, col5,
             col6, col7, col8, col9, col10,
             col11, col12, col13, col14, col15,
             col16, col17, col18, col19, col20
    HAVING COUNT(*) > 1
);
SELECT  * FROM duplicates;

COPY duplicates TO '/tmp/duplicates.csv' WITH CSV HEADER;

select count(*) from feed1
select count(*) from feed2
select count(*) from feed3

REQ-5:Create a script to replace all the duplicates with Unique rows and update back to respective Feed table-- Feed1 (10 columns)
DROP TABLE IF EXISTS temp_feed1_with_pk;
CREATE TEMP TABLE temp_feed1_with_pk AS
SELECT
    row_number() OVER () AS pk,
    col1, col2, col3, col4, col5,
    col6, col7, col8, col9, col10
FROM Feed1;

-- Identify duplicates (keep first occurrence)
DROP TABLE IF EXISTS temp_feed1_to_update;
CREATE TEMP TABLE temp_feed1_to_update AS
SELECT pk
FROM (
    SELECT pk,
           ROW_NUMBER() OVER(
               PARTITION BY col1, col2, col3, col4, col5,
                            col6, col7, col8, col9, col10
               ORDER BY pk
           ) AS rn
    FROM temp_feed1_with_pk
) AS numbered_rows
WHERE rn > 1;

-- Update duplicates with unique values
UPDATE temp_feed1_with_pk
SET
    col1 = pk,  -- unique value
    col2 = substr(md5(random()::text),1,8),
    col3 = substr(md5(random()::text),1,8),
    col4 = substr(md5(random()::text),1,8),
    col5 = substr(md5(random()::text),1,8),
    col6 = substr(md5(random()::text),1,8),
    col7 = substr(md5(random()::text),1,8),
    col8 = substr(md5(random()::text),1,8),
    col9 = substr(md5(random()::text),1,8),
    col10 = substr(md5(random()::text),1,8)
WHERE pk IN (SELECT pk FROM temp_feed1_to_update);

-- Replace original table
TRUNCATE TABLE Feed1;
INSERT INTO Feed1 (col1, col2, col3, col4, col5, col6, col7, col8, col9, col10)
SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10
FROM temp_feed1_with_pk;

-- Verify duplicates removed
SELECT COUNT(*) AS number_of_duplicate_groups
FROM (
    SELECT COUNT(*)
    FROM Feed1
    GROUP BY col1, col2, col3, col4, col5,
             col6, col7, col8, col9, col10
    HAVING COUNT(*) > 1
) AS duplicate_counts;

-- =========================
-- Feed2 (15 columns)
-- =========================
DROP TABLE IF EXISTS temp_feed2_with_pk;
CREATE TEMP TABLE temp_feed2_with_pk AS
SELECT
    row_number() OVER () AS pk,
    col1, col2, col3, col4, col5,
    col6, col7, col8, col9, col10,
    col11, col12, col13, col14, col15
FROM Feed2;

DROP TABLE IF EXISTS temp_feed2_to_update;
CREATE TEMP TABLE temp_feed2_to_update AS
SELECT pk
FROM (
    SELECT pk,
           ROW_NUMBER() OVER(
               PARTITION BY col1, col2, col3, col4, col5,
                            col6, col7, col8, col9, col10,
                            col11, col12, col13, col14, col15
               ORDER BY pk
           ) AS rn
    FROM temp_feed2_with_pk
) AS numbered_rows
WHERE rn > 1;

UPDATE temp_feed2_with_pk
SET
    col1 = pk,
    col2 = substr(md5(random()::text),1,8),
    col3 = substr(md5(random()::text),1,8),
    col4 = substr(md5(random()::text),1,8),
    col5 = substr(md5(random()::text),1,8),
    col6 = substr(md5(random()::text),1,8),
    col7 = substr(md5(random()::text),1,8),
    col8 = substr(md5(random()::text),1,8),
    col9 = substr(md5(random()::text),1,8),
    col10 = substr(md5(random()::text),1,8),
    col11 = substr(md5(random()::text),1,8),
    col12 = substr(md5(random()::text),1,8),
    col13 = substr(md5(random()::text),1,8),
    col14 = substr(md5(random()::text),1,8),
    col15 = substr(md5(random()::text),1,8)
WHERE pk IN (SELECT pk FROM temp_feed2_to_update);

TRUNCATE TABLE Feed2;
INSERT INTO Feed2 (col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
                   col11, col12, col13, col14, col15)
SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
       col11, col12, col13, col14, col15
FROM temp_feed2_with_pk;

-- =========================
-- Feed3 (20 columns)
-- =========================
DROP TABLE IF EXISTS temp_feed3_with_pk;
CREATE TEMP TABLE temp_feed3_with_pk AS
SELECT
    row_number() OVER () AS pk,
    col1, col2, col3, col4, col5,
    col6, col7, col8, col9, col10,
    col11, col12, col13, col14, col15,
    col16, col17, col18, col19, col20
FROM Feed3;

DROP TABLE IF EXISTS temp_feed3_to_update;
CREATE TEMP TABLE temp_feed3_to_update AS
SELECT pk
FROM (
    SELECT pk,
           ROW_NUMBER() OVER(
               PARTITION BY col1, col2, col3, col4, col5,
                            col6, col7, col8, col9, col10,
                            col11, col12, col13, col14, col15,
                            col16, col17, col18, col19, col20
               ORDER BY pk
           ) AS rn
    FROM temp_feed3_with_pk
) AS numbered_rows
WHERE rn > 1;

UPDATE temp_feed3_with_pk
SET
    col1 = pk,
    col2 = substr(md5(random()::text),1,8),
    col3 = substr(md5(random()::text),1,8),
    col4 = substr(md5(random()::text),1,8),
    col5 = substr(md5(random()::text),1,8),
    col6 = substr(md5(random()::text),1,8),
    col7 = substr(md5(random()::text),1,8),
    col8 = substr(md5(random()::text),1,8),
    col9 = substr(md5(random()::text),1,8),
    col10 = substr(md5(random()::text),1,8),
    col11 = substr(md5(random()::text),1,8),
    col12 = substr(md5(random()::text),1,8),
    col13 = substr(md5(random()::text),1,8),
    col14 = substr(md5(random()::text),1,8),
    col15 = substr(md5(random()::text),1,8),
    col16 = substr(md5(random()::text),1,8),
    col17 = substr(md5(random()::text),1,8),
    col18 = substr(md5(random()::text),1,8),
    col19 = substr(md5(random()::text),1,8),
    col20 = substr(md5(random()::text),1,8)
WHERE pk IN (SELECT pk FROM temp_feed3_to_update);

TRUNCATE TABLE Feed3;
INSERT INTO Feed3 (col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
                   col11, col12, col13, col14, col15, col16, col17, col18, col19, col20)
SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
       col11, col12, col13, col14, col15, col16, col17, col18, col19, col20
FROM temp_feed3_with_pk;

req-6:Execute the duplicate script and check the output is zero
-- Check duplicates in Feed1
SELECT COUNT(*) AS duplicate_count
FROM (
    SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
           COUNT(*) AS cnt
    FROM Feed1
    GROUP BY col1, col2, col3, col4, col5, col6, col7, col8, col9, col10
    HAVING COUNT(*) > 1
) AS duplicates;

-- Check duplicates in Feed2
SELECT COUNT(*) AS duplicate_count
FROM (
    SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
           col11, col12, col13, col14, col15,
           COUNT(*) AS cnt
    FROM Feed2
    GROUP BY col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
             col11, col12, col13, col14, col15
    HAVING COUNT(*) > 1
) AS duplicates;

-- Check duplicates in Feed3
SELECT COUNT(*) AS duplicate_count
FROM (
    SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
           col11, col12, col13, col14, col15, col16, col17, col18, col19, col20,
           COUNT(*) AS cnt
    FROM Feed3
    GROUP BY col1, col2, col3, col4, col5, col6, col7, col8, col9, col10,
             col11, col12, col13, col14, col15,
             col16, col17, col18, col19, col20
    HAVING COUNT(*) > 1
) AS duplicates;

REQ-7:Create SQL script to compare data from Feed-2,3 to Feed-1 and write in output file on the compared results
-- Feed2 vs Feed1 (first 10 columns)
CREATE TEMP TABLE compare_feed2 AS
SELECT 'Feed2' AS source_table,
       f2.col1, f2.col2, f2.col3, f2.col4, f2.col5,
       f2.col6, f2.col7, f2.col8, f2.col9, f2.col10,
       CASE 
         WHEN f1.col1 IS NOT NULL THEN 'MATCH'
         ELSE 'NOT IN FEED1'
       END AS comparison_result
FROM Feed2 f2
LEFT JOIN Feed1 f1
  ON f1.col1 = f2.col1
 AND f1.col2 = f2.col2
 AND f1.col3 = f2.col3
 AND f1.col4 = f2.col4
 AND f1.col5 = f2.col5
 AND f1.col6 = f2.col6
 AND f1.col7 = f2.col7
 AND f1.col8 = f2.col8
 AND f1.col9 = f2.col9
 AND f1.col10 = f2.col10;

-- Feed3 vs Feed1 (first 10 columns)
CREATE TEMP TABLE compare_feed3 AS
SELECT 'Feed3' AS source_table,
       f3.col1, f3.col2, f3.col3, f3.col4, f3.col5,
       f3.col6, f3.col7, f3.col8, f3.col9, f3.col10,
       CASE 
         WHEN f1.col1 IS NOT NULL THEN 'MATCH'
         ELSE 'NOT IN FEED1'
       END AS comparison_result
FROM Feed3 f3
LEFT JOIN Feed1 f1
  ON f1.col1 = f3.col1
 AND f1.col2 = f3.col2
 AND f1.col3 = f3.col3
 AND f1.col4 = f3.col4
 AND f1.col5 = f3.col5
 AND f1.col6 = f3.col6
 AND f1.col7 = f3.col7
 AND f1.col8 = f3.col8
 AND f1.col9 = f3.col9
 AND f1.col10 = f3.col10;
-- Combine Feed2 + Feed3 comparison results
CREATE TEMP TABLE compare_results AS
SELECT * FROM compare_feed2
UNION ALL
SELECT * FROM compare_feed3;

COPY compare_results 
TO '/tmp/feed_comparison.csv' 
WITH CSV HEADER;

SELECT * FROM compare_results;

req-8:Create Test plan with all kinds of manual test cases in order to test this End to End functionality
-- Step 1: Create Test Plan Table
CREATE TABLE test_plan (
    test_id SERIAL PRIMARY KEY,
    test_type VARCHAR(50),        -- e.g., Functional, Negative, Boundary, etc.
    test_description TEXT,        -- What is being tested
    test_steps TEXT,              -- Step by step instructions
    expected_result TEXT,         -- What should happen
    actual_result TEXT,           -- To be filled after execution
    status VARCHAR(20),           -- Pass / Fail / Not Executed
    remarks TEXT                  -- Optional notes
);

-- Step 2: Insert Manual Test Cases for Feed End-to-End Testing

-- 1. Verify Feed Table Creation
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional', 
 'Verify Feed1 table creation with 10 columns', 
 'Run procedure to create Feed1 table with 10 columns', 
 'Feed1 table is created with columns col1..col10');

INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional', 
 'Verify Feed2 table creation with 15 columns', 
 'Run procedure to create Feed2 table with 15 columns', 
 'Feed2 table is created with columns col1..col15');

INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional', 
 'Verify Feed3 table creation with 20 columns', 
 'Run procedure to create Feed3 table with 20 columns', 
 'Feed3 table is created with columns col1..col20');

-- 2. Verify Data Population
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional',
 'Populate Feed1, Feed2, Feed3 with random data',
 'Run procedure generate_feed with appropriate parameters', 
 'Tables populated with the requested number of rows and columns');

-- 3. Verify Duplicate Removal
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional',
 'Remove duplicates from all feeds',
 'Run deduplication script using temporary tables and DISTINCT',
 'All tables contain only unique rows; no duplicates');

-- 4. Verify Duplicate Check
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional',
 'Check for duplicates after deduplication',
 'Run COUNT and COUNT(DISTINCT ROW(...)) queries for each feed',
 'Query returns zero duplicates for each feed');

-- 5. Verify Feed Comparison
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional',
 'Compare Feed2 and Feed3 with Feed1',
 'Run comparison script that LEFT JOINs Feed2/Feed3 with Feed1 and marks MATCH/NOT IN FEED1',
 'Comparison table correctly identifies matching and non-matching rows');

-- 6. Verify Export to CSV / Excel
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Functional',
 'Export comparison results to Excel-readable CSV',
 'Run \copy compare_results TO ... WITH CSV HEADER', 
 'CSV file is created and can be opened in Excel with all comparison rows');

-- 7. Negative / Boundary Test
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Negative',
 'Try inserting invalid data (NULL, oversized strings) into Feed tables',
 'Insert invalid rows manually',
 'Database throws errors or rejects invalid data');

-- 8. Performance Test
INSERT INTO test_plan (test_type, test_description, test_steps, expected_result)
VALUES
('Performance',
 'Populate Feed tables with large number of rows (1000+)',
 'Run generate_feed procedure with num_rows = 1000+',
 'Tables populate successfully without errors or timeouts');

-- Step 3: Query the Test Plan
SELECT * FROM test_plan ORDER BY test_id;

req-9:Automate the test cases (if possible) using any method but should be automated…
CREATE TABLE IF NOT EXISTS test_plan (
    test_id SERIAL PRIMARY KEY,
    test_type VARCHAR(50),
    test_description TEXT,
    test_steps TEXT,
    expected_result TEXT,
    actual_result TEXT DEFAULT 'Not Executed',
    status VARCHAR(20) DEFAULT 'Not Executed',
    remarks TEXT
);

CREATE OR REPLACE PROCEDURE run_feed_tests()
LANGUAGE plpgsql
AS $$
DECLARE
    total_rows INT;
BEGIN
    --Test 1: Feed1 table exists and has 10 columns
    PERFORM 1 FROM information_schema.columns 
            WHERE table_name='feed1' AND ordinal_position <= 10;
    IF FOUND THEN
        UPDATE test_plan
        SET actual_result = 'Feed1 table exists with 10 columns', status='Pass'
        WHERE test_id = 1;
    ELSE
        UPDATE test_plan
        SET actual_result = 'Feed1 table missing or incorrect columns', status='Fail'
        WHERE test_id = 1;
    END IF;

    -- Test 2: Feed1 populated with rows
    SELECT COUNT(*) INTO total_rows FROM feed1;
    IF total_rows > 0 THEN
        UPDATE test_plan
        SET actual_result = 'Feed1 populated with ' || total_rows || ' rows', status='Pass'
        WHERE test_id = 2;
    ELSE
        UPDATE test_plan
        SET actual_result = 'Feed1 has no data', status='Fail'
        WHERE test_id = 2;
    END IF;

    -- Test 3: Check duplicates removed in Feed1
    SELECT COUNT(*) INTO total_rows 
    FROM (
        SELECT col1, col2, col3, col4, col5, col6, col7, col8, col9, col10
        FROM feed1
        GROUP BY col1, col2, col3, col4, col5, col6, col7, col8, col9, col10
        HAVING COUNT(*) > 1
    ) AS dup;
    
    IF total_rows = 0 THEN
        UPDATE test_plan
        SET actual_result = 'No duplicates in Feed1', status='Pass'
        WHERE test_id = 3;
    ELSE
        UPDATE test_plan
        SET actual_result = total_rows || ' duplicates found in Feed1', status='Fail'
        WHERE test_id = 3;
    END IF;

    -- Test 4: Compare Feed2 with Feed1
    SELECT COUNT(*) INTO total_rows 
    FROM feed2 f2
    LEFT JOIN feed1 f1
    ON f2.col1=f1.col1 AND f2.col2=f1.col2 AND f2.col3=f1.col3 AND f2.col4=f1.col4 AND f2.col5=f1.col5
       AND f2.col6=f1.col6 AND f2.col7=f1.col7 AND f2.col8=f1.col8 AND f2.col9=f1.col9 AND f2.col10=f1.col10
    WHERE f1.col1 IS NULL;
    
    IF total_rows = 0 THEN
        UPDATE test_plan
        SET actual_result = 'All Feed2 rows match Feed1', status='Pass'
        WHERE test_id = 4;
    ELSE
        UPDATE test_plan
        SET actual_result = total_rows || ' Feed2 rows not in Feed1', status='Fail'
        WHERE test_id = 4;
    END IF;

   

END;
$$;

CALL run_feed_tests();
SELECT test_id, test_type, test_description, actual_result, status 
FROM test_plan
ORDER BY test_id;
