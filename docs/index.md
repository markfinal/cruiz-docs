# Welcome to cruiz

cruiz stands for Conan Recipe User Interface.

At this time, Conan 1.x is supported.

## Goals
The goals of cruiz are as follows:

* Responsive UI
> multiprocessing is used for each Conan command to separate UI and asynchronous workers.

* Managing local caches
> Local caches are named, associated with recipes, and deals with Conan environment variables.

* Visualisation of dependencies
> Visualisation of the package dependency graph using GraphViz and SVG.

* Ease Conan learning curve
> Reduce the learning curve on Conan specifics.

* Alternative remote package inspection
> Something different to Artifactory's web interface but on the client side. Improvements such as syntax highlighted file viewing.

## Recipes are first class citizens
Conan recipe files (conanfile.py/conanfile.txt) are the primary files that cruiz will open.

Use File->Open... to open a recipe into the UI. A wizard will be shown to guide the loading process for any recipe unknown to cruiz. Version agnostic recipes are supported, and the associated conandata.yml is parsed to determine the versions available.

Multiple recipes can be loaded.

## Manage local caches
Conan supports local caches in different locations. Working with different projects may require a different local cache for each. This can be done with environment variables.

cruiz offers a mechanism to associate a recipe file with a named local cache. This binding is kept in preferences. It is recallable if a recipe is reloaded, and also changed if so desired.

Use Edit->Manage local caches... to manage the named local caches. A wizard will guide you through the steps when creating a new named local cache.

## Remote browser
The Artifactory web UI and the Conan CLI are the common ways to browse and search for packages on a remote of an Artifactory server. cruiz offers an alternative viewer, with an interactive package reference search leading to recipe revisions, package_ids, package revisions, and finally a browser over package tarballs themselves. Revisions are only shown when that feature is enabled.

The remote browser is a dock made visible via the View->Conan remote browser menu option.

## Preferences
Many features of cruiz can be configured via the preferences. Features are logically grouped to make finding what you want easier. Most settings can be applied while the dialog remains open; a few require restarting the application.

Use Edit->Preferences... to open the preferences dialog.

## Recipe tabs
Each recipe loaded into cruiz is displayed as a tab in the UI. Each tab widget is split into several sections by default:

1. menu
2. toolbars along the top
3. a dock to the left, showing the dependencies of the recipe and a visualisation of them
4. a dock to the right, split between configuration of the recipe and local workflow options
5. a dock to the bottom, split between a history of Conan commands run on the recipe, and the Conan log stream

### Menus
#### Recipe menu
This menu offers options to interact with the recipe, and the local cache it is associated with.

#### Command menu
This menu offers all of the Conan (and other) commands that are on the toolbars.

### Toolbars
#### Profile
A combobox offering all of the profiles in the associated local cache.
#### Cores
A spinbox offering a way to change the number of cores that Conan commands will use.
#### Commands
Toolbar icons for each Conan and other commands that can be executed on the recipe. Tooltips contain the exact command to be executed on the command line, and will update with changes to the configuration of the recipe.

### Dependencies dock
This is a representation of a Conan lock file for the recipe in its selected configuration.
This displays a flat list of the dependencies found and a graphical representation, if graphviz has been configured. Double clicking on the small visualisation opens a separate dialog showing it full size, with an option to save as an SVG.

### Configuration dock
Split into three sections, it shows:

1. the package_id computed from the lockfile
2. all of the options in the recipe, showing all possible values to choose from for each
3. the package reference namespace, @user/channel, to use for the recipe

Modifying any input data to the lockfile generation will recompute the package_id.

### Local workflow dock
Split into several sections, this allows the definition of paths used in Conan local workflows.

### Conan command dock
Whenever a command is executed on a recipe, it is recorded in the command log. This is intended both as a learning mechanism by seeing what changes by modifying a recipe's configuration, but also as a reproducible mechanism as right clicking over a command allows exporting it to different shells.

### Conan log dock
Running Conan commands captures logging from Conan itself, which is displayed in this dock. This is for diagnostic purposes only really.
