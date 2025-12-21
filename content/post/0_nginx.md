---
title: Nginx
name: 0_nginx
date: 2024-10-15
draft: false
tags:
  - SystemDesign
share: "true"
---

## Introduction to Nginx

Nginx (pronounced as "Engine-X") is a high-performance, open-source web server, reverse proxy server, and email (IMAP/POP3) proxy server. 

## What is Nginx?

### Key Features

- **High Performance:** Ability to handle thousands of concurrent connections with minimal memory footprint.
- **Reverse Proxying:** Acts as an intermediary for requests from clients seeking resources from servers.
- **Load Balancing:** Distributes incoming traffic across multiple servers to ensure reliability and uptime.
- **SSL/TLS Support:** Provides secure connections using SSL/TLS protocols.
- **Caching:** Reduces server load and improves response times by caching responses from backend servers.
- **Modular Architecture:** Supports dynamic modules to extend its functionality.
- **Static and Dynamic Content Serving:** Efficiently serves static files and dynamically generated content.

### Use Cases

- **Web Servers:** Serving websites and web applications.
- **Reverse Proxy:** Forwarding requests to application servers like Node.js, Python, Ruby, etc.
- **Load Balancer:** Distributing traffic across multiple backend servers.
- **API Gateway:** Managing and routing API requests.
- **Content Caching:** Storing frequently accessed content to enhance performance.

## Prerequisites

Before diving into Nginx, ensure you have the following:

- **Basic Understanding of Web Servers:** Familiarity with how web servers work.
- **Command-Line Proficiency:** Comfortable using the terminal/command prompt.
- **Basic Networking Knowledge:** Understanding of concepts like IP addresses, DNS, HTTP/HTTPS.
- **Root/Sudo Access:** Required for installing and configuring Nginx on servers.

## Installation

### Installing on Ubuntu/Debian

1. **Update Package List**

    ```bash
    sudo apt update
    ```

2. **Install Nginx**

    ```bash
    sudo apt install nginx
    ```

3. **Start and Enable Nginx**

    ```bash
    sudo systemctl start nginx
    sudo systemctl enable nginx
    ```

4. **Verify Installation**

    Open your web browser and navigate to `http://your_server_ip/`. You should see the Nginx default welcome page.

### Installing on CentOS/RHEL

1. **Install EPEL Repository**

    ```bash
    sudo yum install epel-release -y
    ```

2. **Install Nginx**

    ```bash
    sudo yum install nginx -y
    ```

3. **Start and Enable Nginx**

    ```bash
    sudo systemctl start nginx
    sudo systemctl enable nginx
    ```

4. **Adjust Firewall**

    Allow HTTP and HTTPS traffic.

    ```bash
    sudo firewall-cmd --permanent --add-service=http
    sudo firewall-cmd --permanent --add-service=https
    sudo firewall-cmd --reload
    ```

5. **Verify Installation**

    Navigate to `http://your_server_ip/` in your browser to see the Nginx default page.

### Installing on macOS

You can install Nginx on macOS using Homebrew.

1. **Install Homebrew** (if not already installed)

    ```bash
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

2. **Install Nginx**

    ```bash
    brew install nginx
    ```

3. **Start Nginx**

    ```bash
    brew services start nginx
    ```

4. **Verify Installation**

    Open `http://localhost:8080/` in your web browser to see the Nginx welcome page.

### Building from Source

Building Nginx from source allows customization by enabling specific modules.

1. **Install Dependencies**

    ```bash
    sudo apt update
    sudo apt install -y build-essential libpcre3 libpcre3-dev zlib1g zlib1g-dev libssl-dev
    ```

2. **Download Nginx Source Code**

    ```bash
    wget http://nginx.org/download/nginx-1.21.6.tar.gz
    tar -zxvf nginx-1.21.6.tar.gz
    cd nginx-1.21.6/
    ```

3. **Configure Nginx**

    ```bash
    ./configure --prefix=/usr/local/nginx --with-http_ssl_module
    ```

    - `--prefix`: Installation directory.
    - `--with-http_ssl_module`: Enables SSL support.

4. **Compile and Install**

    ```bash
    make
    sudo make install
    ```

5. **Start Nginx**

    ```bash
    sudo /usr/local/nginx/sbin/nginx
    ```

6. **Verify Installation**

    Visit `http://your_server_ip/` to see the Nginx welcome page.

## Basic Configuration

### Nginx Configuration File Structure

