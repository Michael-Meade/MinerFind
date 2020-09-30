<h2>What is SSRF?</h2>
SSRF stands for Server Site Request forgery. Some sites and companies will have services that run locally. For example some companies might host a Intranet inside their network.
This is like a mini internet inside their network, in order to view it you have to be conntected to their network. 

The company most likely will have a firewall in place that would block any request that are made to the services that is not a local IP.  

SSRF tricks the firewall into thinking the local web server made the requests, when in reality an end user sent the request to the webserver. But since the web server that hosts
the website the attacker used is locally host, the firewall might allow the request to be made. This might allow an attacker to view senstive information like config information for services,
it might even allow the attacker to view databases that are hosted locally, or view any file on the system. 
