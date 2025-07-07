# Testing the Development Environment with Podman

## 1. Testing the Dockerfile with `podman build`

Run the following command inside `${workspace}\.devcontainer` to build the container:

```sh
podman build -t mkdocs-devcontainer .
```

This will build the container image using your `.devcontainer/Dockerfile`. Since `podman` is compatible with `docker`, no changes to the Dockerfile are required.

---

## 2. Testing the Environment with `podman run`

Run the following command to start the container:

```sh
podman run -it --rm mkdocs-devcontainer
```

This will start the container and drop you into a `bash` shell. From there, you can test:

- **Python**: Run `python3 --version` to verify Python is installed.
- **Conda**: Run `conda --version` to verify Conda is installed.
- **MkDocs**: Run `mkdocs --version` to verify MkDocs is installed.
- **mkdocs-material**: Run `pip show mkdocs-material` to verify

---

## 3. Using the Devcontainer in Windows Terminal App

### a. Configure Podman Socket

1. Ensure the `podman` socket is running:

   ```sh
   podman system service --time=0
   ```

2. Set the `DOCKER_HOST` environment variable to point to the `podman` socket:

   ```sh
   export DOCKER_HOST=unix:///run/user/$(id -u)/podman/podman.sock
   ```

   This allows tools like Visual Studio Code to communicate with `podman`.

---

### b. Open the Devcontainer in VS Code

1. Open your workspace in Visual Studio Code.
2. Install the "Remote - Containers" extension if not already installed.
3. Use the "Remote - Containers: Reopen in Container" command from the Command Palette.
4. VS Code will use the `podman` runtime to build and run the devcontainer.

---

### c. Windows Terminal Integration

You can open a new tab in the Windows Terminal App and connect to the running container using:

```sh
podman exec -it <container-id> bash
```

Replace `<container-id>` with the ID of the running container, which you can find using `podman ps`.

---

## 4. Potential Issues

- **Rootless Podman**: If you are using rootless `podman`, ensure that your user has the necessary permissions to run containers and bind the socket.
- **Volume Mounts**: If you need to mount your workspace into the container, use the `-v` flag with `podman run`:

  ```sh
  podman run -it --rm -v $(pwd):/workspace mkdocs-devcontainer
  ```

- **Windows File Paths**: When using `podman` on Windows, ensure that file paths are correctly translated (e.g., `/mnt/c/...` for Windows drives).

---

## 5. Testing the Devcontainer

Once the container is running, verify:

- The `mkdocs` environment is created and activated:

  ```sh
  conda activate mkdocs
  ```

- You can build documentation using `mkdocs`:

  ```sh
  mkdocs serve
  ```

With these steps, you should be able to use your devcontainer seamlessly in the Windows Terminal App.
