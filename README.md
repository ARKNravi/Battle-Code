This is a backend API for managing user registration, authentication, profiles, and educational materials. It provides functionality for user registration, login, profile management, and CRUD operations on educational materials. The API uses **Express.js** for routing, **Supabase** for database interaction, and **JWT** for authentication.

## Project Structure

```
C:.
│   .env
│   .gitattributes
│   .gitignore
│   index.js
│   LICENSE
│   package-lock.json
│   package.json
│   test.js
│   vercel.json
│
├───handler
│       materiHandler.js        // Handler for materi-related requests
│       profileHandler.js       // Handler for profile-related requests
│       registerHandler.js      // Handler for registration-related requests
│
├───middleware
│       adminMiddleware.js      // Middleware for checking admin rights
│       authMiddleware.js       // Middleware for authentication
│
├───repository
│       materiRepository.js     // Repository for materi data operations
│       profileRepository.js    // Repository for profile data operations
│       registerRepository.js   // Repository for user registration operations
│
├───routes
│       materiRoutes.js         // Routes for materi-related API endpoints
│       profileRoutes.js        // Routes for profile-related API endpoints
│       registerRoutes.js       // Routes for registration-related API endpoints
│
└───utils
        supabase.js            // Utility to interact with Supabase
```

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/ARKNravi/htmlcssbattle.git
    cd htmlcssbattle
    ```

2. Install the dependencies:
    ```bash
    npm install
    ```

3. Create a `.env` file in the root directory and set the following environment variables:
    ```
    SUPABASE_URL=your-supabase-url
    SUPABASE_ANON_KEY=your-supabase-anon-key
    ```

## API Endpoints

### Authentication & User Management

- **POST /register**  
  Registers a new user.
  - Body: `{ "email": "user@example.com", "password": "password123" }`

- **POST /login**  
  Logs in an existing user and returns a JWT token.
  - Body: `{ "email": "user@example.com", "password": "password123" }`

- **PUT /profile**  
  Updates the user profile.
  - Body: `{ "name": "User Name", "age": 25, "address": "Address" }`

- **POST /reset_password**  
  Resets the user's password.
  - Body: `{ "email": "user@example.com" }`

- **GET /profile**  
  Retrieves the authenticated user's profile.

- **DELETE /profile**  
  Deletes the user's profile.

### Materi (Educational Material) Management

- **POST /materi**  
  Creates a new educational material (requires authentication).
  - Body: `{ "title": "Materi Title", "description": "Materi Description", "jenis_materi": "Type" }`

- **GET /materi**  
  Retrieves all educational materials.

- **GET /materi/:id**  
  Retrieves a specific educational material by ID.

- **GET /materi/search/:jenis_materi**  
  Searches educational materials by type.

- **DELETE /materi/:id**  
  Deletes an educational material by ID (requires admin authentication).

- **PUT /cover_photo/:id**  
  Updates the cover photo for an educational material (requires authentication).
  - Form-data: `foto_cover` (file upload)

## Middleware

- **authMiddleware**: Ensures the user is authenticated via JWT.
- **adminMiddleware**: Checks if the user has admin rights for certain operations like deleting materi.

## Utilities

- **supabase.js**: Handles the connection to the Supabase database.

## Dependencies

- `express`: Web framework for building the API.
- `cors`: Middleware for enabling Cross-Origin Resource Sharing.
- `multer`: Middleware for handling file uploads.
- `jsonwebtoken`: For generating and verifying JWT tokens.
- `bcrypt`: For hashing passwords.
- `pg`: PostgreSQL client for Supabase integration.
- `dotenv`: For managing environment variables.
- `uuid`: For generating unique identifiers.
- `validator`: For validating input data.

## Running the Application

1. To start the application in development mode (with hot-reloading):
    ```bash
    npm run dev
    ```

2. To start the application in production mode:
    ```bash
    npm start
    ```

3. The API will be available at [http://localhost:3000](http://localhost:3000).

## License

This project is licensed under the [MIT License](LICENSE).

---
