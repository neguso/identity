# Accesa Identity App

## Description

A mobile application that provides information about Accesa employees. It offer an easy way of searching employees by name, e-mail, skype id, etc.

Display information about an employee: photo, name, phone, e-mail, skype, job, office location.

Mobile application is available to any employee, when application is started for the first time it asks for the user e-mail and sends an activation code to that e-mail to confirm the identity.
The identity is then stored on the device and used to authenticate the device/user in the future. The procedure is required for each new device.


## Requirements


### Application Architecture

Mobile application that uses web services deployed in cloud.
Data is stored in the cloud.
Data is pushed from Accesa on-premises servers to cloud storage through a web service.


### Web Services

* Runs on Azure
* Developed using .NET Core 1.0 using C#
* Database Azure SQL Server or DocumentDB
* Accesed through HTTP using REST/Json


### Mobile Application

* Mobile application runs on Android, iOS
* Developed using Cordova, Angular, Ionic


## Implementation

### Entities Schema

	Employee
	{
		Id : Guid,
		FirstName : string,
		LastName : string,
		E-mail : string,
		Skype : string,
		Photo: string,
		Location: string,
		Job: string
	}

### Web Services

1. Data Synchronization
2. Device Authetication
3. Search employee
4. Employee information
5. Employee photo

Services are autheticated using a token stored in the header.


#### 1. Data Synchronization Service

The service is called from company server to create/update/delete data.

	POST /sync?secret=s

	HEADER
	token

	BODY
	[
		{ id, check, firstname, lastname, ... },
		{ id, check, firstname, lastname, ... },
		...
	]

	id    - unique identifier, guid
	check - a number used to track data changes, a negative number means that record has been deleted
	...   - employee data fields

> Consider sending a limited number of records at a time.
> Send only the data that has been changed synce last synchronization, keep a local copy of what has been sent to the cloud storage.


#### 2. Device Authetication

GET /autheticate/{code}

[todo]


#### 3. Search employee

GET /employees?query=q&sort=s&skip=s&take=t

[todo]

#### 4. Employee information

GET /employees/{id}

[todo]


#### 5. Employee information

GET /photos/{id}?size=s

[todo]


### Mobile Application

[todo]
