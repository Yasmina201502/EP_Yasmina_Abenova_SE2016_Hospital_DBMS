# EP_Yasmina_Abenova_SE2016_Hospital_DBMS

CREATE DATABASE Hospital;

CREATE TABLE hospital (
hosp_number DECIMAL(12) NOT NULL,
h_address VARCHAR(22),
PRIMARY KEY (hosp_number));

CREATE TABLE department (
dep_id DECIMAL(12) NOT NULL,
dep_name VARCHAR(22) NOT NULL,
hosp_number INT NOT NULL,
PRIMARY KEY (dep_id),
FOREIGN KEY (hosp_number) REFERENCES hospital (hosp_number));

CREATE TABLE doctors (
doc_id DECIMAL(12) NOT NULL,
d_fname VARCHAR(12) NOT NULL,
d_lname VARCHAR(12) NOT NULL,
d_dob DATE NOT NULL,
d_gend VARCHAR(6) NOT NULL,
tel_numb VARCHAR(12) NOT NULL,
salary INT NOT NULL,
dep_id DECIMAL(12) NOT NULL,
PRIMARY KEY (doc_id),
FOREIGN KEY (dep_id) REFERENCES department(dep_id));

CREATE TABLE treatment (
treat_id DECIMAL(12) NOT NULL,
treat_desc TEXT NOT NULL,
PRIMARY KEY (treat_id));


CREATE TABLE bill (
bill_id DECIMAL(12) NOT NULL,
price INT NOT NULL,
treat_id DECIMAL(12) NOT NULL,
PRIMARY KEY (bill_id),
FOREIGN KEY (treat_id) REFERENCES treatment(treat_id));

CREATE TABLE rooms(
room_id DECIMAL(12),
room_type VARCHAR(12),
PRIMARY KEY (room_id),
status BOOLEAN
);

CREATE TABLE patients (
p_id DECIMAL(12) NOT NULL,
p_fname VARCHAR(12) NOT NULL,
p_lname VARCHAR(12) NOT NULL,
p_dob DATE NOT NULL,
p_gend VARCHAR(6) NOT NULL,
p_address VARCHAR(32) NOT NULL,
tel_numb VARCHAR(12) NOT NULL,
date_admitted DATE NULL,
date_discharged DATE NULL,
bill_id DECIMAL(12) NOT NULL,
room_id DECIMAL(12) NOT NULL,
PRIMARY KEY (p_id),
FOREIGN KEY (bill_id) REFERENCES bill(bill_id),
FOREIGN KEY (room_id) REFERENCES rooms(room_id)
);




CREATE TABLE appointments (
app_id DECIMAL(12) NOT NULL,
app_date DATE NOT NULL,
app_time TIME NOT NULL,
p_id DECIMAL(12) NOT NULL,
doc_id DECIMAL(12) NOT NULL,
PRIMARY KEY (app_id),
FOREIGN KEY (p_id) REFERENCES patients(p_id),
FOREIGN KEY (doc_id) REFERENCES doctors (doc_id));



INSERT INTO hospital(hosp_number, h_address)
VALUES 
(17, '820 Lindbergh Drive');

INSERT INTO department(dep_id, dep_name, hosp_number)
VALUES 
(01, 'Accident and Emergency', 17),
(02, 'Anesthetics', 17),
(03, 'Cardiology', 17),
(04, 'Diagnostic Imaging', 17),
(05, 'Critical Care', 17),
(06, 'General Surgery', 17),
(07, 'Urology', 17),
(08, 'Gynecology', 17),
(09, 'Infection Control', 17),
(10, 'Neurology', 17);

INSERT INTO doctors(doc_id, d_fname, d_lname, d_dob, d_gend, tel_numb, salary, dep_id)
VALUES
(3008, 'Jodie', 'Whines', '1979-07-22', 'Male', '630-688-1327', 37000, 02), 
(2074, 'Toddy', 'Tulloch', '1987-02-03', 'Male', '974-841-2339', 25000, 03), 
(5374, 'Garvy', 'Kernar', '1985-05-01', 'Male', '549-609-0596', 25000, 08),
(4879, 'Max', 'Toplin', '1971-04-25', 'Female', '595-319-8097', 22000, 09),
(8896, 'Chip', 'Mariyushkin', '1990-05-04', 'Male', '794-493-1412', 19000, 05), 
(9418, 'Maudie', 'Follet', '1971-08-30', 'Female', '641-553-6835', 33000, 02), 
(9273, 'Blanche', 'Goghin', '1987-08-04', 'Female', '780-954-0786', 30000, 04), 
(3489, 'Maryellen', 'MacRanald', '1975-12-26', 'Female', '212-410-4734', 15000, 07), 
(7140, 'Darlene', 'Linklet', '1986-04-17', 'Female', '152-635-0292', 23000, 06), 
(3150, 'Jean', 'Rodinger', '1983-04-14', 'Male', '431-560-5054', 37000, 08), 
(8269, 'Kellina', 'Swindley', '1985-12-02', 'Female', '938-653-3730', 15000, 10), 
(6827, 'Cece', 'Skeemer', '1979-03-27', 'Male', '489-212-8513', 17000, 01), 
(1242, 'Gertie', 'Ziemen', '1974-04-16', 'Female', '378-122-7448', 23000, 03),
(6593, 'Wilmette', 'Edwinson', '1976-07-27', 'Female', '151-168-0821', 33000, 06),
(8498, 'Caril', 'Mattiello', '1986-03-08', 'Female', '999-280-6787', 30000, 09),
(5196, 'Naomi', 'Smithson', '1990-08-28', 'Female', '888-205-4434', 22000, 07),
(9923, 'Sholom', 'Rebanks', '1983-12-03', 'Male', '453-704-2254', 22000, 10),
(5398, 'Burt', 'Treslove', '1970-12-07', 'Male', '389-618-0712', 17000, 01),
(1695, 'Huberto', 'Flintiff', '1987-09-10', 'Male', '608-698-5818', 19000, 04), 
(3279, 'Fawnia', 'Schroter', '1988-08-11', 'Female', '717-179-9271', 22000, 05); 

