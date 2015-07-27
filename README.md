# Part-IV-NGINX-
server {
        listen 80;
	    server_name www.distilnetworks.com;
        root /usr/share/nginx/www;
        index index.html index.htm;
		 
		
	  
		set $mobile_request false;

        if ($http_user_agent ~* '(Mobile|WebOS)') {  
            set $mobile_request true;
        }
        
		if ($mobile_request = true) {
            return 444;
        }
		
		location / {
           Proxy_pass http://www.distilnetworks.com;
		   
		   #block one workstation
		   
           deny    192.225.213.20;
		}
		
	}
