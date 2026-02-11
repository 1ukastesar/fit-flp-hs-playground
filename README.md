# FLP Haskell development playground

This repo is built upon a provided Dockerfile from FLP course at Brno University of Technology, Faculty of Information Technology. It is designed to be a complete development environment for Haskell&Jupyter labs in the course. It uses Docker Compose and optionally VS Code Dev Containers for easy setup and development.

## Setup

1. **Install Docker**:
    
    a. For Windows and macOS, download and install Docker Desktop from [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop).

    b. For Linux, follow the instructions for your distribution at [https://docs.docker.com/engine/install/](https://docs.docker.com/engine/install/).

    *(Or)* Use this simple one-liner (beware of security implications):

    `curl -fsSL https://get.docker.com | sudo sh`


2. **Clone the repository**:

```bash
git clone https://github.com/1ukastesar/fit-flp-hs-playground.git flp-hs-playground
cd flp-hs-playground
```

3. **Start the development environment**:

    a. Using VS Code Dev Containers (recommended):

    - Open the repository folder in VS Code.
    - *(Recommended)* Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) if you haven't already.
    - When prompted, reopen the folder in the container.
    - If not prompted, you can manually open the Command Palette (`Ctrl+Shift+P`) and select `Dev Containers: Reopen in Container`.

    b. Using Docker Compose:

    ```bash
    docker-compose up -d
    ```

## Accessing the Environment

- **VS Code Dev Container**: Once the container is running, you can create and edit files and use the integrated terminal in VS Code (`Ctrl+Shift+;`) to run Haskell's compiler, REPL and Jupyter notebooks.

- **Jupyter Notebook**: In the integrated terminal, print the URL with the access token:

```bash
jupyter notebook list
```

Open the provided URL in your web browser to access the Jupyter interface.

