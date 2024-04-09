# New Repository blazor tutorial

First we need to install .NET SDK in order to use the .NET mark/eviroment/framework
for this u need to follow the steps of installation in the microsoft tutorial .NET
```bash
$ dotnet --version
8.0.203
```

once we have the SDK we need to boost our VSCode by installing C# dev tool kit extension

## Creating a project

In order to create a project we can use the cmd pallet and type `.Net: New project` it will
deploy a list of options with many configurations including the `Blazor web app` one.

But this way sets a lot of folders and files that we don't know so to avoid this many archives
we are going to use a different way to set our `clean` project by doing this on th CLI:

```bash
$ dotnet new --list
These templates matched your input:

Template Name                                 Short Name                  Language    Tags                      
--------------------------------------------  --------------------------  ----------  --------------------------
API Controller                                apicontroller               [C#]        Web/ASP.NET               
ASP.NET Core Empty                            web                         [C#],F#     Web/Empty                 
ASP.NET Core gRPC Service                     grpc                        [C#]        Web/gRPC/API/Service      
ASP.NET Core Web API                          webapi                      [C#],F#     Web/Web API/API/Service   
ASP.NET Core Web API (native AOT)             webapiaot                   [C#]        Web/Web API/API/Service   
ASP.NET Core Web App (Model-View-Controller)  mvc                         [C#],F#     Web/MVC                   
ASP.NET Core Web App (Razor Pages)            webapp,razor                [C#]        Web/MVC/Razor Pages       
Blazor Web App                                blazor                      [C#]        Web/Blazor/WebAssembly    
Blazor WebAssembly Standalone App             blazorwasm                  [C#]        Web/Blazor/WebAssembly/PWA
Class Library                                 classlib                    [C#],F#,VB  Common/Library            
Console App                                   console                     [C#],F#,VB  Common/Console            
dotnet gitignore file                         gitignore,.gitignore                    Config                    
Dotnet local tool manifest file               tool-manifest                           Config                    
EditorConfig file                             editorconfig,.editorconfig              Config                    
global.json file                              globaljson,global.json                  Config                    
MSBuild Directory.Build.props file            buildprops                              MSBuild/props             
MSBuild Directory.Build.targets file          buildtargets                            MSBuild/props             
MSTest Playwright Test Project                mstest-playwright           [C#]        Test/MSTest/Playwright    
MSTest Test Project                           mstest                      [C#],F#,VB  Test/MSTest               
MVC Controller                                mvccontroller               [C#]        Web/ASP.NET               
MVC ViewImports                               viewimports                 [C#]        Web/ASP.NET               
MVC ViewStart                                 viewstart                   [C#]        Web/ASP.NET               
NuGet Config                                  nugetconfig,nuget.config                Config                    
NUnit 3 Test Item                             nunit-test                  [C#],F#,VB  Test/NUnit                
NUnit 3 Test Project                          nunit                       [C#],F#,VB  Test/NUnit                
NUnit Playwright Test Project                 nunit-playwright            [C#]        Test/NUnit/Playwright     
Protocol Buffer File                          proto                                   Web/gRPC                  
Razor Class Library                           razorclasslib               [C#]        Web/Razor/Library         
Razor Component                               razorcomponent              [C#]        Web/ASP.NET               
Razor Page                                    page                        [C#]        Web/ASP.NET               
Razor View                                    view                        [C#]        Web/ASP.NET               
Solution File                                 sln,solution                            Solution                  
Web Config                                    webconfig                               Config                    
Worker Service                                worker                      [C#],F#     Common/Worker/Web         
xUnit Test Project                            xunit                       [C#],F#,VB  Test/xUnit 
```
This command will show us a list of projects that we can create, well let's focus on the blazor one.

