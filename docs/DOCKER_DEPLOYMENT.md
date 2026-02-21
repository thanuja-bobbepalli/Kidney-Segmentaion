# Docker Deployment Guide (Beginner Friendly)

This project is notebook-based, so the Docker setup runs **Jupyter Notebook** inside a container.

## 1) Install Docker

### For Windows 10 (recommended)
1. Enable virtualization in BIOS (usually already enabled on Lenovo laptops).
2. Install **WSL2** (Windows Subsystem for Linux):
   - Open PowerShell as Administrator and run:
     ```powershell
     wsl --install
     ```
   - Restart your laptop.
3. Install **Docker Desktop**:
   - https://www.docker.com/products/docker-desktop/
4. In Docker Desktop settings, ensure **Use the WSL 2 based engine** is enabled.

If you get errors on Windows 10, common causes are:
- Virtualization disabled in BIOS
- WSL2 not installed correctly
- Hyper-V / Windows features not enabled

## 2) Build the Docker image

From the project root:

```bash
docker build -t kidney-segmentation:latest .
```

## 3) Run the container

```bash
docker run --rm -it -p 8888:8888 -v "${PWD}:/app" kidney-segmentation:latest
```

On Windows PowerShell, use:

```powershell
docker run --rm -it -p 8888:8888 -v "${PWD}:/app" kidney-segmentation:latest
```

Then open your browser:
- http://localhost:8888

## 4) Open and run notebooks

Inside Jupyter, open:
- `Unet-kidney segmentation.ipynb` (training)
- `Unet-kidney inference.ipynb` (inference)

## 5) Stop container

Press `Ctrl + C` in terminal where container is running.

---

## Deploy/Run Online (without installing Docker locally)

Yes, this is possible.

### Option A: GitHub Codespaces
1. Push this repo to GitHub.
2. Open it in **Codespaces**.
3. In Codespaces terminal:
   ```bash
   docker build -t kidney-segmentation:latest .
   docker run --rm -it -p 8888:8888 kidney-segmentation:latest
   ```
4. Use forwarded port 8888 to access Jupyter.

### Option B: Play with Docker (quick demo)
- https://labs.play-with-docker.com/
- Good for learning, but session is temporary.

### Option C: Hugging Face Spaces / cloud VM
- You already have a Hugging Face demo link in README.
- For full custom Docker workflow, use cloud VM providers (AWS/GCP/Azure/RunPod) and run same build/run commands.

---

## Troubleshooting quick checks

Check Docker version:

```bash
docker --version
```

Check Docker engine:

```bash
docker info
```

Test Docker with hello-world:

```bash
docker run hello-world
```
