# Pipeline Concepts

## Overview
Scarif is an user-friendly, easy-to-use pipeline toolset for managing full CG, VFX, realtime or game-projects. 
It can be quickly set up with the bundled installer and fitting presets without needing a TD to help out. 
It's underlying structure is very flexible and can be used for projects of all sizes, 
with many advantages especially noticeable, when used on middle to large scale productions. 
Scarif uses a database-driven backend to store all important project information and supports full asset dependency
 tracking throughout the supported software packages.

It supports the most common digital content creation suites, namely Maya, Houdini and Nuke. If you work on a 
realtime project with a game engine like Unity or Unreal and plan to create your assets in one of said packages,
 Scarif comes with an asset manager to keep your in-game assets always up to date. This holds also true if you are 
 creating a VR experience or using the game engine as primary renderer.

While Scarif is designed to serve the artists, Pipeline TDs and developer will still be able to tweak and enhance 
the pipeline using not only the settings but custom script hooks, which can be tied to various events, including 
the publish process and startup procedures. Scarif supports Windows, Linux and macOS - even in mixed environments. 
The underlying database structure makes interaction with metadata especially fast and independent from the actual 
software which created it. Scarif is designed to work with both, MySQL and SQLite databases. This way projects with
 just one artist can enjoy the simplicity of SQLite databases without the need to run a MySQL server.

Scarif comes with a Hub application which allows artists to browse their tasks and launch their tools. 
Producers will be able to check the progress on assets and shots, set milestones and export spreadsheets. 
Other very helpful features include rule-based shading in Maya, shot assembly for all supported DCCs and 
automatic publish setups.

The name is inspired by a Star Wars planet called Scarif, which the Empire used in Rogue One as a store center for top secret data.


## Feature breakdown
### Asset Dependency Tracking
One of the most powerful features of Scarif is the possibility of asset tracking throughout the pipeline. 
To do that, we system uses so called Asset Nodes. These are simple transforms that sit at the top of 
the asset hierarchy and bundle all their children into their "asset tree". The artist is then able to tag 
these nodes with specific attributes, that define other pipeline behaviors such as the publishing functionality. 
Additionally, on publish, all asset nodes are given a unique ID so they can be tracked in all of the files / caches.
This allows Scarif for example to identify copies of the same asset inside a dressing task and apply the correct shader
based on this information. It also allows for quick introspection into the contents of files, 
as the reference information is stored in the database. This enables other handy features like automatic project
cleanup scripts, which can look up all the asset versions in use and move or delete unused ones to save disc space.

### Publish Concept
Our pipeline is based on the concept of splitting assets into work and publish files to guaranty a stable workflow.
When an artist is done with his task or want to forward the current state of his work to the next department, 
the artist needs create a publish file. This is done by the publish tool. Each department will only use published assets 
from other departments. On publish the artist needs to decide if he wants to import all his references 
before he publishes or if he wants to keep all his references life (this will cause references of references 
later down the line). Scarif also supports multi publishing, which basically means that an artists splits his
publish into several files e.g an animator who works on a shot with three characters has all of them 
in one animation scene but creates a multi publish, so he writes out one file per character as a published version.

### Saving, Loading, Versioning
Scarif comes with a tool for loading, saving and versioning files. Each new version will automatically be written 
into the database by the pipeline tool. This way its easy to keep track of all the files in the project and the
artists don't need to take care of versioning or file paths.

### Asset, Task and Version Information
All major components (assets, tasks, versions) in a project can have extra information associated with it like a state, 
feedback, priority or comments. This is helpful especially for the project management.

### Rendering and Previewing handling
The supported DCCs will have tools included for render submissions and preview generations 
(maya: playblast, houdini: flippbook). They will also create an entry in the database.

### Project Content Browser
Most of the project content like textures, renderings, previews will be available for review in a special browser 
which makes it easy to keep track of this content.

### Naming Convention Independent
The core of Scarif does not rely on any naming conventions as it is based on a database. 
Some of the extra tools may be based on naming conventions e.g the "Create Shading Network from Textures" tool.
It will rely on some special prefixes and suffixes to automatically correctly assemble shading networks 
(see future documentation for the tools).
 
### Local and Server Workspace
Scarif supports to open copy workfiles to the local machine before opening them and automatically pushes 
them back to the server after each version up. Further more artists can decide if they want to write caches to their 
local machine or to the server. Publishing can only be done on the server.

### Asset Variations
Artists can create variations of assets which will coexist under the same task but can still be 
distinguished from each other.

## Workflow and tool examples
The core idea is to divide assets into separate tasks (e.g. modeling, shading, rigging, animation etc.), 
work on it and distribute "public" versions of these tasks (known as publishes) to the other departments. 
Which asset versions are currently available or in use is fully tracked within the Scarif pipeline using a database 
and special asset nodes. This way artists can easily get notified by the pipeline, if an asset they depend on 
has been updated. We provide some general examples on how the workflow should be structured when using Scarif. 
Included are basic and advanced character examples as well as an environment setup. 
Following these guidelines ensures that all tools work as expected and the pipeline structure is maintained.