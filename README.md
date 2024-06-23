# UserService

UserService is a gRPC-based user management system with JSON transcoding support, allowing it to be accessed via both gRPC and RESTful HTTP endpoints.

## Features

- User registration and authentication
- User profile management
- Role-based access control
- Password change functionality
- Admin-specific operations (e.g., assigning admin roles, retrieving all users)

## Technologies Used

- ASP.NET Core
- gRPC with JSON Transcoding
- Entity Framework Core
- JWT Authentication
- AutoMapper
- FluentValidation

## Getting Started

### Prerequisites

- .NET 6.0 SDK or later
- SQL Server

### Configuration

Update the `appsettings.json` file:
- Set your SQL Server connection string in `ConnectionStrings:DefaultConnection`
- Configure JWT settings in `JwtOptions` (Secret, Issuer, Audience)

### Running the Application

1. Clone the repository
2. Navigate to the project directory
3. Run `dotnet restore`
4. Run `dotnet run`

The service will start at `https://localhost:7000`.

## API Endpoints

The service supports both gRPC and HTTP endpoints. Here are the available endpoints:

| Functionality     | gRPC Method     | HTTP Endpoint               | HTTP Method |
|-------------------|-----------------|-----------------------------|-------------|
| User Registration | RegisterUser    | `/v1/accounts/register`     | POST        |
| User Login        | Login           | `/v1/accounts/login`        | POST        |
| Get User Profile  | GetUser         | `/v1/accounts/email/{email}`| GET         |
| Update User Profile| UpdateUser     | `/v1/accounts`              | PUT         |
| Delete User       | DeleteUser      | `/v1/accounts`              | DELETE      |
| Change Password   | ChangePassword  | `/v1/accounts/change-password`| POST      |
| Assign Admin Role | AssignAdminRole | `/v1/accounts/assign-admin-role`| POST    |
| Get All Users     | GetAllUsers     | `/v1/accounts`               | GET        |
| Get All Admins    | GetAllAdmins    | `/v1/accounts/admins`        | GET        |

## Authentication

The service uses JWT for authentication. Include the JWT token in the `Authorization` header for authenticated endpoints.

## Testing

You can test the API using:
- Postman (for both gRPC and HTTP requests)
- gRPCurl (for gRPC requests)
- Any HTTP client (for RESTful endpoints)

### Example HTTP Request

 - POST https://localhost:7000/v1/accounts/register
 - Content-Type: application/json
 ```json
{
"email": "user@example.com",
"name": "John Doe",
"phoneNumber": "1234567890",
"password": "securePassword123/"
}
```
