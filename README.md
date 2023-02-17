
# The Hero Hire

Find the Right Tech Talent to Fuel Your Business Growth

## Objective

This web application was developed to efficiently assign engineers with the necessary skills to projects. Managers and department heads can register job requests and specify required skills. Engineers can also register and edit their own skills, and staffing agency representatives can use the matching search function to assign appropriate engineers to job requests.

The main concept of this web application is to optimize the matching of engineers' skills with the required skills for job requests. For this purpose, job requests can be registered with detailed skill requirements. Engineers can also continuously manage their skills and track their skill growth.

The value of this web application lies in its ability to easily find engineers with the necessary skills for projects. This enables managers and department heads to efficiently assign engineers, and allows engineers to be assigned to projects that match their skills. Staffing agency representatives can also assign appropriate engineers to job requests and improve customer satisfaction.

## Development Process

It is important to clarify the requirements necessary for designing and developing a web application. These requirements include functional requirements, non-functional requirements, and constraints. The clearer the requirements are, the smoother the development process is likely to progress.

Next, the application is designed, including the data model and application architecture. This includes designing the database, APIs, and screens. The application architecture should be designed carefully, taking into consideration future scalability.

After that, the necessary development environment is set up and the application is implemented. Frameworks like React and Angular are commonly used for front-end development. Technologies like ASP.NET Core, Java, and Node.js are used for back-end development. Databases like MySQL, PostgreSQL, SQL Server, and Oracle are used for data storage.

Once development is complete, the application is tested and any necessary bug fixes are made. Testing includes unit testing, integration testing, and system testing.

Finally, the application is deployed and released. Cloud platforms such as Azure, AWS, and Google Cloud are commonly used for deployment.

These are the general steps for creating a web application. It is important to follow these steps and progress through the project accordingly.


## Requirements Definition

-   Functional Requirements
    
    -   Business Requirements
        -   Site Manager
            -   Function to register, edit and delete projects
            -   Function to register and edit job requirements for projects
            -   Input function for necessary skills for job requirements
            -   Skill input function by skill category, skill name and level
        -   Department Manager
            -   Function to search for matching engineers by skill
            -   Function to assign engineers to job requirements
        -   Staff at Personnel Dispatch Department
            -   Function to register and edit engineering skills of the dispatch company
            -   Function to import engineering skills of the dispatch company
            -   Function to search for matching dispatch company engineering skills by job requirements
            -   Function to assign engineers to job requirements
        -   Engineer
            -   Function to register and edit skills
            -   Function to display skill history
    -   System Requirements
        -   Frontend development using React
        -   Backend development using ASP.NET Core Web API
        -   Use of Azure SQL Database for the database
        -   Use of Azure AD for the login function
        -   Adoption of an architecture that separates the frontend and backend
-   Non-functional Requirements
    
    -   Assumption of around 1000 simultaneous users
    -   Implementation of UI/UX with consideration for usability
    -   Implementation of data encryption and vulnerability diagnosis as security measures
    -   Implementation of logging and monitoring with consideration for operability and maintainability
    -   Development using PaaS is recommended to keep cloud costs down.


## Data Modeling

-   Users: A table representing the application's users and storing information for employees and administrators.
    -   UserID (primary key)
    -   UserName
    -   Email
    -   Password
    -   Role
-   Departments: A table representing departments in the organization and storing the name and description of the department.
    -   DepartmentID (primary key)
    -   DepartmentName
-   Skills: A table representing skills and storing category, skill name, and level.
    -   SkillID (primary key)
    -   Category
    -   SkillName
    -   Level
-   JobRequests: A table representing job requests for projects and storing information such as title, description, priority, start date, end date, and creator ID.
    -   JobRequestID (primary key)
    -   Title
    -   Description
    -   Priority
    -   StartDate
    -   EndDate
    -   CreatorID (foreign key referencing Users.UserID)
-   JobRequestSkills: A table representing the required skills for a job request and linking the JobRequests and Skills tables.
    -   JobRequestID (primary key and foreign key referencing JobRequests.JobRequestID)
    -   SkillID (primary key and foreign key referencing Skills.SkillID)
-   Project: A table representing assigned projects and storing information such as title, description, start date, end date, status, and client ID.
    -   ProjectID (primary key)
    -   Title
    -   Description
    -   StartDate
    -   EndDate
    -   Status
    -   ClientID (foreign key referencing Users.UserID)
-   ProjectMembers: A table linking the Project and Users tables to represent the engineers assigned to a project.
    -   ProjectID (primary key and foreign key referencing Project.ProjectID)
    -   UserID (primary key and foreign key referencing Users.UserID)
-   EmployeeSkills: A table linking the Users and Skills tables to represent the skills held by employees.
    -   UserID (primary key and foreign key referencing Users.UserID)
    -   SkillID (primary key and foreign key referencing Skills.SkillID)
    -   Level
-   VendorEngineer: A table representing engineers belonging to a staffing agency and storing information such as name, email, and phone number.
    -   VendorEngineerID (primary key)
    -   Name
    -   Email
    -   Phone
-   VendorEngineerSkills: A table linking the VendorEngineer and Skills tables to represent the skills held by vendor engineers.
    -   VendorEngineerID (primary key and foreign key referencing VendorEngineer.VendorEngineerID)
    -   SkillID (primary key and foreign key referencing Skills.SkillID)


## Architecture

The architecture consists of two main components: the front-end and the back-end.

Front-end:

-   A single-page application (SPA) developed using React that users access via their web browser.
-   Business logic is executed and the UI is rendered using React components and libraries such as Redux.
-   Security features such as user authentication and authorization are implemented using Azure AD and React components.

Back-end:

-   An ASP.NET Core Web API implemented as a RESTful API.
-   Entity Framework Core is used for database access, communicating with Azure SQL Database.
-   User authentication and authorization are implemented using Azure AD and extended with ASP.NET Core Identity.
-   Middleware from ASP.NET Core is used to handle common tasks such as error handling and logging for all API requests.

Azure:

1.  Front-end: Development of the front-end is done using React.js, which employs a component-based development approach and enables high levels of reuse.
    
2.  Back-end: Development of the back-end is done using ASP.NET Core Web API, which allows for the easy construction of high-performance and robust web APIs, making it well-suited for this application.
    
3.  Authentication: User authentication is performed using Azure Active Directory, which is highly secure and therefore an optimal authentication system for this application.
    
4.  Database: The database is built using Azure SQL Database, which offers high availability, durability, and scalability, making it well-suited for this application.
    
5.  Storage: File storage is implemented using Azure Blob Storage, which offers high durability, availability, and the ability to store large amounts of files, making it an ideal solution for this application.
    
6.  CI/CD: A CI/CD pipeline is built using Azure DevOps, which automates the build, testing, and deployment processes, enabling faster development cycles.
    
7.  Hosting: The web application is hosted using Azure Static Web Apps, which makes it easy to host static web applications, making it well-suited for this application.
    
8.  Other services: Azure services such as Azure Application Insights, Azure Monitor, Azure Key Vault, and Azure Redis Cache can be used in the development of this application. These services help with monitoring the application, managing secret information, and improving performance, among other things.