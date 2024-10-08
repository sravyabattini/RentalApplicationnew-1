# RentalApplication

## Project Overview
RentalApplicationnew-1 is a Spring Boot-based web application designed for managing rental properties. The application offers role-based functionality with three user roles: Admin, Host, and Guest. 
- **Host**: Can add, update, or delete properties for rent and upload property photos.
- **Guest**: Can browse properties, view details, and book properties either individually or in bulk.
- **Admin**: Has access to user management, overseeing the activities of both hosts and guests.

## Tech Stack
- **Java Version**: 18
- **IDE**: Spring Tool Suite (STS)
- **Framework**: Spring MVC
- **View Layer**: JSP, jQuery, Bootstrap, JSTL
- **Persistence**: JPA, Hibernate, MS SQL Database
- **Security**: Spring Security (with JWT Authentication)
- **Database**: MS SQL

## Features
1. **Host Dashboard**: After logging in, hosts can view and manage their properties. They can add properties via a form and upload property photos, which are displayed on the homepage as cards.
2. **Guest Dashboard**: Guests can browse available properties, view property details, and book properties by specifying start and end dates for their stay.
3. **Bulk Booking**: Allows guests to book multiple properties at once by selecting properties and entering the booking details for the chosen properties.
4. **Admin Dashboard**: Manages users (hosts and guests), can view and modify user details, and oversee overall operations of the rental platform.
5. **Security**: The application uses JWT tokens for authentication and authorization, ensuring secure access for different user roles.

## Setup Instructions

### Prerequisites
1. **Java 18** should be installed.
2. **Apache Maven** should be installed to handle dependencies.
3. **MS SQL Server** should be running, with credentials and URL properly configured.
4. **Spring Tool Suite (STS)** configured with the Spring tools plugin.

### Configuration

#### Step 1: Clone the Repository



#### Step 2: Setup Database
    1. **Ensure MS SQL Server is Installed**: Make sure that MS SQL Server is running on your machine.
    2. **Create a New Database**:
   - Open SQL Server Management Studio (SSMS).
   - Connect to your SQL Server instance.
   - Right-click on the `Databases` folder and select **New Database**.
   - Name the database (e.g., `RentalDB`) and click **OK**.
3. **Configure Permissions**: Ensure that your application user has the necessary permissions to access the database.

#### Step 3: Configure Application Properties
Open the `src/main/resources/application.properties` file and update it with your MS SQL database configuration:
```properties
spring.datasource.url=jdbc:sqlserver://<server_url>:<port>;databaseName=<database_name>
spring.datasource.username=<your_username>
spring.datasource.password=<your_password>
spring.datasource.driver-class-name=com.microsoft.sqlserver.jdbc.SQLServerDriver

# Hibernate Properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.SQLServerDialect
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true

# View Layer Configurations
spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp

# Security and Logging
logging.level.org.springframework=DEBUG
logging.level.org.hibernate=DEBUG
logging.level.org.springframework.security=DEBUG

spring.main.allow-bean-definition-overriding=true

#### Step 4: Build the Project
Run the following command in the project root to resolve dependencies and build the application:
```bash
mvn clean install


#### Step 5: Run the Application
You can run the application through your IDE (STS or Eclipse) or from the command line with:
```bash
mvn spring-boot:run

### Accessing the Application
Once the application is running, access it at `http://localhost:8080`. Depending on your role:
- **Host**: Log in to access the host dashboard and manage properties.
- **Guest**: Browse and book available properties.
- **Admin**: Manage users and properties after logging in.

### Important Endpoints
- `/hostLogin`: Login page for Hosts.
- `/guestLogin`: Login page for Guests.
- `/adminLogin`: Admin login page.
- `/addProperty`: Host can add new properties.
- `/bulkBooking`: Guest can bulk book properties.
- `/propertyDetails`: Displays property details and allows booking.


### Key Features of the Application
- **JWT Authentication**: User authentication is managed through JWT tokens stored in cookies for secure session management.
- **Role-based Dashboard**: Separate views and functionalities for Admin, Guest, and Host roles.
- **Property Cards**: Properties are displayed in card format on the home page, with individual and bulk booking options.
- **Bulk Booking**: Guests can book multiple properties at once by selecting them from the homepage.
- **Image Upload**: Hosts can upload images for their properties, which are displayed alongside property details.

### Troubleshooting
- If the application fails to start, ensure the correct database URL, username, and password are set in `application.properties`.
- Ensure that MS SQL Server is up and running, and all tables are created correctly.
- Confirm all dependencies are resolved by running `mvn clean install`.

### Contributors
- **Alex** - Developer and Project Owner.

### License
This project is licensed under the MIT License.

