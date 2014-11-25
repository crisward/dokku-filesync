#Dokku Filesync

Simple plugin to allow the syncing of files in two docker containers.
This works by pipe tared files into a shared volume held in the apps folder.
This is a bit specific, but the principle could be extended to be more adaptable.

##Installing

    cd /var/lib/dokku/plugins/
    git clone https://github.com/crisward/dokku-filesync.git


##Basic Usage

###Sync files between containers

    ssh dokku@server1.com sync:down yourapp | ssh dokku@server2.com sync:up yourapp

###Upload a local directory

    cd /your-dir
    tar cfm - ./* | ssh dokku@server2.com sync:up yourapp

###Download to a local directory

    cd /your-dir
    ssh dokku@server2.com sync:down yourapp | tar xfvm - -C . 
