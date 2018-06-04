# OpenShift template for nginx and php-fpm

This template creates OpenShift resources for nginx with php-fpm

* DeploymentConfig for a pod with nginx and php-fpm
* BuiltConfig and ImageStream for php-fpm (to be able to customize the php-fpm version and include custom PHP modules)
* ConfigMap for nginx configuration
* Service for the nginx-php-fpm Pod
* PersistentVolumeClaim for the webroot volume

## Getting Started

You can import the template to your OpenShift cluster

```
oc create -f https://raw.githubusercontent.com/rybnico/openshift-nginx-php-fpm/master/nginx-php-fpm-template.yaml
```

or process it directly

```
oc process -f https://raw.githubusercontent.com/rybnico/openshift-nginx-php-fpm/master/nginx-php-fpm-template.yaml APP_NAME=my-fancy-app NGINX_IMAGE=nginx:stable PHP_FPM_IMAGE=php:7.2-fpm WEBROOT_SIZE=512Mi | oc create -f -
```

Customize the php-fpm build according to your needs and start a build for the newly created BuildConfig to start a deployment.

## Built With

* [Offical nginx image](https://hub.docker.com/_/nginx/) - defaults to stable
* [Offical php image](https://hub.docker.com/_/php/) - defaults to php:7.2-fpm