```bash
$ dotnet new blazor --help
Blazor Web App (C#)
Author: Microsoft
Description: A project template for creating a Blazor web app that supports both server-side rendering and client interactivity. This template can be used for web apps with rich dynamic user interfaces (UIs).
This template contains technologies from parties other than Microsoft, see https://aka.ms/aspnetcore/8.0-third-party-notices for details.

Usage:
  dotnet new blazor [options] [template options]

Options:
  -n, --name <name>       The name for the output being created. If no name is specified, the name of the output directory is used.
  -o, --output <output>   Location to place the generated output.
  --dry-run               Displays a summary of what would happen if the given command line were run if it would result in a template creation.
  --force                 Forces content to be generated even if it would change existing files.
  --no-update-check       Disables checking for the template package updates when instantiating a template.
  --project <project>     The project that should be used for context evaluation.
  -lang, --language <C#>  Specifies the template language to instantiate.
  --type <project>        Specifies the template type to instantiate.

Template options:
  -f, --framework <net8.0>                 The target framework for the project.
                                           Type: choice
                                             net8.0  Target net8.0
                                           Default: net8.0
  --no-restore                             If specified, skips the automatic restore of the project on create.
                                           Type: bool
                                           Default: false
  --exclude-launch-settings                Whether to exclude launchSettings.json from the generated template.
                                           Type: bool
                                           Default: false
  -int, --interactivity <None|Server|...>  Chooses which interactive render mode to use for interactive components
                                           Type: choice
                                             None         No interactivity (static server rendering only)
                                             Server       Runs on the server
                                             WebAssembly  Runs in the browser using WebAssembly
                                             Auto         Uses Server while downloading WebAssembly assets, then uses WebAssembly
                                           Default: Server
  -e, --empty                              Configures whether to omit sample pages and styling that demonstrate basic usage patterns.
                                           Type: bool
                                           Default: false
  -au, --auth <Individual|None>            The type of authentication to use
                                           Type: choice
                                             None        No authentication
                                             Individual  Individual authentication
                                           Default: None
  -uld, --use-local-db                     Whether to use LocalDB instead of SQLite. This option only applies if --auth Individual is specified.
                                           Type: bool
                                           Default: false
  -ai, --all-interactive                   Configures whether to make every page interactive by applying an interactive render mode at the top 
                                           level. If false, pages will use static server rendering by default, and can be marked interactive on a 
                                           per-page or per-component basis.
                                           Enabled if: (InteractivityPlatform != "None")
                                           Type: bool
                                           Default: false
  --no-https                               Whether to turn off HTTPS. This option only applies if Individual isn't used for --auth.
                                           Type: bool
                                           Default: false
  --use-program-main                       Whether to generate an explicit Program class and Main method instead of top-level statements.
                                           Type: bool
                                           Default: false
```

So now we have this list of things that we don't even have a clue but the key
flags are `--interactivity` that we are goint to set to `None` so we don't
enable any interactivity yet and the flag `--empty` to get the minimum
set of files.

###  Let's take advantage of this flags:

```bash
$ dotnet new blazor --interactivity None --empty -n GameStore.Fromend
The template "Blazor Web App" was created successfully.
This template contains technologies from parties other than Microsoft, see https://aka.ms/aspnetcore/8.0-third-party-notices for details.

Processing post-creation actions...
Restoring /home/nivekyeff/courses/game_store/GameStore.Frontend/GameStore.Frontend.csproj:
  Determining projects to restore...
  Restored /home/nivekyeff/courses/game_store/GameStore.Frontend/GameStore.Frontend.csproj (in 83 ms).
Restore succeeded.

$
```
The explorer now contains the project, let's take a look at at the `Program.cs`


To my understanding the first section of this file imports all the nescesary
components from the Components folder, in the blazor platform, every component needs to be
registered and managed by the app service system in order to be functionaly usable,
with the `AddRazorComponents()`method, by calling this method the builder adds the nescesary
services for the razor components execution, this allows the web app to use the components
efectively during the build process and the execution process.<br>
Then it manages some configurations for the HTTP request pipeline, if the app is not in
delepment mode, it adds a handler of exceptions to manage errors and enables HSTS (HTTP
Strict Transport Security), this idicates the browsers that only HTTPS requests are allowed
<br>
Also:
- It specifies the usage of stactic files like CSS files, images, etcétera
- Adds a protection against cross-site request forgery (CSRF) attacks by        setting an anti-forgery token on application forms.
- It also maps the main component of the app, to be the main UI component
of the application.

> **_Note:_** Feel free to correct my English grammar and understanding.