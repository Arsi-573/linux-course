# h3 Hello Web Server

First assingment was to read twon articles about name based Virtual Hosts and summarize both articles. 
#### 1) Name based virtual host
   https://httpd.apache.org/docs/2.4/vhosts/name-based.html

- Apache can host multiple websites on one IP address using name-based virtual hosts.
- Apache selects the correct virtual host by matching the requested hostname against ServerName and ServerAlias directives.
- Virtual hosts are defined using <VirtualHost> blocks, typically differentiated by name rather than IP.
- If no matching virtual host is found, Apache uses the first defined virtual host as the default.
- Each virtual host usually specifies at least ServerName and DocumentRoot.

#### 2) Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address
   https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/

- Apache can host multiple websites on one IP address using name-based virtual hosts.
- Each website has its own configuration file in the sites-available directory.
- Virtual host configurations define ServerName, optional ServerAlias, and DocumentRoot.
- Sites are enabled with the a2ensite command and applied by restarting Apache.
- The /etc/hosts file can be used for local testing without real DNS entries.

As we can see, there's a lot in common between these two articles.

### Testing the web server

#### 1) At first i installed apache2 using commands
   sudo apt update
   sudo apt install apache2
I had already done this earlier, so then I later just confirmed that it's working by running the command
   sudo systemctl status apache2
I also opened the web browser and moves to http://localhost to verify, that apache2 is running and working well.

<img width="1263" height="748" alt="1  localhost ja terminal" src="https://github.com/user-attachments/assets/5324a113-e78c-4854-9e28-30298342b5bd" />

I then entered the command 
    sudo tail -f /var/log/apache2/access.log 
To see the log when downloading the site. The lines can be summarized:
- Each line in the Apache access log represents one HTTP request.
- The log shows who made the request, what was requested, and when it happened.
- It includes the HTTP method, status code, and response size.
- Status code 200 means the request succeeded, and 404 means the resource was not found.
- Access logs are used to monitor server activity and troubleshoot problems.

<img width="916" height="482" alt="image" src="https://github.com/user-attachments/assets/52e2793f-52e7-46b0-82fb-5951ff63b4b5" />

#### 2) Creating directory and configuring the site
Using the commands shown in the picture below, I created a new directory hattu.example.com, used micro to create the site and created the new VirtualHost. Then I ensited the new hattu.example.com and dissited the default- site and restarted apache2. 

<img width="679" height="289" alt="image" src="https://github.com/user-attachments/assets/d505c4e3-4b4d-4210-aa19-80801cd68e15" />

Command on micro:
<img width="451" height="265" alt="3  micro" src="https://github.com/user-attachments/assets/dc1ad04f-fdd0-4c6d-921a-79ed5d2d34e7" />

Configuring the VirtualHost:
<img width="587" height="211" alt="4  VirtualHost" src="https://github.com/user-attachments/assets/682549c0-f5ad-4e70-94b3-641695f3af72" />

After this I went back to browser and got error 403, so I gave the command 
   sudo tail -n 50 /var/log/apache2/error.log
And after consulting AI found out that there was no execute permission to the given directory so I used the command 
   sudo chmod 711/home/juho 
To give the right permissions. After this I restarted apache2 again and refreshed the page on my browser to see the results and it worked.

<img width="1260" height="771" alt="image" src="https://github.com/user-attachments/assets/d01e80d5-1bc6-411d-9016-3ea745b29573" />

#### 3) Creating valid HTML5- site
I then opened micro again to update the site to HTML5. I used the commands ahown in the picture below:

<img width="907" height="685" alt="image" src="https://github.com/user-attachments/assets/e0916c72-2255-4393-961d-cebf205fc288" />

And i used my browser to verify the results:

<img width="661" height="247" alt="image" src="https://github.com/user-attachments/assets/e4ebfc83-68fa-4f64-a435-94b5773d6270" />

#### 4) Curl
The curl -I command can be summarized:
- The curl -I http://localhost/ command was used to fetch only the HTTP response headers.
- The response HTTP/1.1 200 OK shows that the request was successful.
- The Server header indicates that the page is served by Apache on Debian.
- Content-Type: text/html tells the browser that the response contains HTML content.
- Content-Length shows the size of the HTML response in bytes.
- The curl http://localhost/ command was used to fetch the full HTML content of the page.

<img width="868" height="628" alt="image" src="https://github.com/user-attachments/assets/5ef23b21-2063-42d0-8577-f78e3d4f706f" />

