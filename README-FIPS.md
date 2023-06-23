# Ingress NGINX Controller -- FIPS

Images need to be manually tagged & pushed.

nginx need to be built before ingress controller.

Build nginx image and push to a repo:

cd image/nginx
PLATFORMS="linux/amd64" REGISTRY=gcr.io/spectro-dev-public/guyni/ingress-nginx make build


To build ingress controller:
cd to project root and update NGINX_BASE to have the nginx image built above. And then run:

PLATFORMS="amd64" BUILDX_PLATFORMS="linux/amd64" REGISTRY=gcr.io/spectro-dev-public/guyni/ingress-nginx make release

Build kube-webhook-certgen:
cd images/kube-webhook-certgen
PLATFORMS=linux/amd64 REGISTRY=gcr.io/spectro-dev-public/guyni/ingress-nginx make build

