# FLP Haskell development playground

This repo is built upon a provided Dockerfile from FLP course at Brno University of Technology, Faculty of Information Technology. It is designed to be a complete development environment for Haskell&Jupyter labs in the course. It uses Docker Compose and optionally VS Code Dev Containers for easy setup and development.

## Setup

1. **Install Docker**:

    a. For Windows and macOS, download and install Docker Desktop from [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).

    b. For Linux, follow the instructions for your distribution at [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/).

    *(Or)* Use this simple one-liner (beware of security implications):

```bash
curl -fsSL https://get.docker.com | sudo sh
```

2. **Clone the repository**:

```bash
git clone https://github.com/1ukastesar/fit-flp-hs-playground.git flp-hs-playground
cd flp-hs-playground
```

3. **Start the development environment**:

    a. Using Docker Compose (recommended):

    ```bash
    docker compose up -d
    ```

    b. Using VS Code Dev Containers:

    - Open the repository folder in VS Code.
    - *(Recommended)* Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) if you haven't already.
    - When prompted, reopen the folder in the container.
    - If not prompted, you can manually open the Command Palette (`Ctrl+Shift+P`) and select `Dev Containers: Reopen in Container`.

## Accessing the Environment

- **VS Code Dev Container**: Once the container is running, you can create and edit files and use the integrated terminal in VS Code (`Ctrl+Shift+;`) to run Haskell's compiler, REPL and Jupyter notebooks.

- **Jupyter Notebook web interface**: Get notebook URL with the access token:

```bash
# Docker Compose: run in current directory
docker compose exec devcontainer jupyter notebook list

# Dev Containers: integrated terminal
jupyter notebook list
```

And then open the provided URL in your web browser to access the Jupyter interface.

- **GHCi**: Run GHCi interactively from the container shell
```bash
# Docker Compose: run on host machine
docker compose exec devcontainer ghci

# Dev Containers: integrated terminal
ghci
```

## Troubleshooting

- **Write permission denied in the `work` directory**

> [!IMPORTANT]
> You'll probably need to re-run these commands after adding any files to the `work/` directory from the host.
> But the f would I know, Docker's bind mounts are just one big permission hell especially in rootless mode.

```bash
# on the host machine
sudo chmod -R 777 work

# or, if you wanna be better
docker compose exec -u 0 chown -R jovyan:users ~jovyan/work
# and thanks to `userns: host` in compose file it shouldn't break anything on host
```