INSERT INTO treatment(treat_id, treat_desc)
VALUES
(108, 'Musculoskeletal Injuries'),
(342, 'First Aid'),
(189, 'Tensilon Test'), 
(221, 'Arm X-ray'), 
(848, 'Coronary Artery Bypass'), 
(938, 'Anesthesia '), 
(245, 'Vacnination'), 
(216, 'Sleep Study'), 
(962, 'First Aid'), 
(188, 'Vactination'), 
(580, 'MRI'), 
(658, 'Adhesiolysis'), 
(137, 'Atherectomy'), 
(237, 'Central Line Placement'), 
(696, 'Anesthesia'), 
(622, 'Hydrocoele '), 
(993, 'Embolic Protection'), 
(463, 'Invasive Cardiac Monitoring'), 
(728, 'Circumcision'),
(710, 'Cervical (Cone) Biopsy'); 


INSERT INTO bill(bill_id, price, treat_id)
VALUES
(4619, 4000, 108),
(9038, 1500, 342),
(2715, 3000, 189),
(2247, 4500, 221),
(8544, 1000, 848),
(8168, 2000, 938),
(7843, 4000, 245),
(4743, 2100, 216),
(4620, 3000, 962),
(4613, 2222, 188),
(6916, 2000, 580),
(6536, 4500, 658),
(3389, 1800, 137),
(6309, 4000, 237),
(5010, 3000, 696),
(4836, 3100, 622),
(3656, 2100, 993),
(6974, 2200, 463),
(3636, 1600, 728),
(2207, 3500, 710);

INSERT INTO rooms(room_id, room_type, occupied)
VALUES
(101, 'single', 'TRUE'),
(102, 'double', 'TRUE'),
(103, 'single', 'TRUE'),
(104, 'single', 'FALSE'),
(105, 'triple', 'TRUE'),
(106, 'double', 'TRUE'),
(107, 'triple', 'TRUE'),
(108, 'triple', 'TRUE'),
(109, 'triple', 'TRUE'),
(110, 'triple', 'FALSE');

