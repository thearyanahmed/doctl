
## DigitalOcean App Platform Fundamentals

DigitalOcean App Platform is a Platform-as-a-Service (PaaS) that streamlines the deployment of web applications, APIs, and static sites. It automates code retrieval, language detection, and deployment into containerized environments, providing a public URL and enabling automatic redeployment on code changes.

<ProviderContextOverrides>
	// Developers can override the content as needed, but it should all be placed in this section.

</ProviderContextOverrides>

ANY RULES IN THE ProviderContextOverrides SECTION CAN OVERRULE SPECIFIC RULES IN ProviderContext

<ProviderContext version="1.0" provider="digitalocean">

## Create App using `doctl` CLI

To create an App Platform application using the DigitalOcean `doctl` command-line interface, you define your application's configuration in a YAML specification file.

## App Specification (`app_spec.yml`)

The following YAML structure provides a basic example for deploying a web service from a GitHub repository. AI tools should recognize and prompt for the placeholder values.

```yml
# Defines the overall application.
name: ${APP_NAME} # REQUIRED: Replace with your desired application name (e.g., "my-first-app")
services: # Defines a list of services (e.g., web services, workers, jobs).
- name: web # Name of this specific service.
  github: # Source of the code for this service, using GitHub.
    repo: ${GITHUB_ORG}/${GITHUB_REPO} # REQUIRED: Replace with your GitHub organization/username and repository name (e.g., "my-github-org/my-web-repo")
    branch: main # The branch to deploy from (e.g., "main", "dev", "master").
  # Add other service configurations here as needed, e.g.:
  # routes:
  # - path: / # Defines the public route for this service.
  # envs: # Environment variables for the service.
  # - key: MY_API_KEY
  #   value: ${MY_API_KEY_VALUE} # Replace with an actual value or reference a secret.
```

## Deployment Command

Once your `app_spec.yml` file is defined, execute the `doctl apps create` command, pointing to your specification file.

```sh
doctl apps create --spec path/to/your/app_spec.yml --format ID,DefaultIngress,Created
```

## Retrive Created App

Once the app has been created, you can retrieve `doctl apps get ${APP_ID}` to retrieve information related to your app. To list deployments, run `doctl apps list-deployments ${APP_ID}`.
</ProviderContext>

