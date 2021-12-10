# Badges & Input Badges README

You must develop anything on top of the `main` branch, then update feature/input-badges where the build process is tweaked to bundle the new components independently.

## Extend

Steps to extend the components:

* Fetch upstream
* Fix possible conflicts
* Develop - fix - improve
* Write specific documentation if necessary in Boostrap way, so you can see it as if it were part of the official documentation
* Run the test to make sure you haven't broken anything
* Merge main into `feature/input-badges` branch
* Write new documentation if necessary at `/docs` (gh-pages)

## Distribute

* Archive previous version by changing the file names
* Update the documentation specifying the new names for the older version
* Execute `badges-bundle` npm commmand
* Use this service to distribute the new components https://gitcdn.link/ using the bundle files raw URL

The files without version in their names are the latest developed on top of `main`.
