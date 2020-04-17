# Use the Nginx image
FROM nginx

# Remove the default.conf
RUN rm /etc/nginx/conf.d/default.conf

# Copy the nginx.conf to include the sites-available folder
COPY nginx.conf /etc/nginx

# Add the  directory of modules-available, sites-available
RUN mkdir /etc/nginx/sites-available /etc/nginx/sites-enabled /etc/nginx/modules-enabled

#symlinks creation
RUN ln -s /usr/share/nginx/modules-available/* /etc/nginx/modules-enabled/


COPY ./oot_nginx/oot.conf /etc/nginx/sites-available

RUN ln -s /etc/nginx/sites-available/oot.conf /etc/nginx/sites-enabled/

COPY uwsgi.conf /etc/init.d
# Copy the uwsgi_param
COPY uwsgi_params /etc/nginx
