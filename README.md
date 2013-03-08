# MapStory GeoServer Dependency Repo

This repo contains submodule references to all the parts of the MapStory 
GeoServer dependency chain, namely:

* GeoTools
* GeoWebCache
* GeoServer
* GeoServer Extensions

## Building

The `build.xml` file is used to build the dependency chain. To build all the 
projects simply run the `ant command:

    ant

Projcets can be built individualy as well:

    ant build-gt
    ant build-gwc
    ant build-gs
    ant build-gs-exts

## Deploying

To deploy all projects:

    ant deploy-all

Or individually:

    ant deploy-gt
    ant deploy-gwc
    ant deploy-gs
    ant deploy-gs-exts

The deployment uses a custom `settings.xml` file, described in the next section, to deploy to the [MapStory maven repository](http://mapstory.repo.opengeo.org).

## Custom Maven Settings

This repo contains a custom `settings.xml` file that does three things:

1. Turns off snapshots from the main OpenGeo maven repository
1. Overrides distribution management for upstream projects
1. Specifies credentials for the MapStory maven repository

## Updating Dependencies

As mentioned previously dependencies are managed with submodule references. 
Updating a dependency involves the following procedure:

1. First ensure a clean checkout with all submodules up to date

        git submodule update --init --recursive

1. Change directory to the submodule to be updated

        cd geoserver

1. Checkout the new revision to reference

        git checkout 2.2.x
        git pull origin 2.2.x

1. Change back to the root of the repository and add/commit the changes

        cd ..
        git add geoserver
        git commit -m "updating geoserver dependency"