INSERT INTO patients(p_id, p_fname, p_lname, p_dob, p_gend, p_address, tel_numb, date_admitted, date_discharged, bill_id, room_id)
VALUES
(23210, 'Marybeth', 'Allmark', '1989-10-02', 'Female', '860 Clemons Road', '393-239-8697', '2020-07-10', '2020-08-13', 4619, 101),
(15668, 'Berti', 'Puttock', '2004-03-26', 'Male', '708 Springs Place', '445-104-7293', '2020-06-23', '2020-07-07', 9038, 102),
(46367, 'Roz', 'Creser', '2006-09-16', 'Female', '5 Gerald Street', '432-649-1184', '2020-08-09', '2020-08-30', 2715, 103),
(74983, 'Wendell', 'Wingate', '1978-03-20', 'Male', '9 Linden Road', '601-499-3788', '2020-08-02', '2020-08-31', 2247, 102),
(13610, 'Winnifred', 'Schooley', '1981-07-02', 'Female', '24928 Kenwood Pass', '251-989-2531', '2020-09-15', '2020-09-18', 8544, 105),
(69663, 'Walt', 'Finnis', '1953-05-06', 'Male', '9634 Luster Center', '962-538-0203', '2020-10-16', '2020-11-01', 8168, 106),
(74539, 'Gale', 'Hartly', '1983-04-07', 'Male', '1811 Anzinger Place', '973-347-2835', '2020-07-15', '2020-07-30', 7843, 105),
(51974, 'Conway', 'Pleven', '1980-06-16', 'Male', '7 Pond Lane', '859-491-1849', '2020-10-13', '2020-11-09', 4743, 106),
(20564, 'Sada', 'Jirik', '1979-06-07', 'Female', '122 Sachs Avenue', '720-962-8754', '2020-04-28', '2020-05-09', 4620, 105),
(26794, 'Danit', 'Kirkbride', '1995-03-17', 'Female', '8365 Elka Parkway', '916-497-9545', '2020-06-02', '2020-06-18', 4613, 107),
(90524, 'Al', 'Chater', '1960-02-26', 'Male', '219 Hayes Plaza', '369-692-7123', '2020-07-01', '2020-07-11', 6916, 107),
(13357, 'Diana', 'Lerer', '1956-05-24', 'Female', '2394 Springview Street', '849-628-8108', '2020-08-29', '2020-09-06', 6536, 107),
(49325, 'Korrie', 'Kiefer', '1955-08-15', 'Female', '942 Twin Pines Street', '212-835-0795', '2020-09-02', '2020-09-11', 3389, 108),
(60517, 'Windy', 'Gutans', '2008-11-21', 'Female', '9 Novick Way', '912-991-5131', '2020-04-02', '2020-04-17', 6309, 109),
(68533, 'Faye', 'FitzGilbert', '1950-09-04', 'Female', '5814 Schurz Junction', '151-440-4122', '2020-04-30', '2020-05-10', 5010, 108),
(33858, 'Eli', 'Fitzsimmons', '1981-10-03', 'Male', '8821 Melrose Drive', '865-775-1077', '2020-02-04', '2020-02-18', 4836, 108),
(71562, 'Jasun', 'Grand', '1992-08-22', 'Male', '213 Rutledge Point', '815-597-3487', '2020-03-22', '2020-03-28', 3656, 109),
(93582, 'Arielle', 'Gilford', '1960-06-29', 'Female', '1 8th Terrace', '958-664-8767', '2020-06-27', '2020-07-07', 6974, 109),
(79022, 'Ax', 'Bynert', '1965-12-04', 'Male', '3 3rd Pass', '317-370-0902', '2020-08-07', '2020-08-14', 3636, 110),
(57178, 'Garvy', 'Skill', '1952-02-04', 'Male', '254 Anthes Parkway', '741-157-9025', '2020-01-29', '2020-02-11', 2207, 110);



INSERT INTO appointments(app_id, app_date, app_time, p_id, doc_id)
VALUES
(900, '2020-07-08', '12:00', 23210, 3008),
(954, '2020-06-20', '8:45', 15668, 2074),
(571, '2020-08-07', '12:50', 46367, 5374),
(274, '2020-07-30', '12:54', 74983, 4879),
(686, '2020-09-10', '12:45', 13610, 8896),
(353, '2020-10-14', '13:30', 69663, 9418),
(841, '2020-07-06', '14:45', 74539, 9273),
(317, '2019-10-10', '14:39', 51974, 3489),
(741, '2020-04-21', '8:59', 20564, 7140),
(247, '2020-06-01', '13:09', 26794, 3150),
(919, '2020-06-28', '16:31', 90524, 8269),
(613, '2020-08-25', '17:34', 13357, 6827),
(363, '2020-08-30', '9:24', 49325, 1242),
(858, '2019-04-01', '11:06', 60517, 6593),
(287, '2020-04-20', '11:36', 68533, 8498),
(462, '2020-02-02', '10:24', 33858, 5196),
(898, '2019-03-20', '14:58', 71562, 9923),
(191, '2019-06-22', '8:21', 93582, 5398),
(429, '2020-08-05', '13:09', 79022, 1695),
(811, '2020-01-25', '17:35', 57178, 3279);



ALTER TABLE rooms
RENAME TO occupied_room;

ALTER TABLE doctors
ADD COLUMN hire_date DATE;

ALTER TABLE doctors
DROP COLUMN hire_date;

ALTER TABLE patients
ADD CONSTRAINT tel_numb UNIQUE (tel_numb);

ALTER TABLE patients
DROP CONSTRAINT tel_numb;


SELECT MAX(salary), MIN(salary), SUM(salary), AVG(salary)
FROM doctors;

SELECT doc_id, d_fname, d_lname, salary, dep_id, d_gend
FROM doctors
WHERE d_gend = 'Female';

SELECT COUNT (d_gend)
FROM doctors
WHERE d_gend = 'Male'
GROUP BY dep_id;

SELECT doc_id, d_fname, d_lname, salary, dep_id
FROM doctors
WHERE salary > 25000;

SELECT  doctors.d_fname, doctors.d_lname, doctors.doc_id, department.dep_id, doctors.salary
FROM doctors
LEFT OUTER JOIN department
ON doctors.dep_id = department.dep_id
WHERE doctors.salary > (SELECT MIN(salary) FROM doctors);

SELECT  patients.p_id, occupied_room.room_id, occupied_room.room_type, occupied_room.occupied
FROM occupied_room
INNER JOIN patients
ON patients.room_id = occupied_room.room_id
WHERE occupied = 'FALSE';
