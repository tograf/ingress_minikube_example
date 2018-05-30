## Simple example to get ingress running using minikube

The following steps show a basic example to get the ingress controller running with minikube.

The setup was testet using minkube version 0.27 and kubernetes 1.10 on a Mac.

The used image is based on the default nginx image with a simple HTML Hello World page. Please note, the html is copied into a directory called `test` within `usr/share/nginx/html`.

For details see the `docker` directory.

### Basic Setup and test of service
    ## set up minikube
    $ minikube start --vm-driver=virtualbox

    ## deploy image and create service
    $ kubectl -f test_nginx.html

    ## check deployment and Service
    $ kubectl get -f test_nginx.yaml

    ## get ip of the Service
    $ minikube service test-nginx --url

    ## or open the url in the browser
    $ open $(minikube service test-nginx --url)/test

### Enabling minikube ingress
    ## enable minikube addon
    $ minikube addons enable ingress

    ## check if addon is enabled
    $ minikube addons list

    ## check the healthz page (should be http/200)
    $ curl -i http://$(minikube ip)/healthz

### Setup Ingress
    ## setup path and rules for Ingress
    $ kubectl create -f setup_ingress.yaml

    ## check ingress
    $ kubectl desrcibe ing

    ## in my case the ip shown using the previous command
    ## did not work, however using the minikube ip works
    $ open http://$(minikube ip)/test
