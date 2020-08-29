# About

This is probally my third or so time attempting to code a Cowrie log scraper. But this time is different because I experimented with design patterns.
Design patterns purpose is to make the code more organized. Which makes it easier to fix problems and add more features.

# What I learned
The whole idea of the 'get_links' method was to create an array of all the URLs that were accessed. "h" is the array I created to store all the urls. 
Arrays are usually in the following format. [ "1". "2", "3". "4", "5" ]. The value between each of the " " is called an element. 
I wanted to make sure that there were not duplicates of the same element. 

![Original code](https://i.imgur.com/cC6BbkJ.png | width=100)
Instead of having the code above which uses Ruby's 'include?' method to check to see if the the URL is not one of the arrays elements. The include? method will return true if the supplied string is an element. If it does not contain the supplied string it will return false. I used the ! operator to tell it if it [b]does not contain[/b] the supplied string to do the next step, which is to add the URL to the array. I used the << operator which will append it to the array.  But doing this way was kinda buggy and chunky. I wanted to improve on it. I was bored one day coding and was just looking at the code to decide what I should add next. It came to me there
that coding is like writting an essay for school. You have to give it a look over and proof read the code. When coding something I usually have an idea of what it should do and how I should do it. When coding functions that might be complex I like to break down the idea into chunks.  I work on the first chunk.
Once I am satisfied  that chunk works, I will move onto the next chunk. and so on. This also makes it easier to debug becuase you are only focusing on a small part of the code. This allows me to make sure that the idea of functionally is actually possible before putting all the pieces together.  But when I work on each chunk I take short cuts and use bad coding methods. After I get the whole idea working as a whole is when I start to pretty up the code. Its usually changing up methods, variables names, or simplizing the lines.  Sometimes I will create new folder names in my ruby directory, work on an idea in that directory. Make sure that everything works, after I am happy that everythign is working I will implement the idea into the project directory. 


