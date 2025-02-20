
# Hotel Reservation API

This is a REST API for managing hotel reservation data. It allows you to fetch a list of hotels and add new hotels to the system.

## Features
- **GET** `/hotels`: Retrieve a list of all hotels.
- **POST** `/hotels`: Add a new hotel to the system.

## Technologies Used
- **Spring Boot**: For building the REST API.
- **MySQL**: For storing hotel data.
- **JPA (Java Persistence API)**: For interacting with the database.

## API Endpoints

### 1. **Get All Hotels**
Retrieve a list of all available hotels.

- **Method**: `GET`
- **Endpoint**: `/hotels`
- **Response**: A list of hotel objects.
  
**Example:**
```json
[
  {
    "id": 1,
    "name": "Hotel ABC",
    "location": "New York",
    "pricePerNight": 150.0
  },
  {
    "id": 2,
    "name": "Hotel XYZ",
    "location": "Los Angeles",
    "pricePerNight": 200.0
  }
]
```

### 2. **Add a New Hotel**
Add a new hotel to the system.

- **Method**: `POST`
- **Endpoint**: `/hotels`
- **Request Body**: A JSON object containing the hotel details.
  - `name`: Name of the hotel (string)
  - `location`: Location of the hotel (string)
  - `pricePerNight`: Price per night for the hotel (number)

**Example Request:**
```json
{
  "name": "Hotel Sunshine",
  "location": "Miami",
  "pricePerNight": 180.0
}
```

**Example Response:**
```json
{
  "id": 3,
  "name": "Hotel Sunshine",
  "location": "Miami",
  "pricePerNight": 180.0
}
```

## Running the Project

### Prerequisites
Before running this project, ensure that you have the following installed on your machine:
- Java 17 or above
- Maven
- MySQL or any other compatible database

### Setting Up the Database
1. Create a database in MySQL. For example, you can create a database named `hotel_reservation_db`.
2. Create a table called `hotel` in your database. Here is the SQL code to create the table:
   ```sql
   CREATE TABLE hotel (
       id INT AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(255) NOT NULL,
       location VARCHAR(255) NOT NULL,
       pricePerNight DOUBLE NOT NULL
   );
   ```

### Configuring Database Connection
In the `src/main/resources/application.properties` file, add your MySQL database configuration:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/hotel_reservation_db
spring.datasource.username=root
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### Running the Application
1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/hotel-reservation-api.git
   ```
2. Navigate to the project directory:
   ```bash
   cd hotel-reservation-api
   ```
3. Build and run the project:
   ```bash
   mvn spring-boot:run
   ```

The application will start on `http://localhost:8080`. You can test the endpoints using tools like Postman or `curl`.

### Testing the API
You can test the API using the following `curl` commands:

- **GET All Hotels**:
  ```bash
  curl -X GET http://localhost:8080/hotels
  ```

- **Add a New Hotel**:
  ```bash
  curl -X POST http://localhost:8080/hotels        -H "Content-Type: application/json"        -d '{
             "name": "Hotel Sunshine",
             "location": "Miami",
             "pricePerNight": 100
           }'
  ```

## Contributing
Feel free to fork the repository, make improvements, and submit pull requests. Contributions are always welcome!

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
