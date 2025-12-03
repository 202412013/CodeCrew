ZeroDayCoder – Software Design Commentary


1. How We Improved the Design of the Software

We improved the system design by focusing on modularity, scalability, maintainability, and cleaner architecture.

a. Modular Folder Structure

Split code into clear modules on both frontend and backend.

Backend separated into controllers, routes, middleware, models, utils.

Frontend divided into pages, components, utils, store.
This increases reusability and readability.

b. Better API Design

Introduced RESTful APIs with proper resource naming.

Used correct HTTP methods (GET, POST, PUT, PATCH, DELETE).

Clear route grouping: /user, /problem, /submission, /video, /ai.

c. Consistent UI & Reusable Components

Built reusable React components like AdminPanel, AdminUpload, Editorial, SubmissionHistory.

Maintains consistent styling using Tailwind utility classes.

d. Secure Authentication Layer

Implemented JWT authentication for protected routes.

Added userMiddleware & adminMiddleware to secure endpoints.

e. Improved Error Handling

Standardized API responses with correct status codes.

Added error messages for both user and admin flows.

f. Enhanced Performance

Used axiosClient wrapper → less repeated API code.

Optimized rendering through useEffect, useMemo, and minimal re-renders.

2. Where We Applied Design Principles
a. Single Responsibility Principle (SRP)

Each component/module does only one task:

Controllers only contain business logic.

Routes only define endpoints.

Middleware only handles authentication/authorization.

Models only define schemas.

This makes debugging easier and reduces code complexity.

b. DRY (Don’t Repeat Yourself)

Created axiosClient.js so we don't rewrite axios setup in every component.

Reused components such as ProblemPage, AdminUpdate, AdminDelete.

Centralized validation inside validator.js.

c. Separation of Concerns

Backend handles data & logic,

Frontend handles UI & user interaction.

MongoDB deals with persistent storage.

Clear boundaries make the system scalable.

d. Dependency Injection (Lightweight)

Middleware injects req.result (user data) before controller executes.

Allows controllers to stay clean and independent.

e. REST Design Principles

Resource-based URLs

Uniform responses

Use of proper status codes

Stateless operations

This makes the API predictable and easy to use.

f. Component-Based Architecture (React)

Each UI piece is a separate component.

Components are easy to modify without breaking others.

Ensures clean scalability.

g. Clean Code Principles

Used camelCase, PascalCase, meaningful names, ES6 syntax.

Arrow functions for readability.

Avoided extra complexity.

3. Key Refactoring Done to Improve the Design
a. Extracted Middlewares

Previously, authorization logic was inside controllers.
We refactored it into:

userMiddleware.js

adminMiddleware.js
This reduced duplicate logic and improved structure.

b. Centralized Axios Configuration

Before: Each component used its own axios setup.
After: Created axiosClient.js for all API calls.
→ Less code, consistent headers, easier maintenance.

c. Moved Logic Out of Routes

Routes earlier contained controller logic.
Refactored into:

routes → only endpoint definitions

controllers → business logic
This aligns with MVC-like architecture.

d. Separated Problem, Submission, and Video Logic

Earlier code mixed multiple features into the same file.
Now:

userProblem.js

userSubmission.js

videoSection.js
are fully separated.

e. Reusable Admin Components

Instead of writing different pages for add/update/delete,
we refactored into reusable components:

AdminUpload.jsx

AdminUpdate.jsx

AdminDelete.jsx

AdminVideo.jsx

f. UI Refactoring for Responsiveness

Reduced repetitive CSS.

Used Tailwind responsive classes.

Improved layout with grids and flex.

g. Error Handling Standardization

Before: inconsistent 200/400 errors.
After: uniform responses across all controllers.

4. Summary

The design improvements made the project:

More structured

Easy to scale

Easy to maintain

Cleaner and more professional

Following industry-level patterns

The use of modern design principles and refactoring helped ensure ZeroDayCoder is maintainable and ready for future expansion.
