# CreditWorks-Software-Engineer-Technical-Programming-Assignment
Technical Programming Assignment

Setup & Installation
1. Required Software
.NET SDK (Version 8.0 or compatible)
Visual Studio 2022 or VS Code with C# extensions
SQL Server / SQL Server LocalDB (default for Entity Framework Core)

2. Database Requirements
Ensure your database server instance is running (LocalDB is typically pre-configured with Visual Studio).

3. Configuration Steps
Clone or download the repository to your local computer.
Open the project and locate appsettings.json.

Verify or update the connection string under ConnectionStrings:DefaultConnection to match your local database environment:

JSON
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=VehicleRegistryDb;Trusted_Connection=True;MultipleActiveResultSets=true"
  }
}

4. Database Creation & Migration Instructions
Open your terminal in the project root directory and apply the Entity Framework Core migrations to create the database schema:

dotnet ef database update


5. How to Build the Application
Restore dependencies and compile the solution:
dotnet build

6. How to Run the Application
Start the web server:

dotnet run
Once running, open your browser and navigate to the local URL provided in the terminal (typically https://localhost:5001 or http://localhost:5000).

Overall Solution Architecture
Pattern: Created in accordance with the traditional Model-View-Controller (MVC) architectural pattern offered by ASP.NET Core.

Separation of Concerns:

Models / ViewModels: Represent database objects as well as UI transfer objects.

Services: Business logic, such as evaluation of the weight category, is separated from the controllers and moved into a dedicated service class (CategoryService) for easy unit testing.

Client-Side: Uses jQuery, Bootstrap 5, and DataTables for 


2. Database Design

The relational aspect employed in Entity Framework Core comprises three main tables:

Vehicles: This table preserves separate vehicle records and encompasses parameters like OwnerName, ManufactureYear, Weight, foreign keys that connect with Manufacturer, as well as metadata. 

Manufacturers: This table serves as a reference table containing information about the manufacturer (Id, Name). 

Categories: This table outlines limitations–including parameters like MinWeight and MaxWeight, names, and icons(i.e., IconName), along with styles for badges.


3. Category Calculation Approach
Half-Open Interval Rules: The evaluation of vehicle weight is described with strict numerical limits; the minimum limit includes the weight value but the maximum limit does not.
   
Seamless Mapping: Mapping makes sure that one weight category (such as Light, Medium or Heavy) has one and only weight limit assigned so that weights do not overlap dynamically in the application’s category service layer.