Nginx configuration files are typically located at `/etc/nginx/nginx.conf` on Unix-based systems. The primary configuration is divided into several blocks:

- **Main Context:** Global settings.
- **Events Block:** Handles connection-related settings.
- **HTTP Block:** Configures web server settings, including server blocks.
- **Server Blocks:** Define virtual hosts/sites.
- **Location Blocks:** Specify how to handle different request URIs.

### Understanding the `nginx.conf` File

Here is a breakdown of a typical `nginx.conf` file:

```nginx
user www-data;
worker_processes auto;
pid /run/nginx.pid;

events {
    worker_connections 1024;
}

http {
    include /etc/nginx/mime.types;
    default_type application/octet-stream;

    sendfile on;
    keepalive_timeout 65;

    # Logging
    access_log /var/log/nginx/access.log;
    error_log /var/log/nginx/error.log;

    # Gzip Compression
    gzip on;
    gzip_types text/plain application/xml text/css application/javascript;

    # Server Block
    server {
        listen 80;
        server_name example.com www.example.com;

        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;

        location / {
            try_files $uri $uri/ =404;
        }

        # Additional configurations...
    }

    # Additional server blocks...
}
```

- **Main Context:** Sets user permissions, worker processes, and PID file location.
- **Events Block:** Configures connection-related settings like `worker_connections`.
- **HTTP Block:** Contains settings related to handling HTTP requests, including MIME types, logging, compression, and server blocks.
- **Server Block:** Defines settings for a virtual host, including ports, server names, root directory, index files, and location handling.

## Serving Static Content

One of the fundamental uses of Nginx is to serve static files efficiently.

### Basic Server Block

Here's a simple server block configured to serve static content:

