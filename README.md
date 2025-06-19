

# How to update the site using Docker

TLDR: Simply commit the changes on Github and push the changes in your Github branch. Owner can push directly to master branch, others can open a merge request. Once the code is merged into master, Github automatically runs the rsync etc automation code to update the live website. Track it and debug it by clicking "Actions" tab on Github.com project. Issue with Github automation running on wcsng-18 machine? Contact Gavin or Vatsank.

If you want to host it locally for visualizing changes locally before updating live page (e.g. local link http://0.0.0.0:4000/), then follow the instructiosn below.

Alternate to Docker, the ruby and jekyll can be installed on a local machine directly, but Docker works much better.

PS: Instructions generated using chatGPT, verified by Ish.

---

### rpi-iot-projects Jekyll Site: Docker Quickstart

This project uses [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/) to provide a reproducible, cross-platform environment for Jekyll development and site builds.  
The setup works seamlessly on Windows, Linux and Mac - Intel and Apple Silicon (M1/M2/M3) Macs using Docker Desktop.

---

### Prerequisites

- **Docker Desktop**: [Download & install](https://www.docker.com/products/docker-desktop/) (for Mac, Windows, or Linux).
- **Docker Compose**: Included with Docker Desktop (use `docker compose`, not `docker-compose`).
- (Optional) Familiarity with the [Jekyll](https://jekyllrb.com/) static site generator.

---

### 1. Clone this Repo

```sh
git clone https://github.com/rpi-iot-projects/rpi-iot-projects.github.io.git
cd rpi-iot-projects.github.io
```

---

### 2. Build the Docker Images

> **Build only once** (unless you change the Dockerfile or dependencies):

```sh
docker compose build
```

---

### 3. Local Development: Hot-Reloading Server

For editing and live-preview on your computer, use the `local` service:

```sh
docker compose up local
```

- Your Jekyll site will be served at [http://localhost:4000](http://localhost:4000).
- Any changes to your files will **auto-reload** in the browser (thanks to the volume mount).
- To stop the server, press **Ctrl+C**.

---

### 4. Production (“Remote”) Site Build

To generate your site with production settings (built files in the `_site` directory):

```sh
docker compose run --rm remote
```

- The built site will appear under your project’s local `_site/` directory.
- This is the folder to deploy to the website. Two ways

1. (Recommended) Simply commit the changes on Github and push the changes in your Github branch. Owner can push directly to master branch, others can open a merge request. Once the code is merged into master, Github automatically runs the rsync etc automation code to update the live website. Track it and debug it by clicking "Actions" tab on Github.com project. Issue with Github automation running on wcsng-18 machine? Contact Gavin or Vatsank.
2. (Manual - not recommended, but works for urgent need) - Directly rsync the `_site/` directory to 

---

### 5. Clean Up Build Artifacts

Remove the generated `_site/` and cache files:

```sh
docker compose run --rm cleanup
```

---

### 6. Common Issues

- **Gemfile changes?** Rebuild the image:  
  ```sh
  docker compose build
  ```
- **Port 4000 in use?**  Stop all containers or..
  Change the port in `docker-compose.yml`:  
  ```yaml
  ports:
    - "8080:4000"
  # Then access http://localhost:8080
  ```


---

### 7. File Structure

```text
/
├── Dockerfile
├── docker-compose.yml
├── Gemfile
├── _config.yml
├── ... (your Jekyll site files)
└── _site/         # (generated after build)
```

---

### 8. More Information

- [Jekyll Docs](https://jekyllrb.com/docs/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Docker Compose](https://docs.docker.com/compose/)

---

### Quick Reference

| Command                             | Purpose                        |
|--------------------------------------|--------------------------------|
| `docker compose build`               | Build the Docker image(s)      |
| `docker compose up local`            | Launch live dev site (4000)    |
| `docker compose run --rm remote`     | Run production site build      |
| `docker compose run --rm cleanup`    | Remove `_site/`, clean cache   |

