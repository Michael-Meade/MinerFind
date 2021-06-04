### What is the looker?
The looker is a tool that is able to extract information out of non compiled scripts. It might work with compiled 
programs too if the author did not remove the strings. The story of this project that I would search  <a href="https://www.hybrid-analysis.com/">Hybrid-analysis</a> for non compiled samples like 
vbs, sh, py, perl. This is where I found most of the samples that I have written about. At first I was doing it manually. Most the samples also downloaded other files and did stuff with them, so I woudld have
a bunch of tabs open in Sublime. A bunch of different directories and files. It was starting to get a mess and becoming hard to go back to the task after taking a break. 

I thought to myself that there has to be a way to automate the proccess. The looker is the product of that idea. 

Each functionality has different class. This is so that the person running the program can decide what functionality they want to use on the sample. It would
also make it easier to add functionality to the program later without making a mess. 



The orginal post about this project can be found <a href="https://michael-meade.github.io/Projects/The-Looker.html">here</a>

### Running main.rb
```ruby
ruby main.rb d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh
```
This will create a new directory in the output directory. It will create a new directory named `d9f0ed1533f2727254d2e1c63c087147c84e054678d958f6317e8bfd499cfe9e.sh`.
All the data and files that was extracted from the sample will be stored here.
