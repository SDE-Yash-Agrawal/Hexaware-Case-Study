# Case Study - Car Rental System

**Schema**

CREATE TABLE Vehicle (<br>
vehicleID INT PRIMARY KEY Identity(1,1),<br> 
make VARCHAR(50), <br>
model VARCHAR(50), <br>
year INT, <br>
dailyRate DECIMAL(10, 2),<br> 
status VARCHAR(15) CHECK (status IN ('available',<br> 
'notAvailable')), <br>
passengerCapacity INT,<br> 
engineCapacity DECIMAL(10, 2) <br>
); <br><br>
CREATE TABLE Customer ( <br>
customerID INT PRIMARY KEY identity(100,1), <br>
firstName VARCHAR(50), <br>
lastName VARCHAR(50), <br>
email VARCHAR(100), <br>
phoneNumber VARCHAR(15) <br>
); <br><br>
CREATE TABLE Lease ( <br>
leaseID INT PRIMARY KEY identity(300,1), <br>
vehicleID INT FOREIGN KEY REFERENCES Vehicle(vehicleID), <br>
customerID INT FOREIGN KEY REFERENCES Customer(customerID), <br>
startDate DATE, <br>
endDate DATE, <br>
type VARCHAR(50) CHECK (type IN ('DailyLease', 'MonthlyLease')) <br>
); <br><br>
CREATE TABLE Payment ( <br>
paymentID INT PRIMARY KEY identity(1000,1), <br>
leaseID INT FOREIGN KEY REFERENCES Lease(leaseID), <br>
paymentDate DATE, <br>
amount DECIMAL(10, 2) <br>
); <br>
