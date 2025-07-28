# Dockerized PDF Heading Extraction Solution

This guide explains how to use the Dockerized solution for extracting headings and structure from PDFs automatically.

---

## Folder Structure

```
Adobe_1A/
├── improved_process_pdfs.py      # Main Python script
├── requirements.txt              # Python dependencies
├── dockerfile                    # Docker build instructions
├── Docker_README.md              # This documentation file
├── input/                        # Place your PDF files here
├── output/                       # JSON outputs will be written here
├── (other files/folders)
```

---

## Prerequisites
- Docker installed on your system ([Download Docker](https://www.docker.com/products/docker-desktop/))

---

## How to Use

### 1. Place PDFs in the `input` Folder
- Copy all `.pdf` files you want to process into the `input` directory.

### 2. Build the Docker Image
Run this command in your project root (`Adobe_1A`):

```
docker build --platform linux/amd64 -t mysolutionname:somerandomidentifier .
```

### 3. Run the Docker Container
- **Windows Command Prompt:**
  ```
  docker run --rm -v C:/Users/tanvi/OneDrive/Desktop/Adobe_1A/input:/app/input -v C:/Users/tanvi/OneDrive/Desktop/Adobe_1A/output:/app/output --network none mysolutionname:somerandomidentifier
  ```
- **Windows PowerShell:**
  ```
  docker run --rm -v ${PWD}/input:/app/input -v ${PWD}/output:/app/output --network none mysolutionname:somerandomidentifier
  ```
- **Git Bash/WSL/Linux/macOS:**
  ```
  docker run --rm -v $(pwd)/input:/app/input -v $(pwd)/output:/app/output --network none mysolutionname:somerandomidentifier
  ```

### 4. Retrieve Results
- After the container finishes, the `output` folder will contain a `.json` file for each `.pdf` processed.

---

## Notes
- The solution automatically processes all PDFs in `/app/input` and writes results to `/app/output`.
- No need to activate any Python virtual environment locally; all dependencies are managed inside Docker.
- If you see a warning about platform flags, you can safely ignore it or follow the best-practice fix as shown in the Dockerfile.

---

## Troubleshooting
- **No PDF files found:**
  - Ensure your PDFs are directly inside the `input` folder (not in subfolders).
- **Volume mount errors:**
  - Use the correct path syntax for your shell (see above).
- **Other issues:**
  - Check Docker Desktop is running and you have permissions for the directories.

---

## Contact
For further assistance, please contact the project maintainer.
