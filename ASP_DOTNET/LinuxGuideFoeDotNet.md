Install DotNet To Linux Deb

    1. Get Packages
        Run following command to get required packages

        wget https://packages.microsoft.com/config/ubuntu/21.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
        sudo dpkg -i packages-microsoft-prod.deb
        rm packages-microsoft-prod.deb

    2. Install SDK
        Run following command to install sdk

        sudo apt-get update
        sudo apt-get install -y apt-transport-https
        sudo apt-get update
        sudo apt-get install -y dotnet-sdk-6.0

    3. Install Runtime
        Run following command to install runtime version 6.0

        sudo apt-get install -y dotnet-runtime-6.0

    4. Check install status useing command
        dotnet --version

Install Entity Framework for Database and Database connectivity

    dotnet tool install --global dotnet-ef

Create New dotnet MVC Project with C#

    mkdir NewDotnetProject
    cd NewDotnetProject

    dotnet new mvc -n 'putProjectNameHere' -lang 'C#' -au none;

        {-lang:- defines programing language
        -n:- defines name of project
        -au:- authentication }



    Add Following packages to access Sqlite and EntityFrameworkCore


        dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore --version 5.0.1
        dotnet add package Microsoft.EntityFrameworkCore.Sqlite --version 5.0.1
        dotnet add package Microsoft.EntityFrameworkCore.Tools --version 5.0.1
        dotnet add package Microsoft.AspNetCore.Identity.Dignostics.EntityFrameworkCore --version 5.0.1


        dotnet add package Pomelo.EntityFrameworkCore.MySql --version 6.0.1
        dotnet add package Pomelo.EntityFrameworkCore.MySql.NetTopologySuite --version 6.0.1


    update appsettins.jason file to include connection to our DB

        "ConnectionString":{
          "DefaultConnection": "DataSource=app.db;Cache=Shared"
        }


    Run Following Command
    dotnet build
    dotnet run

Create Application Database Context

    mkdir Data
    cd Data
    touch ApplicationDbContext.cs

    '''
        using Microsoft.EntityFrameworkCore;

        namspace ApplicationDbContext.Data{
            public class ApplicationDbContext: DbConnect{
                public ApplicationDbContext(DbContextOptions<ApplicationDbContext>options)
                :base(options){

                }
            }
        }

    '''


    update Starup.cs file
        In ConfigurServices class add following code

        services.AddDbContext<ApplicationDbContext>(
            options => options.UseSqlite(
                Configuration.GetConnectionString("DefaultConnection")
            )
        );
        services.AddDatabaseDeveloperPageExceptionFilter();


    Add initial migration

        dotnet ef migrations add "Inital Migrations"
        dotnet ef database update
