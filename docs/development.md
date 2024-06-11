# Development Set-Up

This documentation covers the development set-up to start developing under this repository.

## Software Requirements

You must have the following softwares installed in your computer and some VSCode extensions that will help you with development process.

- Docker. You have to install Docker on your local computer.

- VSCode. This is the editor this repository uses for local development.

- Dev Containers VSCode extensions. This extension is required to create the development container and the postgres container as well.


## Development Proccess

Before to launch the Docker containers, you have to change the workspace folder name in the docker configuration.

1. Open the project with VSCode

2. Search for "rails_google_cloud_quickstart" in the Dockerfile, docker compose files and the .devcontainer.json file and change the name.

3. Initialize Docker

4. Type **ctrl + shift + p** and select the option: "Dev Containers: Rebuild without cache and reopen in container"

5. Wait until the containers are ready. The database will be created automatically

6. Finally, run the following command to create a new rails credentials:

```bash
bin/run-after-repo-create-from-template
```

7. Compile the assests with the following command:

```bash
rails assets:precompile
```

8. Launch the rails server and happy coding!

```bash
rails s
```

If you encountered errors on the installation process, feel free to reach any of the support team by email: ortiz.mata.jorge@gmail.com
