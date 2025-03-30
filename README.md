# BENR3433-VMS

## Overview

BENR3433-VMS is a Visitor Management System (VMS) built using Node.js, Express, and MongoDB. It provides a RESTful API for managing visitors, hosts, and security personnel in a condominium or similar environment. The system includes features such as user authentication, role-based access control, visitor registration, and logging.

## Features

- **Authentication**: Secure login for Admins, Hosts, and Security personnel using JWT.
- **Role-Based Access Control**: Different roles (Admin, Host, Security) with specific permissions.
- **Visitor Management**: Register, view, and delete visitors.
- **Host Management**: Register and view hosts.
- **Security Features**: Password complexity validation and account lockout after multiple failed login attempts.
- **Swagger API Documentation**: Interactive API documentation available at `/api-docs`.

## Project Structure

```
BENR3433-VMS/
├── .gitignore
├── client.http
├── index.js
├── package.json
├── README.md
├── .github/
│   └── workflows/
│       └── main_fakhrul-vms.yml
```

### Key Files

- **`index.js`**: Main application file containing API routes and business logic.
- **`client.http`**: HTTP client file for testing API endpoints.
- **`.github/workflows/main_fakhrul-vms.yml`**: GitHub Actions workflow for CI/CD deployment to Azure Web App.
- **`package.json`**: Project dependencies and scripts.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/benr3433-vms.git
   cd benr3433-vms
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up MongoDB:
   - Update the MongoDB connection URI in `index.js`:
     ```js
     const uri = "your-mongodb-connection-string";
     ```

4. Start the server:
   ```bash
   node index.js
   ```

5. Access the API at `http://localhost:3000`.

## API Endpoints

### Authentication

- **Login as Host**: `POST /loginHost`
- **Login as Security**: `POST /loginSecurity`
- **Login as Admin**: `POST /loginAdmin`

### Visitor Management

- **Register Visitor**: `POST /issuepassVisitor`
- **View Visitor**: `POST /viewVisitor`
- **Delete Visitor**: `DELETE /deleteVisitor`

### Host Management

- **Register Host**: `POST /registerHost`
- **View Hosts**: `POST /viewHost`

### Admin Management

- **Manage User Role**: `POST /manageRole`

### Security Features

- **Retrieve Host Contact**: `POST /retrieveHostContact`

### Swagger Documentation

Access the Swagger API documentation at:
```
http://localhost:3000/api-docs
```

## Testing

Use the `client.http` file to test the API endpoints. You can use an HTTP client like [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) in Visual Studio Code.

## Deployment

This project is configured for deployment to Azure Web App using GitHub Actions. The workflow file is located at `.github/workflows/main_fakhrul-vms.yml`.

### Steps to Deploy

1. Set up Azure Web App and obtain the following secrets:
   - `AZUREAPPSERVICE_CLIENTID`
   - `AZUREAPPSERVICE_TENANTID`
   - `AZUREAPPSERVICE_SUBSCRIPTIONID`

2. Add these secrets to your GitHub repository under **Settings > Secrets and variables > Actions**.

3. Push changes to the `main` branch to trigger the deployment workflow.

## Dependencies

- [Express](https://expressjs.com/) - Web framework for Node.js.
- [MongoDB](https://www.mongodb.com/) - NoSQL database.
- [bcrypt](https://www.npmjs.com/package/bcrypt) - Password hashing.
- [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) - JWT authentication.
- [swagger-jsdoc](https://www.npmjs.com/package/swagger-jsdoc) - Swagger documentation generator.
- [swagger-ui-express](https://www.npmjs.com/package/swagger-ui-express) - Swagger UI for API documentation.

## Security

- Passwords are hashed using bcrypt.
- JWT is used for secure authentication.
- Password complexity is enforced.
- Accounts are locked after multiple failed login attempts.

## License

This project is licensed under the ISC License. See the [LICENSE](LICENSE) file for details.
