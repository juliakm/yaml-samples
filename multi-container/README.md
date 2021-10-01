# Building multi-container applications with Docker Compose and Azure Pipelines

Sample code to build three networked containers - Python, MySQL, and Postgres as part of a Django app. Working scenario is that you have a legacy app with user data saved in MySQL that your Django app needs to access and test against.

This example expands on the [Quickstart: Compose and Django tutorial in Docker Docs.](https://docs.docker.com/samples/django/)

@TODO: Update the example to build with a Azure DevOps YAML pipeline in addition to the `docker-compose.yml` file.

## Implementation notes

Run `sudo docker-compose run web django-admin startproject composeexample .` within your project directory to create a sample Django app. 

New database string for `settings.py`: 

```py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    },
    'users': {
        'NAME': 'users',
        'ENGINE': 'django.db.backends.mysql',
        'USER': 'mysql',
        'PASSWORD': 'mysql'
    }
```

### Resources
* [Quickstart: Compose and Django](https://docs.docker.com/samples/django/)
* [Overview of Docker Compose](https://docs.docker.com/compose/)
* [Azure Pipelines YAML Sidecar or Multi-container Support](https://github.com/microsoft/azure-pipelines-yaml/blob/master/design/sidecar-containers.md)
* [Using containerized services in your pipeline](https://devblogs.microsoft.com/devops/using-containerized-services-in-your-pipeline/)
