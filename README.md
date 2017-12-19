1. [Web API](https://docs.microsoft.com/en-us/aspnet/core/tutorials/web-api-vsc#add-support-for-entity-framework-core)
    * mkdir TodoApi
    * cd TodoApi
    * dotnet new webapi

2. [Use SQLite instead of InMemory](https://docs.microsoft.com/en-us/ef/core/get-started/netcore/new-db-sqlite)
    * Startup.cs
    ```
    public void ConfigureServices(IServiceCollection services)
    {   
        services.AddDbContext<TodoContext>(options => options.UseSqlite("Data Source=TodoList.db"));
        services.AddMvc();
    }
    ```
    * Run `dotnet ef migrations add InitialCreate` to scaffold a migration and create the initial set of tables for the model.
    * Run `dotnet ef database update` to apply the new migration to the database. This command creates the database before applying migrations.
        * If you don't do this, you'll get errors like "SQLite Error 1: 'no such table"

3. Go back to tutorial in step 1
    * The Postman demo is wrong. Need the plural noun in the url 'http://localhost:5000/api/todos' NOT 'http://localhost:5000/api/todo'