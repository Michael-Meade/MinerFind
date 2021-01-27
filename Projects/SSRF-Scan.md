### Background
The code to the project can be found <a href="https://github.com/Michael-Meade/SSRF-Scan">here</a>
I wanted to focus more on cyber security tools. So I decided I would try to dig deep and learn as much as I can about a topic. I picked SSRF. I am unsure what it is about SSRF that I 
find so cool, but I think SSRf is the bee's knees. In one of my other posts, I wrote about messing around with <a href="https://michael-meade.github.io/2021/01/19/Messing-with-SSRF.html">SSRF</a>

### The design
Since it was my first attempt at creating a tool or messing around with codign a tool for SSRf. I wanted to make it simple as I can. I thought that I could always add stuff to it if I need to. 

I wanted to the script to take command arguments, so first I had to create an argument that would take the domain we wanted so we could scan it for any SSRF vulnerabilites. 

The url argument should look something like this: 
`
test.rb --url http://localhost:4567/?url=SSRF
`

You <b>need</b> to add the word <b>SRRF</b> to the param you want to scan. The code will replace this with the url when it is time to scan. 
Currently the program is only able to run port scans. To do this the user needs to use the input an ip to scan. If the site is vulnerable wer might be able to port scan on the 
the network to see if there are other any open ports. 

`--ps 127.0.0.01`
