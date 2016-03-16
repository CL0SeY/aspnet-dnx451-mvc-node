# aspnet-dnx451-mvc-node
Docker base image which includes a bunch of asp.net dnx451 mvc packages already installed PLUS node.js, bower and gulp.

Docker hub: https://hub.docker.com/r/cl0sey/aspnet-dnx451-mvc-node/

To use:
```
docker pull cl0sey/aspnet-dnx451-mvc-node
```

In your Dockerfile:
```dockerfile
FROM aspnet-dnx451-mvc-node:latest
ADD . app/
WORKDIR app
RUN "dnu" "restore"
RUN "dnu" "publish"
EXPOSE 5000
ENTRYPOINT ["bin/output/approot/web"]
```

Also in your project.json, ensure your Kestrel server is allowing port 5000 out for all to see:
```json
...
"commands": {
  "web": "Microsoft.AspNet.Server.Kestrel --server.urls=http://*:5000/"
},
...
```
