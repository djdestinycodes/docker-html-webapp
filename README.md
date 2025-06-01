
# Docker HTML Webapp

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)

---

## Overview

This project is a simple static HTML website served by an Nginx web server inside a Docker container.

It demonstrates the basics of:

- Writing a Dockerfile using the official `nginx:alpine` image
- Copying static files into the container
- Building and running a Docker image locally

---

## Project files

- `Dockerfile`  
- `index.html`  

---

## Dockerfile contents

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

---

## index.html contents

```html
<!DOCTYPE html>
<html>
<head>
  <title>Docker Demo</title>
</head>
<body>
  <h1>Hello from Docker!</h1>
  <p>This is a simple static site running in a Docker container.</p>
</body>
</html>
```

---

## How to build and run

1. **Build the Docker image**

```bash
docker build --no-cache -t html-webapp .
```

2. **Run the Docker container**

```bash
docker run -d -p 8080:80 --name test-html-webapp html-webapp
```

3. **Open your browser** and visit:

```
http://localhost:8080
```

You should see the "Hello from Docker!" page.

---

## Verify files inside container

You can check the contents served inside the container with:

```bash
docker run --rm html-webapp ls -l /usr/share/nginx/html/
```

---

## Notes

- The image uses `nginx:alpine` for a lightweight web server
- The static site files are copied into the container at build time
- Port 80 inside the container is mapped to port 8080 on your host machine

---

## Author

Girish Vilvankadu Jesudas  
[GitHub](https://github.com/djdestinycodes)
