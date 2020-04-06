# NemakiWare-run
Run NemakiWare as a set of compartmentalized docker images. 

## Prerequisites
In order to run NemakiWare, you will need to build the war files with NemakiWare-builder [NemakiWare-builder](https://github.com/aegif/NemakiWare-builder). An example is included and can be run with `docker-compose up` in the build folder of this project. This builds the entire environment for NemakiWare and then creates the war files necessary to run NemakiWare ui/solr/core. Total build time for first run will take a long time - about an hour. 

## Running
A default installation can be run without changing any files, however you may find you need to change properties files to suit your environment - for example if you have a remote CouchDB installation then make sure to edit `files/app-server-core.properties` to point to your database, and edit `docker-compose.yml` by commenting out the `nemaki-couchdb` section.

To run NemakiWare, simply issue `docker-compose up` in the run folder for this project.
