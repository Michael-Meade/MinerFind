### Orgin Story

I plan on taking the <a href="https://www.comptia.org/certifications/security">Security plus</a> exam, but I wanted an easy way to study. 
 
I have a discord bot named Moss, so I wanted to write a module for the bot that could allow me to practice anywhere I wanted. First I had to find a bunch of questions. That was the hard part. I had to manually add the questions. I wanted to scrape them but I couldn't find an easy way to do that. Instead of working on a lame script to scrape those sites to get the questions, I wanted to work on the fun part of the project. 
Plus after I got the meat of the project done, I would have all the time in the world to figure out a way to scrape the questions and answers. 
  
  
  
### How does it work
  <br>
  The end user starts the quiz by using the following comamnd:
  ```ruby
  !game
  ```
  
After that, the script will call a couple of different classes. First, it will initialize the ```PickQuestion``` class.
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
  
 First, it will read and parse ```quiz.json```. Then it will use ```.to_a``` to turn the JSON file into an array. After that, the code uses the ```.sample``` method to 'randomly' pick from the array. The element picked from the array will be the question that is going to be sent.  The other methods in the class will define other stuff like the results, id, and the answer. 
  

Next, the script will initialize the Points class. Unlike the ```PickQuestion```, the Points class takes some input. First, it needs the user's ID. This is so that the script can keep track of the score of the user. The ```Points``` class looks like the following:


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

After that is done, the update_score method will read and parse the ```quiz_score``` file. It will then use the user's id to get the user's score.
  



### LeaderBoard Command


The code below is the code behind the ```.lb``` command. 
```ruby
out = ""
i   = 0
j    = File.read("quiz_score.json")
json = JSON.parse(j).to_h
json.each do |keys, value|
    user = keys
    out += "#{i}] #{event.user.display_name} #{value}"
    i+=1
end
event.respond(out)
```
First the code empty creates a string named ```out```. This is the string that will be sent to the chat. 
Next it crates a variable named ```i``` with the value of 0.  Next it will read and parse the ```quiz_score``` file. 
Using ```JSON.parse``` turns the score file into an array. That allows us to use ``` each do |key, values|```. It will automatically parse the JSON's file keys and values into two different variables, ``` key ``` and ```values```. 
The keys of the JSON file is all the players Discord user id. Next the code combines, the ```i``` variable, the user's id and the value. Which is the score of the user. After it takes the combined string adds it to the end of the out variable.  Next it will +=1 to the ```i``` variable. After it has looped through all the users, it will send the output to the channel.   
