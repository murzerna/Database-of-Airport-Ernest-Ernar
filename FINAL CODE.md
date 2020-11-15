# Database-of-Airport-Ernest

create table Pilots(
pilot_id INT,
first_name_p VARCHAR(32), 
last_name_p VARCHAR(32),
hire_date DATE,
phone_number VARCHAR(64),
airl_id INT,
flight_id INT,
PRIMARY KEY (pilot_id),
FOREIGN KEY (flight_id) REFERENCES Flights(flight_id),
FOREIGN KEY (airl_id) REFERENCES Airlines(airl_id)
);

--Created a table for pilots and assigned them air_id, flight_id to know which airline the pilot works for and which flight he serves.

create table Stewardesses(
stew_id INT,
first_name_s VARCHAR(32),
last_name_s VARCHAR(32),
hire_date DATE,
phone_number VARCHAR(64),
airl_id INT,
flight_id INT,
PRIMARY KEY (stew_id),
FOREIGN KEY (flight_id) REFERENCES Flights(flight_id),
FOREIGN KEY (airl_id) REFERENCES Airlines(airl_id)
);

--Creating a table for the service personnel on Board the aircraft, where we specify their data, the airline they work for and which flight they serve

create table Passengers(
ticket_id INT,
first_name_pg VARCHAR(32),
last_name_pg VARCHAR(32),
hire_date DATE,
phone_number VARCHAR(64),
airl_id INT,
flight_id INT,
baggage_id INT,
cafe_id INT,
class_of_pg VARCHAR(10),
PRIMARY KEY (ticket_id),
FOREIGN KEY (flight_id) REFERENCES Flights(flight_id),
FOREIGN KEY (airl_id) REFERENCES Airlines(airl_id),
FOREIGN KEY (baggage_id) REFERENCES Baggage(baggage_id),
FOREIGN KEY (cafe_id) REFERENCES Cafe(cafe_id),
FOREIGN KEY (class_of_pg) REFERENCES Classes(class_of_pg)
);

--We create a table for the airline customer, specify their personal data, which airline they fly, which flight, where they eat, and what class they belong to.

create table Flights(
flight_id INT,
airplanes_id INT,
airl_id INT,
ticket_id INT,
PRIMARY KEY (flight_id),
FOREIGN KEY (airplanes_id) REFERENCES Airplanes(airplanes_id),
FOREIGN KEY (airl_id) REFERENCES Airlines(airl_id)
);

/*Creating a table for flights, creating a primary key for flight_id, and applying it to other tables,
thanks to foreign keys, we know what information about flights consists of */

create table Baggage(
baggage_id INT,
capacity DECIMAL,
weight DECIMAL,
dimensions DECIMAL,
PRIMARY KEY (baggage_id)
);

--Creating a table for baggage, a unique baggage_id for each customer's baggage, and information about the baggage.

create table Airlines(
airl_id INT,
airlines_name VARCHAR(32),
airplanes_id INT,
class_of_airl VARCHAR(10),
PRIMARY KEY (airl_id),
FOREIGN KEY (airplanes_id) REFERENCES Airplanes(airplanes_id)
);
/*Creating a table for the airline, where we specify a unique url_id to know what kind of company it is, the company name, 
and thanks to foreign keys, to know what is included in the "Airlines" table" */

create table Airplanes(
airplanes_id INT,
model_name VARCHAR(64),
PRIMARY KEY (airplanes_id),
FOREIGN KEY (model_name) REFERENCES Aircraft_models(model_name)
);

--Creating a table for planes, assigning a unique airfanes_id to know the number of planes in the airline, and adding information about the model name and model_id

create table Aircraft_models( 
model_name VARCHAR(64),
PRIMARY KEY (model_name)
);

--Creating a table for aircraft models, in this table we fill in information about aircraft models 

create table Cafe(
cafe_id INT,
cafe_name VARCHAR(32),
PRIMARY KEY (cafe_id) 
);

create table Classes(
class_of_pg VARCHAR(20),
PRIMARY KEY (class_of_pg)
);

--Create a table for classes, where you specify the class type of passenger(business or economy), and class check(status airline)
