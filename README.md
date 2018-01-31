# coolstore-demo-guides

This repository contains the guides for delivering a demo using the [CoolStore Microservices](https://github.com/jbossdemocentral/coolstore-microservice) application on OpenShift. The guides are written in AsciiDoc and use [Workshopper](https://github.com/openshift-evangelists/workshopper) for rendering. 


You can deploy the guides using docker and a local copy of this GitHub repository:
```
$ cd coolstore-demo-guides
$ docker run -p 8080:8080 -v $(pwd):/app-data \
        -e CONTENT_URL_PREFIX="file:///app-data" \
        -e WORKSHOPS_URLS="file:///app-data/demo-cicd-eap.yml" \
        osevg/workshopper:latest
```

Or on OpenShift and directly referencing the GitHub repo:

```
$ oc new-app --name=guides --docker-image=osevg/workshopper:latest \
    -e WORKSHOPS_URLS=https://raw.githubusercontent.com/siamaksade/coolstore-demo-guides/blob/master/demo-cicd-eap.yml \
    -e CONTENT_URL_PREFIX=https://raw.githubusercontent.com/siamaksade/coolstore-demo-guides/blob/master

$ oc expose svc/guides
```