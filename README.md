## Website Sample
This is a sample website setup using `docker-compose`, Next.js, nginx and .NET 5. It is not functional as a website as it's only an example.

## Required Setup
### NGINX
- You need to edit the configs to:
  - Add the other containers as upstreams (as in [`30-main-base.conf`](./Website.Nginx/configurations/conf.d/30-main-base.conf));
  - Add each domain and make it point to containers or serve assets (as in [`40-example.com.conf`](./Website.Nginx/configurations/conf.d/40-example.com.conf) and [`41-backend.example.com.conf`](./Website.Nginx/configurations/conf.d/41-backend.example.com.conf)).
- You also need to add your SSL/TLS certificates to [`certificates`](./Website.Nginx/certificates);
- (Optional) Re-generate `dhparams.pem` using `openssl dhparam -out dhparam.pem 4096`.
