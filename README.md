# NemakiWare-run
Run NemakiWare as a set of compartmentalized docker images. 

## Prerequisites
In order to run NemakiWare, you will need to build the war files with NemakiWare-builder [NemakiWare-builder](https://github.com/aegif/NemakiWare-builder). 

## Running
A default installation can be run without changing any files but you may find you need to change properties files to suit your environment, for example if you have a remote CouchDB installation then make sure to edit `files/app-server-core.properties` to point to your database, and edit `docker-compose.yml` by commenting out the `nemaki-couchdb` section.

To run, simply issue `docker-compose up` in the root folder for this project.
