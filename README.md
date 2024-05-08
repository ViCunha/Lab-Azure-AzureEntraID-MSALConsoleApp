
### Overview
---
In this exercise, you learn how to perform the following actions:

- Register an application with the Microsoft Identity platform
- Use the PublicClientApplicationBuilder class in MSAL.NET
- Acquire a token interactively in a console application

   
### Key Aspects
---
- Microsoft Authentication Library

### Environment
---
Microsoft Azure Portal
- Valid subscription

Integrated Development Environment (IDE)
- Visual Studio Community 2022 or Visual Studio Code (with C# extension)

Framework
- DNET 8 or greater

### Actions
---

Prepare the environment

- Sign in to the portal: https://portal.azure.com

- Open the Microsoft Entra ID instance

- Under Manage, select App registrations > New registration

- When the Register an application page appears, enter your application's registration information

  - Name: az204appreg

  - Supported account types: Select Accounts in this organizational directory only

  - Redirect URI (optional): Select Public client/native (mobile & desktop) and enter http://localhost in the box to the right.

- Select Register

Configure and code the console application

- Create the project folder
```
md Lab-Azure-AzureEntraID-MSALConsoleApp
cd Lab-Azure-AzureEntraID-MSALConsoleApp
```

- Open the Visual Studio Code using the project folder as the base
```
code .
```

- In the Visual Studio Code, open the terminal window

- Create the new directory az204-auth
```
md az204-auth
cd az204-auth
```

- Create the .NET console app
```
dotnet new console
```

- Add packages and use statements
```
dotnet add package Microsoft.Identity.Client
```

- The Program.cs must have the code below
```
using System;
using System.Threading.Tasks;
using Microsoft.Identity.Client;

namespace az204_auth
{
    class Program
    {
        private const string _clientId = "APPLICATION_CLIENT_ID";
        private const string _tenantId = "DIRECTORY_TENANT_ID";

        public static async Task Main(string[] args)
        {
            var app = PublicClientApplicationBuilder
                .Create(_clientId)
                .WithAuthority(AzureCloudInstance.AzurePublic, _tenantId)
                .WithRedirectUri("http://localhost")
                .Build(); 
            string[] scopes = { "user.read" };
            AuthenticationResult result = await app.AcquireTokenInteractive(scopes).ExecuteAsync();

            Console.WriteLine($"Token:\t{result.AccessToken}");
        }
    }
}
```

- Compile the project
```
dotnet build
```

- Execute the project
```
dotnet run
```

### Media
---
![image](https://github.com/ViCunha/Lab-Azure-AzureEntraID-MSALConsoleApp/assets/65992033/fcc34f09-40ec-4bde-b183-e80691bcab0f)

---
![image](https://github.com/ViCunha/Lab-Azure-AzureEntraID-MSALConsoleApp/assets/65992033/45b46552-5eb2-4ae3-ab5c-6f8f41dc947e)

---
![image](https://github.com/ViCunha/Lab-Azure-AzureEntraID-MSALConsoleApp/assets/65992033/425a6459-a9ef-41af-8e41-b165f9c3d258)


### References
---
- [Bacon ipsum dolor](https://#)
