# Get Started
Here you will find some instructions on how to setup Scarif for your first project and a short overview of
the dcc workflow.

## Setup Scarif
To use Scarif in your project you have to download and install it for each machine.
> [Install Instructions](./02_installation.md)

After installation you can start to create a new project. To have others join the same project, they
need to have access to the project directory which you specify during project setup.
> [Project Manager](./04_projectsetup.md)

Now you can start to add users to you project to assemble a team.
> [User Manager](./05_usersetup.md)

Next you can start linking your dcc applications (Maya, Houdini, Nuke, etc.) to the project and create custom configurations
for them as needed. To do so you will also need to add some extra packages to scarif depending on the dcc.

> [Application Manager](./06_applicationsetup.md) & [Package Manager](./09_packages.md)


You can add more project content locations then the one specified during the project setup.
> [Location Manager](./07_locationsetup.md)

Now you should have everything up and running. All the configuratiosn you just created are stored in the database
and will be distibuted to other teammembers as soon as they have added the project in scarif.

## DCC Workflow
When using Scarif as your pipeline tool most of the digital content you create will go through the pipeline.
Each of the dcc's Scarif supports will come with some form of a Scarif "Save", "Load" and "Publish" tool. 
This ensures that everything you create will be registered and available for all applications.

Scarif helps you to structure your digital content like assets and shots. You will not need to worry where
to save, load or export data to but use the Scarif user interface inside the DCC applications to do so.

> More infos: [Pipeline Concepts](./01_pipelineconcept.md) 

##### Digital Content:
Digital content is separated into different layers:
- Categories
- Assets
- Shots
- Tasks (Of a specific TaskType)
- Variants
- Versions
- Files (Of a specific FileType)

All the file naming will be done automatically by some default template which you can customize if needed.

##### Assets / Shots
Each asset and shot is divided into different tasks. Fot example asset R2D2 can consists of the tasks: modeling, texturing, shading, riggig
and a shot 0050 where R2D2 is smashing some droids can be made up of tasks like: animation, lighting, compositing.

For bigger projects it makes sense to structure your assets and shots into categories.

##### Workflow
Scarif differentiates between work and publish files. Work files are used to for each task to get the work done and when 
the result should be available to the next department a publish file is generated which can be referenced in other departments.

As a rule of thumb:  Worlk file -> Publish -> Reference to other departments

> In-depth: [Technical Guide](./10_technicalguide.md) 