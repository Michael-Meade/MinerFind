<center><h2>What is SSRF?</h2></center>
SSRF stands for Server Site Request forgery. This type of attack allows users to access information that is located within the compan's network. A company may have firewall rules set up that only allow local IPs to have access or files or services. The attacker uses the web server, which is accessabile across the internet to request locally hosted information that should only be accessible if they are in the network. Since the web server is hosted locally, the firewall does not block the request, allowing the hackers to access information that should not be accessed by the public. 

<center><h2>What type of things can be accessed</h2></center>
Attackers might be able to access config files. They might be able to access any other files hosted locally, any locally ran databases, services. 
