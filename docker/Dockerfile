# Defines tool versions
ARG PYTHON_VERSION=3.12-slim
ARG NGINX_VERSION=1.27-alpine
ARG ZENSICAL_VERSION=0.0.73

# Uses the specified Python version to build the documentation
FROM python:${PYTHON_VERSION} AS build

# Makes the Zensical version available in this build stage
ARG ZENSICAL_VERSION

# Sets the working directory inside the build container
WORKDIR /app

# Copies the documentation source files into the container
COPY files/ ./files/

# Installs the specified Zensical version
RUN pip install --no-cache-dir zensical==${ZENSICAL_VERSION}

# Builds the documentation website
RUN cd files && zensical build --clean

# Uses the specified Nginx version to serve the website
FROM nginx:${NGINX_VERSION}

# Copies the generated website to Nginx's web root
COPY --from=build /app/files/site /usr/share/nginx/html

# Exposes the HTTP port
EXPOSE 80

# Starts Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]