## Docker

### Docker clean
`docker system prune`

### Docker UI

Install Portainer `docker run -d -p 9000:9000 --name portainer -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer`

Open localhost:9000 to access web UI. First you should create a user.
