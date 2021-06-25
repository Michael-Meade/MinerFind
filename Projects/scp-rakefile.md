---
title:  "scp rakefile"
tags: [ scp, rakefile, ruby ]
---
Rake has this cool feature that allows you to create rakefiles that can do scripts. It can all be done in Ruby. 


It is important that the current directory is the home directory. 
```
mkdir .rake; cd .rake
```

The commands above will first create a hidden directory named .rake. After the directory the command will then tell your system to change directories into the .rake directory. Now create a new file and name it something like scp.rake. 


```ruby
task :scp, [:first, :second] do |t, args|
  c = "scp #{args[:first]} root@.127.0.0.1:#{args[:second]}"
  sh "#{c}"
end
```

The code snippet above is the code that allows the user to easily upload content to their vps. Dont forget to replace the local ip with the IP of your VPS. 

The following command can be used to run the rakefile. 

```
rake scp[the_file_you_Want_to_upload_to_your_vps, he_location_and_name_of_Where_you_want_to_save_it_as]
```
