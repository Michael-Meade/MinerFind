# Setting up the Scoring Sever
<a href="https://www.stuartellis.name/articles/rake/">Rakefiles</a> are a handy tool that can be used to automate tasks. In this case we will use the rakefile to setup the database and to install the needed tools.


# Installing the Gems and Packages
For the following sets of commands to work, it is important that you are in the same directory as ```rakefile.rb```

To install the gems, use the command ```rake install:gems```. This script will assume that none of the gems or sqlite are already installed. 
Running ```rake install:gems``` will also run all the other tasks. The order that the tasks are ran is: 

``` installing the gems => Installing the deps```

Apache2 needs to be installed on the player server, this can be done by the following commands: ```sudo apt-get update; sudo apt-get --assume-yes install apache2```



To create the table, use the command ```rake users```. 

# The files that need to be edited
In order to SSH into the player server, we use the <a href="https://github.com/net-ssh/net-ssh">net-ssh gem</a>.
The net-ssh gem uses password base authentication to SSH into the player server to create a user with the team name.
Edit the following file and change the player server IP & the password: ```sql/db.rb```.
