# mysql
sudo systemctl restart mysql
sudo systemctl restart apache2

# update sdk and runtime
https://devblogs.microsoft.com/dotnet/september-2022-updates/
https://devblogs.microsoft.com/dotnet/april-2023-updates/

Ienumerable -> cann't extend query
IQueryable -> good for use
Lazy loading - avoid in web applications
Visual studio productivity power tools
web essentials
resharper (paid)

controllers 
TblShelfMapLocation (Model)
Add to IRepositoryWrappers -> IShelfMapLocationRepository -> ShelfMapLocationRepository -> RepositoryWrapper
AppDb.cs

dotnet new --list
dotnet new webapi -o projectName

.NET or .NET Core is .NET Framework.
create microservices (boz high-performance)
docker containers
multi-platform support

dotnet tool install --global dotnet-ef
dotnet ef
dotnet new -> dotnet new webapi -o MoviesAPI
dotnet dev-certs https --trust

- omnisharp error slove
https://newbedev.com/omnisharp-msbuild-projectmanager-attempted-to-update-project-that-is-not-loaded

# update vscode
wget 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64' -O /tmp/code_latest_amd64.deb
sudo dpkg -i /tmp/code_latest_amd64.deb


cd /var/dotnet/webapps/citizen_admin
service supervisorctl 
restart dotnet-citizenmobile
tail -n 200 /var/log/dotnet-citizenmobile.err.log

sudo su
supervisorctl
restart dotnet-citizenmobile

dotnet publish
bin/debug/dotnetcore2.1/publish/

TokenProviderMiddleware
InvokeAsync
GenerateToken

AutoMapper (Data Transfer Object with AutoMapper | Object to Object Mapper)
https://www.youtube.com/watch?v=lUGZrrx6fHI
https://www.youtube.com/watch?v=7xQm0EH8S0o
// resueable code
// need nuget automapper extenstion
You must add -> builder.Services.AddAutoMapper()

nHibernate
database <--Mapping--> class
config[db connection string] -> mapping -> session factory. (call AppLevel)
session -> transaction. (call RequestLevel)
...................................

***dotnet 2.1 to 6 (fix errors)***

- optional if you have another sdk versions
dotnet new globaljson --sdk-version 6.0.8

- create .vscode for debug
click -> Create a launch.json file -> .net5 and .net core

- first edit csproj file
<PackageReference Include="Pomelo.EntityFrameworkCore.MySql" Version="6.0.2" />
<PackageReference Include="Microsoft.Extensions.Caching.Abstractions" Version="6.0.0" />
<PackageReference Include="System.IdentityModel.Tokens.Jwt" Version="6.22.1" />
<PackageReference Include="Microsoft.AspNetCore.Authentication.JwtBearer" Version="6.0.8" />
<PackageReference Include="Microsoft.Extensions.Configuration" Version="7.0.0-preview.7.22375.6" />
for BaseDataAccess.cs
<PackageReference Include="MySql.Data" Version="8.0.30" />

- Startup.cs 
services.AddControllers()
            .AddNewtonsoftJson(options => options.SerializerSettings.ContractResolver = new DefaultContractResolver());
<PackageReference Include="Microsoft.AspNetCore.Mvc.NewtonsoftJson" Version="6.0.8" />

startup.cs -> enable routing 
https://stackoverflow.com/questions/57684093/using-usemvc-to-configure-mvc-is-not-supported-while-using-endpoint-routing
https://stackoverflow.com/questions/58266344/net-core-3-mvc-using-usemvcwithdefaultroute-to-configure-mvc-is-not-suppo
services.AddControllers(option => option.EnableEndpointRouting = false);

Startup.cs
ASP.NET Core : Synchronous operations are disallowed
Exception thrown: 'System.InvalidOperationException' in Microsoft.AspNetCore.Server.Kestrel.Core.dll
https://stackoverflow.com/questions/47735133/asp-net-core-synchronous-operations-are-disallowed-call-writeasync-or-set-all
// If using Kestrel:
    services.Configure<KestrelServerOptions>(options =>
    {
        options.AllowSynchronousIO = true;
    });

    // If using IIS:
    services.Configure<IISServerOptions>(options =>
    {
        options.AllowSynchronousIO = true;
    });
    
serviceExtensions.cs
https://www.anycodings.com/questions/cannot-convert-from-string-to-microsoftentityframeworkcoreserverversion
services.AddDbContext<AppDb>(o => o.UseMySql(connectionString, new MySqlServerVersion(new Version())));

serviceExtensions.cs -> cors allow
https://www.syncfusion.com/faq/error-handling/how-do-you-fix-the-cors-protocol-does-not-allow-specifying-a-wildcard-any-origin-and-credentials-at-the-same-time-error-in-blazor-server-application
options.AddPolicy("Open", builder =>
                builder.SetIsOriginAllowed(_ => true).
                AllowAnyMethod().
                //AllowAnyOrigin().
                AllowAnyHeader().
                AllowCredentials());

OAuthTokenHandler.cs
you get wrong path if you aren't edit this
https://www.faqcode4u.com/faq/77189/aspnet-core-jwt-bearer-token-custom-validation

- Disable warning
https://docs.microsoft.com/en-us/dotnet/fundamentals/syslib-diagnostics/syslib0021
https://docs.microsoft.com/en-us/dotnet/fundamentals/syslib-diagnostics/syslib0022

- sql lite
https://stackoverflow.com/questions/69472240/asp-net-6-identity-sqlite-services-adddbcontext-how
work 
https://www.tektutorialshub.com/entity-framework-core/ef-core-console-application/

- Migrations
dotnet ef migrations add InitialCreate
dotnet ef database update
dotnet ef migrations add InitialCreate -IgnoreChanges -Force