```nginx
server {
    listen 80;
    server_name your_domain.com;

    root /var/www/your_domain;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

### Setting Up Root and Index Files

- **root:** Specifies the root directory where your website files are located.
- **index:** Defines the default file to serve when a directory is requested.

**Example:**

```nginx
server {
    listen 80;
    server_name example.com;

    root /usr/share/nginx/html;
    index index.html index.htm;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

## Handling Dynamic Content

Nginx can also handle dynamic content by forwarding requests to application servers.

### Proxying Requests to Application Servers

Use the `proxy_pass` directive to forward requests to backend servers like Node.js, Python, Ruby, etc.

**Example: Proxying to a Node.js Server**

```nginx
server {
    listen 80;
    server_name your_domain.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

**Explanation:**

- **proxy_pass:** Forwards all requests to the specified backend server.
- **proxy_set_header:** Sets custom headers to maintain the original client details and support WebSockets.
- **proxy_cache_bypass:** Ensures that cached content is bypassed when necessary.

### FastCGI and PHP Integration

Nginx can serve PHP applications using FastCGI processors like PHP-FPM.

**Example: Configuring Nginx to Serve PHP with PHP-FPM**

1. **Install PHP and PHP-FPM**

    ```bash
    sudo apt install php-fpm
    ```

2. **Configure Nginx Server Block**

    ```nginx
    server {
        listen 80;
        server_name your_domain.com;

        root /var/www/your_domain;
        index index.php index.html index.htm;

        location / {
            try_files $uri $uri/ =404;
        }

        # Pass PHP scripts to FastCGI server
        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
        }

        # Deny access to .htaccess files
        location ~ /\.ht {
            deny all;
        }
    }
    ```

**Explanation:**

- **location ~ \.php$:** Matches PHP files.
- **include snippets/fastcgi-php.conf:** Includes default FastCGI parameters.
- **fastcgi_pass:** Specifies the FastCGI server address and socket.
- **deny all:** Denies access to hidden files like `.htaccess`.

## Load Balancing

Nginx can distribute incoming traffic across multiple backend servers to ensure reliability and improve performance.

### Basic Load Balancing Methods

1. **Round Robin (Default Method)**

    Distributes requests sequentially across the backend servers.

    ```nginx
    http {
        upstream backend {
            server backend1.example.com;
            server backend2.example.com;
            server backend3.example.com;
        }

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                proxy_pass http://backend;
            }
        }
    }
    ```

2. **Least Connections**

    Sends requests to the server with the fewest active connections.

    ```nginx
    http {
        upstream backend {
            least_conn;
            server backend1.example.com;
            server backend2.example.com;
            server backend3.example.com;
        }

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                proxy_pass http://backend;
            }
        }
    }
    ```

    **Explanation:**

    - **least_conn:** Nginx directive to enable least connections load balancing.

3. **IP Hash**

    Ensures that requests from the same client IP are always directed to the same backend server.

    ```nginx
    http {
        upstream backend {
            ip_hash;
            server backend1.example.com;
            server backend2.example.com;
            server backend3.example.com;
        }

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                proxy_pass http://backend;
            }
        }
    }
    ```

    **Explanation:**

    - **ip_hash:** Nginx directive to enable IP hash load balancing.

### Advanced Load Balancing Techniques

1. **Session Persistence**

    Ensures that a user's session is consistently routed to the same backend server.

    ```nginx
    http {
        upstream backend {
            server backend1.example.com;
            server backend2.example.com;
            server backend3.example.com;
        }

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                proxy_pass http://backend;
                proxy_set_header Cookie $http_cookie;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            }
        }
    }
    ```

    **Explanation:**

    - **proxy_set_header Cookie $http_cookie:** Passes cookies to maintain session persistence.

2. **Health Checks**

    Automatically detects and removes unhealthy backend servers from the rotation.

    ```nginx
    http {
        upstream backend {
            server backend1.example.com;
            server backend2.example.com;
            server backend3.example.com;

            # Health check parameters
            keepalive 32;
        }

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                proxy_pass http://backend;
                proxy_http_version 1.1;
                proxy_set_header Connection "";
            }
        }
    }
    ```

    **Note:** Nginx core does not support active health checks. For active health checks, consider using the **Nginx Plus** version or integrating with external tools like **Consul**.

3. **Dynamic Load Balancing with Variables**

    Use variables to dynamically select backend servers based on request attributes.

    ```nginx
    http {
        upstream backend {
            server backend1.example.com;
            server backend2.example.com;
        }

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                set $backend "";
                if ($arg_site = "site1") {
                    set $backend "backend1.example.com";
                }
                if ($arg_site = "site2") {
                    set $backend "backend2.example.com";
                }

                proxy_pass http://$backend;
            }
        }
    }
    ```

## Security Best Practices

Securing your Nginx server is crucial to protect your web applications and data.

### SSL/TLS Configuration

Implement SSL/TLS to encrypt data between clients and your server.

1. **Obtain SSL Certificates**

    - **Using Let's Encrypt:** Free SSL certificates via Certbot.
    
        ```bash
        sudo apt install certbot python3-certbot-nginx
        sudo certbot --nginx -d your_domain.com -d www.your_domain.com
        ```

2. **Configure SSL in Nginx**

    ```nginx
    server {
        listen 443 ssl;
        server_name your_domain.com www.your_domain.com;

        ssl_certificate /etc/letsencrypt/live/your_domain.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/your_domain.com/privkey.pem;
        ssl_protocols TLSv1.2 TLSv1.3;
        ssl_ciphers HIGH:!aNULL:!MD5;

        location / {
            proxy_pass http://backend;
            # Additional proxy settings...
        }
    }

    server {
        listen 80;
        server_name your_domain.com www.your_domain.com;
        return 301 https://$host$request_uri;
    }
    ```

    **Explanation:**

    - **listen 443 ssl;**: Listens for HTTPS connections.
    - **ssl_certificate:** Path to the SSL certificate.
    - **ssl_certificate_key:** Path to the SSL certificate key.
    - **ssl_protocols:** Specifies allowed TLS protocols.
    - **ssl_ciphers:** Defines strong ciphers.

3. **Enable HTTP/2**

    ```nginx
    server {
        listen 443 ssl http2;
        server_name your_domain.com www.your_domain.com;

        ssl_certificate /etc/letsencrypt/live/your_domain.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/your_domain.com/privkey.pem;
        ssl_protocols TLSv1.2 TLSv1.3;
        ssl_ciphers HIGH:!aNULL:!MD5;

        location / {
            proxy_pass http://backend;
            # Additional proxy settings...
        }
    }
    ```

    **Explanation:**

    - **http2:** Enables HTTP/2 protocol for improved performance.

### Restricting Access

Control access to sensitive resources and restrict unwanted traffic.

1. **Restrict Access by IP Address**

    ```nginx
    server {
        listen 80;
        server_name your_domain.com;

        location /admin {
            allow 192.168.1.0/24;
            deny all;

            proxy_pass http://admin_backend;
        }

        location / {
            proxy_pass http://backend;
        }
    }
    ```

    **Explanation:**

    - **allow 192.168.1.0/24;**: Allows access from the specified IP range.
    - **deny all;**: Denies access to all other IPs.

2. **Password Protection with HTTP Basic Auth**

    ```bash
    sudo apt install apache2-utils
    sudo htpasswd -c /etc/nginx/.htpasswd user1
    ```

    **Explanation:**

    - **apache2-utils:** Provides `htpasswd` utility to create password files.
    - **htpasswd -c /etc/nginx/.htpasswd user1:** Creates a new password file and adds `user1`.

    **Nginx Configuration:**

    ```nginx
    server {
        listen 80;
        server_name your_domain.com;

        location /secure {
            auth_basic "Restricted Area";
            auth_basic_user_file /etc/nginx/.htpasswd;

            proxy_pass http://secure_backend;
        }

        location / {
            proxy_pass http://backend;
        }
    }
    ```

    **Explanation:**

    - **auth_basic:** Enables basic authentication with a realm name.
    - **auth_basic_user_file:** Specifies the path to the password file.

### Preventing Common Attacks

1. **DDoS Protection**

    Implement rate limiting to mitigate DDoS attacks.

    ```nginx
    http {
        limit_req_zone $binary_remote_addr zone=one:10m rate=1r/s;

        server {
            listen 80;
            server_name your_domain.com;

            location / {
                limit_req zone=one burst=5 nodelay;
                proxy_pass http://backend;
            }
        }
    }
    ```

    **Explanation:**

    - **limit_req_zone:** Defines a shared memory zone named `one` with a rate of 1 request per second.
    - **limit_req:** Applies the rate limit to requests in the specified location.

2. **Preventing Clickjacking**

    Add `X-Frame-Options` header to prevent the website from being framed.

    ```nginx
    server {
        listen 80;
        server_name your_domain.com;

        add_header X-Frame-Options "SAMEORIGIN" always;

        location / {
            proxy_pass http://backend;
        }
    }
    ```

    **Explanation:**

    - **add_header X-Frame-Options "SAMEORIGIN" always;**: Prevents the site from being embedded in iframes from different origins.

3. **Content Security Policy (CSP)**

    Define a CSP to prevent cross-site scripting (XSS) and other code injection attacks.

    ```nginx
    server {
        listen 80;
        server_name your_domain.com;

        add_header Content-Security-Policy "default-src 'self'; script-src 'self' https://cdnjs.cloudflare.com;" always;

        location / {
            proxy_pass http://backend;
        }
    }
    ```

    **Explanation:**

    - **add_header Content-Security-Policy:** Sets the CSP header to restrict sources of content.

## Performance Optimization

Enhance Nginx's performance to handle high traffic efficiently.

### Caching

Implement caching strategies to reduce server load and improve response times.

1. **Proxy Caching**

    Cache responses from backend servers.

    **Configuration:**

    ```nginx
    http {
        proxy_cache_path /var/cache/nginx levels=1:2 keys_zone=my_cache:10m max_size=10g inactive=60m use_temp_path=off;

        server {
            listen 80;
            server_name your_domain.com;

            location /api/ {
                proxy_cache my_cache;
                proxy_pass http://backend;
                proxy_cache_valid 200 302 10m;
                proxy_cache_valid 404      1m;
                proxy_cache_use_stale error timeout updating;
                add_header X-Proxy-Cache $upstream_cache_status;
            }
        }
    }
    ```

    **Explanation:**

    - **proxy_cache_path:** Defines cache storage path and parameters.
    - **proxy_cache:** Enables caching for the specified location.
    - **proxy_cache_valid:** Sets cache duration based on response statuses.
    - **proxy_cache_use_stale:** Serves stale content under specific conditions.
    - **add_header X-Proxy-Cache:** Adds a header indicating cache status.

2. **FastCGI Caching**

    Cache responses from FastCGI servers like PHP-FPM.

    **Configuration:**

    ```nginx
    http {
        fastcgi_cache_path /var/cache/nginx levels=1:2 keys_zone=fastcgi_cache:10m inactive=60m use_temp_path=off;

        server {
            listen 80;
            server_name your_domain.com;

            location ~ \.php$ {
                fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
                include fastcgi_params;
                fastcgi_cache fastcgi_cache;
                fastcgi_cache_valid 200 302 10m;
                fastcgi_cache_valid 404      1m;
                fastcgi_cache_use_stale error timeout updating;
                add_header X-FastCGI-Cache $upstream_cache_status;
            }
        }
    }
    ```

    **Explanation:**

    - **fastcgi_cache_path:** Defines FastCGI cache storage path and parameters.
    - **fastcgi_cache:** Enables FastCGI caching for the specified location.

### Gzip Compression

Enable gzip compression to reduce the size of responses and improve load times.

**Configuration:**

```nginx
http {
    gzip on;
    gzip_disable "msie6";

    gzip_vary on;
    gzip_proxied any;
    gzip_comp_level 6;
    gzip_buffers 16 8k;
    gzip_http_version 1.1;
    gzip_types text/plain application/xml text/css application/javascript image/svg+xml;
}
```

**Explanation:**

- **gzip on;**: Enables gzip compression.
- **gzip_disable "msie6";**: Disables gzip for old browsers.
- **gzip_vary on;**: Adds `Vary: Accept-Encoding` header.
- **gzip_comp_level:** Sets compression level (1-9).
- **gzip_buffers:** Defines buffer size for compression.
- **gzip_http_version:** Minimum HTTP version for gzip.
- **gzip_types:** Specifies MIME types to compress.

### Buffer Adjustments

Adjust buffer sizes to optimize request and response handling.

**Example:**

```nginx
http {
    client_max_body_size 50M;
    client_body_buffer_size 128k;
    large_client_header_buffers 4 16k;
    client_body_timeout 12;
    client_header_timeout 12;
    send_timeout 10;
}
```

**Explanation:**

- **client_max_body_size:** Limits the maximum allowed size of the client request body.
- **client_body_buffer_size:** Sets the buffer size for reading client request body.
- **large_client_header_buffers:** Defines buffers for large client headers.
- **client_body_timeout, client_header_timeout, send_timeout:** Sets timeouts for reading client requests and sending responses.

### Rate Limiting

Control the rate of incoming requests to prevent abuse and ensure quality of service.

**Example: Rate Limiting Using Shared Memory Zones**

```nginx
http {
    limit_req_zone $binary_remote_addr zone=one:10m rate=1r/s;

    server {
        listen 80;
        server_name your_domain.com;

        location /api/ {
            limit_req zone=one burst=5 nodelay;
            proxy_pass http://backend;
        }
    }
}
```

**Explanation:**

- **limit_req_zone:** Defines a shared memory zone for rate limiting based on the client IP.
- **limit_req:** Applies rate limiting to the specified location.

## Monitoring and Logging

Effective monitoring and logging are essential for maintaining and troubleshooting your Nginx server.

### Access Logs

Access logs record all incoming requests, providing valuable insights into traffic patterns and user behavior.

**Configuration:**

```nginx
http {
    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                    '$status $body_bytes_sent "$http_referer" '
                    '"$http_user_agent" "$http_x_forwarded_for"';

    access_log /var/log/nginx/access.log main;
}
```

**Explanation:**

- **log_format:** Defines the format of the log entries.
- **access_log:** Specifies the location and format of the access log.

### Error Logs

Error logs capture server-side errors and issues, aiding in diagnosis and troubleshooting.

**Configuration:**

```nginx
http {
    error_log /var/log/nginx/error.log warn;
}
```

**Explanation:**

- **error_log:** Specifies the location and log level (`debug`, `info`, `notice`, `warn`, `error`, `crit`, `alert`, `emerg`).

### Real-time Monitoring with ngx_http_stub_status_module

The `ngx_http_stub_status_module` provides a simple status page displaying basic server metrics.

**Configuration:**

1. **Enable the Status Module**

    Ensure the module is included during Nginx compilation. Most pre-built Nginx packages include this module by default.

2. **Configure the Status Page**

    ```nginx
    server {
        listen 8080;
        server_name localhost;

        location /nginx_status {
            stub_status;
            allow 127.0.0.1; # Allow only local access
            deny all;
        }
    }
    ```

3. **Access the Status Page**

    Navigate to `http://localhost:8080/nginx_status` to view real-time metrics:

    ```
    Active connections: 291 
    server accepts handled requests
     1526989 1526989 2983949 
    Reading: 12 Writing: 34 Waiting: 245 
    ```

    **Explanation:**

    - **Active connections:** Current active connections.
    - **accepts/handled/requests:** Total accepted, handled, and processed requests.
    - **Reading/Writing/Waiting:** State of connections.

