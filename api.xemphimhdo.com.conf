server {

       listen   80;

       server_name api.xemphimhdo.com;

       access_log off;

       error_log /var/www/files/logs/error.log;

       root /var/www/files/html/public;

       index index.php;

       location / {
           if (!-f $request_filename) {
            rewrite ^(.*)$ /index.php?q=$1 last;
            break;
           }
       }

       location ~ /\.{deny  all;}

       location ~ \.php$ {

           include /etc/nginx/fastcgi_params;

           fastcgi_pass 127.0.0.1:9000;

           fastcgi_param APPLICATION_ENV production;

           fastcgi_index index.php;

           fastcgi_param SCRIPT_FILENAME /var/www/files/html/public$fastcgi_script_name;

       }

}

server {

       listen   80;

       server_name static-api.xemphimhdo.com;

       error_log /var/www/files/logs/static_error.log;

       root /var/www/files/html/static;

       add_header Pragma public;

       add_header Cache-Control "public, must-revalidate, proxy-revalidate";

       expires           max;

       access_log off;

       log_not_found     off;

       location ~ /\.{deny  all;}

       location ~* \.(eot|ttf|woff|otf|svg||woff2|html)$ {

         add_header "Access-Control-Allow-Origin" "*";

       }

       # Deny access to sensitive files.

       location ~ (\.inc\.php|\.tpl|\.sql|\.tpl\.php|\.db)$ {

         deny all;

       }

        #concat_types text/css application/javascript;

       location ~* /js {

         #concat on;

         #concat_max_files 30;

       }

       location ~* /css {

         #concat on;

         #concat_max_files 30;

       }

       location ~ /\.ht {

         deny  all;
        }
}

server {
       listen   80;
       server_name upload-api.xemphimhdo.com;
       error_log /var/www/files/logs/upload_error.log;
       root /var/www/files/html/static/uploads;
       add_header Pragma public;
       add_header Cache-Control "public, must-revalidate, proxy-revalidate";
       add_header "Access-Control-Allow-Origin" "*";
       expires           max;
       access_log on;
       log_not_found     off;
       location ~ /\.{deny  all;}

       location ~* \.(eot|ttf|woff|otf|svg)$ {
         add_header "Access-Control-Allow-Origin" "*";
       }

        location ~* \.(png|jpg|gif|webp)$ {
         add_header "Access-Control-Allow-Origin" "*";
       }

       # Deny access to sensitive files.
       location ~ (\.inc\.php|\.tpl|\.sql|\.tpl\.php|\.db)$ {
         deny all;
       }

       location ~ /\.ht {
         deny  all;
       }
}

