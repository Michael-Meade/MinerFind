# Setting up the Scoring Sever
<a href="https://www.stuartellis.name/articles/rake/">Rakefiles</a> are a handy tool that can be used to automate tasks. In this case we will use the rakefile to setup the database and to install the needed tools.


# Installing the Gems and Packages
For the following sets of commands to work, it is important that you are in the same directory as ```rakefile.rb```
To install the gems and packages, use the command ```rake install```. This script will assume that none of the gems or sqlite are already installed. 

To create the table, use the command ```rake users```. 