## Advanced Features

Explore advanced functionalities of Nginx to streamline and enhance your web server capabilities.

### Reverse Proxy

Implementing Nginx as a reverse proxy allows it to handle all client requests and distribute them to appropriate backend servers.

**Example: Reverse Proxy Setup**

```nginx
server {
    listen 80;
    server_name your_domain.com;

    location / {
        proxy_pass http://backend_server;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

**Explanation:**

- **proxy_pass:** Forwards requests to the specified backend server.
- **proxy_set_header:** Sets headers to preserve client information.

### Using Nginx as a Mail Proxy

Nginx can function as a mail proxy for IMAP, POP3, and SMTP protocols.

**Configuration Example for IMAP Proxy**

```nginx
mail {
    server {
        listen     143;
        protocol   imap;
        proxy_pass_error_message on;

        auth_http  localhost:8080/auth;
    }
}
```

**Explanation:**

- **mail:** Defines mail-related configurations.
- **server:** Configures the mail server.
- **listen:** Specifies the port and protocol.
- **proxy_pass_error_message:** Enables forwarding of error messages from the backend.
- **auth_http:** Defines the authentication server.

### WebSockets Support

Enable real-time, bidirectional communication using WebSockets.

**Configuration Example: WebSockets with Nginx**

```nginx
server {
    listen 80;
    server_name your_domain.com;

    location /ws {
        proxy_pass http://backend_server;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "Upgrade";
        proxy_set_header Host $host;
    }
}
```

**Explanation:**

- **proxy_http_version 1.1:** Sets HTTP version to 1.1 to support WebSockets.
- **proxy_set_header Upgrade $http_upgrade;**: Passes the Upgrade header.
- **proxy_set_header Connection "Upgrade";**: Maintains the connection upgrade.

### HTTP/2 Support

Implement HTTP/2 for improved performance with features like multiplexing, header compression, and server push.

**Configuration Example: Enabling HTTP/2**

```nginx
server {
    listen 443 ssl http2;
    server_name your_domain.com;

    ssl_certificate /etc/ssl/certs/your_domain.com.crt;
    ssl_certificate_key /etc/ssl/private/your_domain.com.key;

    location / {
        proxy_pass http://backend;
    }
}
```

**Explanation:**

- **http2:** Enables HTTP/2 protocol on the listen directive.
- **ssl_certificate & ssl_certificate_key:** Required for HTTPS and HTTP/2.

## Automation with Nginx

Automate configuration management and deployments to streamline operations.

### Automated Configuration Reloads

Automatically reload Nginx configurations without downtime.

**Using `nginx -t` and `nginx -s reload`**

```bash
sudo nginx -t && sudo nginx -s reload
```

**Explanation:**

- **nginx -t:** Tests the configuration for syntax errors.
- **nginx -s reload:** Reloads Nginx without stopping the service.

### Integration with CI/CD Pipelines

Integrate Nginx configuration deployments into CI/CD workflows for seamless updates.

**Example: GitLab CI/CD Configuration (`.gitlab-ci.yml`)**

```yaml
stages:
  - test
  - deploy

