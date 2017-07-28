# nginx-rtmp-docker
**Dockerfile for building lightweight nginx + rtmp module for replicating streams**

## Usage

### Running
`docker run -d -p 1935:1935 -p 80:8000 tomasolander/nginx-rtmp-docker`

If you want to use a custom nginx.conf file, create a volume mapping:

`docker run -d -p 1935:1935 -p 80:8000 -v /path/to/my/custom/nginx.conf:/etc/nginx/nginx.conf tomasolander/nginx-rtmp-docker`

### Broadcasting
Create a new profile in OBS and change your broadcast settings:

- **Stream type:** Custom Streaming Server
- **URL:** rtmp://`<your server ip>`/live
- **Stream key:** `<whatever you like>`
  
### Watching
You can view the stream via HLS in your browser:

http://`<your server ip>`/#`<your stream key>`

## Troubleshooting
If you encounter an error like this:
```
[alert] could not open error log file: open() "/var/log/nginx/access.log" failed (13: Permission denied)
```

Then you are running an outdated version of Docker. See [the Docker documentation](https://docs.docker.com/engine/installation/) on how to get the latest version.

## More info
Docker Hub: https://hub.docker.com/r/tomasolander/nginx-rtmp-docker/

Based on setup described on the OBS forums [here](https://obsproject.com/forum/resources/how-to-set-up-your-own-private-rtmp-server-using-nginx.50/).

Fork of [DvdGiessen/nginx-rtmp-docker](https://github.com/DvdGiessen/nginx-rtmp-docker).
