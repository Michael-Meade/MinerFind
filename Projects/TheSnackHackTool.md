### The idea behind the name
There are many different types of snacks, they come in all types: crunchy, soft, sugarly, natural. This tool does not have one single purpose.
How it works is that there is a 'plugin' or modular like system that a user could create a module to add a certain functionality to the project. This makes it easy for new features to be added to the tool without having mess with the main part of the code. 

The end user can choose what modular they want to run, or run a bunch of them together. The tool will save the results of the scan 
as reports.  The formats that it currently supports is JSON & TXT files. 


### Senior Project
This tool is also being created for my Senior Projects. My senior Project is to create a standard that could be 
used by web site administrators to limit the amount of inforamtion that could be used by attackers to exploit or attack the 
site. It is stil in the working but it will set up a bunch of guidelines like: 
- Remove the server header in the requests
- Check for SSRF
- Check  & remove any  default pages ( server-info, server-status, etc )
- Makes sure that there is not any sensitive inforamtion that is exposed in the robots.txt file



### Source code
The code for the project can be found <a href="https://github.com/Michael-Meade/snack_hack">here</a>


### Robots.txt Modules
```ruby
require './lib/reports'
require 'excon'
module SnackHack
    module RobotsScore
        def self.run(url)
            results  = []
            response = Excon.get(File.join(url, "robots.txt"))
            text     = response.body
            contents = text.split("\n").each { |c|  }.to_a
            contents.each do |l|
                # makes sure that the line has the 
                # string "Disallow:" in it
                if l.include?("Disallow:")
                    #  remove any empty elements that are empty
                    deny =  l.split("Disallow: ").reject { |r| r.empty? }
                    # makes sure that its not already in the array.
                    if !results.include?(deny)
                        # if is not found in the array
                        # it will add it to the results array
                        results += deny
                    end
                end
            end
            # saves the results into the file named robots_score.txt
            Reports.new(url, results.join("\n"), "robots_score.txt").save_txt
            score = 0
            new_url = url.to_s.gsub("https://", "").gsub("http://", "")
            File.readlines(File.join("reports", new_url, "robots_score.txt")).each do |l|
                l = l.strip
                response = Excon.get(File.join(url, l))
                if response.status.to_i == 200
                    score+=1
                end
            end
            Scoring.new(score, File.join("reports", new_url, "robots_score.txt")).calc
        end
    end
end
```
The code snippet above shows the robots.txt module that will be used to give the site a score based the items in the Robots.txt file and if the denied items are accessible. The first thing that the script does is visit the robots.txt file and save the response as the variable text. The next line will convert the text variable into an array and starts a block to loop through the contents. Next it will check to see if the element includes the text "Disallow". If it does include "Disallow it will then remove any empty elements and split the element so that only the URL path of the disallow item will present. Now it will double check to make sure that the URL  path is not already in the array named results. If it is not in the array named `results` it will append the URL path to the array. 

Next the code wil save the results array in a file named robots_score.txt. Each time a IP or domain is ran the code will automatically create a new directory with the name of the site. This is where it will save the robots_score.txt file. We next create a variable named score with the value of `0`.  Since URLS contain backslashes and other text that is not allowed to be in file names, we have to use Ruby's gsub method to remove any characters that are not allowed. Next we use Ruby's File.readlines method to loop through the robots_score.txt file line by line. First we have to use the strip method to remove any newlines or "\r". Now the code will visit take the URL and the path of the URL that was found in the robots.txt file and use the File.join method to create a valid URL. The code will visit the URL and check to see what status code the server sent back. If the server responds with a 200 status code then the code will += the score variable. 

The last thing that the code will do is calculate the score by adding the total of the items in the robots.txt file and then divide the results by the score of valid web paths. 


### Default Pages Module
```ruby
require 'excon'
require './lib/utils'
module SnackHack
    module DefaultPages
        def self.scanning_file
            File.join("lists", "default_status.txt")
        end
        def self.run(url)
            score = 0
            File.readlines(self.scanning_file).each do |path|
                response = Excon.get(File.join("https://", url, path.strip))
                content  = response.body
                # first we should check to make sure that the server gave us a 200 status code back
                if response.status.to_i == 200
                    score += 1
                    puts "Detected default status page at :#{File.join(url, path.strip)}"
                    Reports.new(url, path, "default_status_pages.txt" ).save_txt
                end
            end
        Scoring.new(score, File.join("lists", "default_status.txt")).calc
        end
    end
end
```