test_config:
  stage: test
  script:
    - sudo nginx -t
  only:
    - master

deploy_production:
  stage: deploy
  script:
    - sudo nginx -s reload
  only:
    - master
    - tags
```

**Explanation:**

- **test_config:** Tests Nginx configuration on commit to master.
- **deploy_production:** Reloads Nginx after successful tests.

## Troubleshooting

Identify and resolve common Nginx issues to maintain a healthy web server.

### Common Issues and Solutions

1. **Nginx Not Starting**

    - **Check Configuration Syntax:**

        ```bash
        sudo nginx -t
        ```

    - **Inspect Error Logs:**

        ```bash
        sudo tail -f /var/log/nginx/error.log
        ```

    - **Solution:** Fix any syntax errors or conflicts in the configuration file.

2. **403 Forbidden Error**

    - **Cause:** Incorrect file permissions or missing `index` file.
    - **Solution:** Ensure Nginx has read permissions to the root directory and that an `index` file exists.

        ```bash
        sudo chown -R www-data:www-data /var/www/your_domain
        sudo chmod -R 755 /var/www/your_domain
        ```

3. **502 Bad Gateway**

    - **Cause:** Backend server is down or misconfigured.
    - **Solution:** Verify the backend server is running and accessible. Check Nginx proxy settings.

4. **504 Gateway Timeout**

    - **Cause:** Backend server is taking too long to respond.
    - **Solution:** Increase timeout settings in Nginx and ensure backend server performance.

        ```nginx
        location / {
            proxy_pass http://backend;
            proxy_read_timeout 300;
            proxy_connect_timeout 300;
            proxy_send_timeout 300;
        }
        ```

### Debugging Techniques

1. **Enable Debug Logging**

    Modify the `error_log` directive to include debug information.

    ```nginx
    error_log /var/log/nginx/error.log debug;
    ```

    **Note:** Debug logging can generate large amounts of log data, so it should be used with caution to avoid enabling it in production environments.

2. **Use `curl` for Testing**

    Test server responses and behavior using `curl`.

    ```bash
    curl -I http://your_domain.com/
    curl -v http://your_domain.com/api
    ```

3. **Analyze Access Logs**

    Review access logs to understand traffic patterns and identify anomalies.

    ```bash
    sudo tail -f /var/log/nginx/access.log
    ```

4. **Check System Resources**

    Ensure the server has sufficient resources (CPU, memory, disk I/O).

    ```bash
    top
    df -h
    ```

## Extending Nginx with Modules

Enhance Nginx’s capabilities by integrating additional modules.

### Third-Party Modules

1. **ngx_brotli**

    Adds Brotli compression to Nginx.

    **Installation:**

    - Clone the module repository.

        ```bash
        git clone https://github.com/google/ngx_brotli.git
        cd ngx_brotli
        git submodule update --init
        ```

    - Recompile Nginx with the module.

        ```bash
        ./configure --add-module=/path/to/ngx_brotli
        make
        sudo make install
        ```

2. **ngx_pagespeed**

    Optimizes web pages by automatically applying best practices.

    **Installation:**

    - Download Pagespeed module.

        ```bash
        wget https://dl.google.com/dl/page-speed/psol/1.13.35.2-x64.tar.gz
        tar -xzvf 1.13.35.2-x64.tar.gz
        ```

    - Recompile Nginx with Pagespeed.

        ```bash
        ./configure --add-module=/path/to/ngx_pagespeed-1.13.35.2-beta
        make
        sudo make install
        ```

**Note:** Third-party modules require recompiling Nginx from source. Consider using dynamic modules if supported.

### Custom Module Development

Develop custom modules to extend Nginx functionality specific to your needs.

1. **Understand Nginx Module Architecture**

    - **Handler Directives:** Define how requests are processed.
    - **Configuration Directives:** Customize module behavior.
    - **Context Types:** Specify where directives can appear (`http`, `server`, `location`).

2. **Set Up Development Environment**

    - Install development dependencies.
    - Familiarize yourself with Nginx internals.

3. **Create a Basic Module**

    **Example: Hello World Module**

    ```c
    #include <ngx_config.h>
    #include <ngx_core.h>
    #include <ngx_http.h>

    static char *ngx_http_hello_world(ngx_conf_t *cf, ngx_command_t *cmd, void *conf);
    static ngx_int_t ngx_http_handler(ngx_http_request_t *r);

    static ngx_command_t ngx_http_hello_world_commands[] = {
        {
            ngx_string("hello_world"),
            NGX_HTTP_MAIN_CONF | NGX_CONF_NOARGS,
            ngx_http_hello_world,
            0,
            0,
            NULL
        },
        ngx_null_command
    };

    static ngx_http_module_t ngx_http_hello_world_module_ctx = {
        NULL, // preconfiguration
        NULL, // postconfiguration

        NULL, // create main configuration
        NULL, // init main configuration

        NULL, // create server configuration
        NULL, // merge server configuration

        NULL, // create location configuration
        NULL  // merge location configuration
    };

    ngx_module_t ngx_http_hello_world_module = {
        NGX_MODULE_V1,
        &ngx_http_hello_world_module_ctx,
        ngx_http_hello_world_commands,
        NGX_HTTP_MODULE,
        NULL, // init master
        NULL, // init module
        NULL, // init process
        NULL, // init thread
        NULL, // exit thread
        NULL, // exit process
        NULL, // exit master
        NGX_MODULE_V1_PADDING
    };

    static char *ngx_http_hello_world(ngx_conf_t *cf, ngx_command_t *cmd, void *conf) {
        ngx_http_core_loc_conf_t *clcf;

        // Get the core location config
        clcf = ngx_http_conf_get_module_loc_conf(cf, ngx_http_core_module);

        // Set the handler
        clcf->handler = ngx_http_handler;

        return NGX_CONF_OK;
    }

    static ngx_int_t ngx_http_handler(ngx_http_request_t *r) {
        if (!(r->method & NGX_HTTP_GET)) {
            return NGX_HTTP_NOT_ALLOWED;
        }

        ngx_str_t response = ngx_string("Hello, Nginx Module!");

        // Set response headers
        ngx_table_elt_t *h;
        h = ngx_list_push(&r->headers_out.headers);
        if (h == NULL) {
            return NGX_HTTP_INTERNAL_SERVER_ERROR;
        }

        h->key.len = sizeof("Content-Type") - 1;
        h->key.data = (u_char *) "Content-Type";
        h->value.len = sizeof("text/plain") - 1;
        h->value.data = (u_char *) "text/plain";

        r->headers_out.status = NGX_HTTP_OK;
        r->headers_out.content_length_n = response.len;
        r->headers_out.content_type = h->value;

        // Send headers
        ngx_int_t rc = ngx_http_send_header(r);
        if (rc == NGX_ERROR || rc > NGX_OK || r->header_only) {
            return rc;
        }

        // Create buffer
        ngx_buf_t *b = ngx_pcalloc(r->pool, sizeof(ngx_buf_t));
        if (b == NULL) {
            return NGX_HTTP_INTERNAL_SERVER_ERROR;
        }

        b->pos = response.data;
        b->last = response.data + response.len;
        b->memory = 1; // content is in memory
        b->last_buf = 1; // this is the last buffer in the response

        // Create chain link
        ngx_chain_t out;
        out.buf = b;
        out.next = NULL;

        return ngx_http_output_filter(r, &out);
    }
    ```

4. **Compile Nginx with the Custom Module**

    - **Download Nginx Source**

        ```bash
        wget http://nginx.org/download/nginx-1.21.6.tar.gz
        tar -zxvf nginx-1.21.6.tar.gz
        cd nginx-1.21.6/
        ```

    - **Copy Custom Module**

        Save the custom module as `ngx_http_hello_world_module.c` in the Nginx source directory.

    - **Configure Nginx with the Custom Module**

        ```bash
        ./configure --add-module=./ngx_http_hello_world_module
        make
        sudo make install
        ```

    - **Update Nginx Configuration to Use the Module**

        ```nginx
        server {
            listen 80;
            server_name your_domain.com;

            location /hello {
                hello_world;
            }
        }
        ```

    - **Restart Nginx**

        ```bash
        sudo nginx -s reload
        ```

    - **Test the Module**

        Navigate to `http://your_domain.com/hello` and you should see "Hello, Nginx Module!" displayed.

