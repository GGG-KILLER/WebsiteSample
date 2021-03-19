FROM nginx:mainline-alpine

# Fix permissions
RUN touch /var/run/nginx.pid \
	&& chown -R nginx:nginx /var/run/nginx.pid \
	&& chown -R nginx:nginx /var/cache/nginx \
	&& rm -r /etc/nginx

# Set user (stuff above actually needs root)
USER nginx:nginx

# Move configs
COPY --chown=nginx:nginx ["certificates", "/var/cert"]
COPY --chown=nginx:nginx ["certificates/dhparam.pem", "/etc/ssl/dhparam.pem"]
COPY --chown=nginx:nginx ["configurations", "/etc/nginx"]

ENTRYPOINT ["nginx", "-g", "daemon off;"]
