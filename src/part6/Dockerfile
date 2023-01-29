FROM nginx
WORKDIR /home/

COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY nginx_start.sh /home/nginx_start.sh

RUN chmod 755 /usr/bin/wall ; \
 chmod 777 /nginx_start.sh ; \
 chmod 755 /usr/bin/chsh ; \
 chmod 755 /usr/bin/expiry ; \
 chmod 755 /usr/bin/gpasswd ; \
 chmod 755 /usr/bin/passwd ; \
 chmod 755 /usr/bin/chage ; \
 chmod 755 /bin/umount ; \
 chmod 755 /usr/bin/newgrp ; \
 chmod 755 /usr/bin/chfn ; \
 chmod 755 /bin/mount ; \
 chmod 755 /bin/su ; \
 chmod 755 /sbin/unix_chkpwd ; \
 touch /var/run/nginx.pid ; \
 chown -R nginx:nginx /var/run/nginx.pid ; \
 chown -R nginx:nginx /var/log/nginx ; \
 chown -R nginx:nginx /var/cache/nginx

USER nginx
HEALTHCHECK NONE
ENTRYPOINT bash nginx_start.sh