### Benefits of Extending Nginx with Modules

- **Customized Functionality:** Tailor Nginx to meet specific application requirements.
- **Enhanced Performance:** Optimize request handling and processing.
- **Improved Security:** Implement custom security measures and protocols.
- **Scalability:** Introduce features that facilitate the scaling of web services.

## Resources and Further Reading

### Official Documentation

- **Nginx Official Site:** [https://nginx.org/](https://nginx.org/)
- **Nginx Documentation:** [https://nginx.org/en/docs/](https://nginx.org/en/docs/)
- **Nginx Wiki:** [https://www.nginx.com/resources/wiki/](https://www.nginx.com/resources/wiki/)
- **Nginx Blog:** [https://www.nginx.com/blog/](https://www.nginx.com/blog/)

### Books and Articles

- **"Nginx: A Practical Guide to High Performance"** by Stephen Corona
- **"Mastering Nginx"** by Dimitri Aivaliotis
- **"Nginx Cookbook"** by Derek DeJonghe
- **"Nginx Essentials"** by Arun Kumar Maheshwari
- **Official Nginx Blog Articles:** Regularly updated with best practices and case studies.

### Online Tutorials and Courses

- **DigitalOcean Nginx Tutorials:** [https://www.digitalocean.com/community/tags/nginx](https://www.digitalocean.com/community/tags/nginx)
- **TutorialsPoint Nginx Tutorial:** [https://www.tutorialspoint.com/nginx/index.htm](https://www.tutorialspoint.com/nginx/index.htm)
- **Udemy Nginx Courses:** [https://www.udemy.com/topic/nginx/](https://www.udemy.com/topic/nginx/)
- **Coursera Web Server Management Courses:** Search for Nginx-related courses.

### Community and Support

- **Nginx Forums:** [https://forum.nginx.org/](https://forum.nginx.org/)
- **Stack Overflow:** Tag questions with `nginx` to get help from the community.
- **Reddit r/nginx:** [https://www.reddit.com/r/nginx/](https://www.reddit.com/r/nginx/)
- **Nginx Slack:** Join the [official Nginx Slack workspace](https://nginx.slack.com/) for real-time discussions (requires invitation).
- **GitHub Issues:** Report bugs or request features in the [Nginx GitHub repository](https://github.com/nginx/nginx/issues).

*Happy Nginx-ing!*
