FROM debian:bullseye-slim

# Set up environment
ENV NGINX_VERSION=1.24.0
ENV NJS_VERSION=0.8.1

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    gnupg2 \
    lsb-release

# Add the official nginx signing key
RUN curl -fsSL https://nginx.org/keys/nginx_signing.key | gpg --dearmor -o /usr/share/keyrings/nginx-archive-keyring.gpg

# Add nginx repo
RUN echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] http://nginx.org/packages/mainline/debian `lsb_release -cs` nginx" \
    > /etc/apt/sources.list.d/nginx.list

# Install nginx
RUN apt-get update && apt-get install -y --no-install-recommends nginx


RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN ln -sf /dev/stdout /var/log/nginx/access.log \
&& ln -sf /dev/stderr /var/log/nginx/error.log

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
