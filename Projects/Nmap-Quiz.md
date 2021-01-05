
### Orgin Story

I plan on taking the <a href="https://www.comptia.org/certifications/security>Security plus</a> exam, but I wanted a easy way to study. 
  I have a discord bot named Moss, so I wanted to write a module for the bot that could allow me to practice anywhere I wanted. First I had to find a bunch of questions. That was the hard part. I had to manunally add the questions. I wanted to scrape them but I couldnt find a easy way to do that. Instead of wokring on a lame script to scrape those sites to get the questions, I wanted to actually work on the fun part of the project. 
Plus after I got the meat of the project done, I woudl have all the time in the world to figure out a way to scrape the questions and answers. 
  
  
  ### How does it work?
  The end user starts the quiz by using the following comamnd:
  ```ruby
  !game
  ```
  
  After that the script will call a couple of different classes. First it will initialize the ```PickQuestion``` class.
  The PickQuestion class looks like the code below: 
  ```ruby
  class PickQuestion
    		def initialize
    			read     = File.read("quiz.json")
    			@results = JSON.parse(read).to_a.sample.to_a
    		end
    		def results
    			@results
    		end
    		def id
    			@results[0]
    		end
    		def question
    			@results[1][0]
    		end
    		def answer 
    			@results[1][1]
    		end
    	end
  ```
  
  First it will read and parse ```quiz.json```. Then it will use ```.to_a``` to turn the JSON file into an array. After that the code uses the ```.sample``` method to 'randomly' pick from the array. The element picked from the array will be the question that is going to be sent.  The other methods in the class will define other stuff like the results, id and the answer. 
  

Next the script will initialize the Points class. Unlike the the ```PickQuestion```, the Points class takes some input. First it needs the users ID. This is so that the script can keep track of the score of the user. The ```Points``` class looks like the following:


```ruby 
class Points
  def initialize(uid, display_name = nil)
    @uid  = uid
  end
  def uid
      @uid
  end
  def display_name
      @display_name
  end
  def default_score
      "10"
  end
  def create_file
      if(!File.file?('quiz_score.json'))
          File.open("quiz_score.json", "w") { |file| file.write("{}") }
      end
  end
  def update_score
      # create a the score file if it doesnt exist
      create_file
      read = File.read("quiz_score.json")
      j    = JSON.parse(read)
      old_score = j[uid].to_i
      j[uid]    =   old_score += default_score.to_i
      File.open("quiz_score.json", "w") { |file| file.write(JSON.generate(j)) }
  end
end
```

The ```update_score``` method is the main method of the class. This is what is going to be called later. First the ```update_score``` method, calls the create_file method. This method checks to make sure that a file named ```quiz_score.json``` exists. If it does not exist, it will create a file named that and write ```{}``` as its content. 

After that is done, the update_score methdo will read and parse the ```quiz_score``` file. 
  
