# Solana Development Docker Image

This Docker image is a ready-to-use development environment for building and interacting with Solana programs. It includes Rust, Solana CLI, Anchor, SPL Token CLI, and Metaboss—all configured and pre-installed on top of **Ubuntu 24.04**.

## What's Inside

- **Ubuntu 24.04**
- **Rust (via rustup)**
- **Solana CLI (latest stable)**
- **SPL Token CLI**
- **Anchor (via AVM)**
- **Metaboss**
- Build tools and libraries:
  - `build-essential`, `curl`, `git`, `just`
  - `libclang-dev`, `libssl-dev`, `libudev-dev`, `llvm`, `protobuf-compiler`
  - `pkg-config`, `nano`, `sudo`

## Usage

### Build the Image

```bash
docker build -t solana-dev .
````

### Run the Container

```bash
docker run -it --rm solana-dev
```

You will be dropped into a fully functional Bash shell with all tools available in your `$PATH`.

## Quick Start

Inside the container, you can immediately start using Solana tools:

```bash
# Check Solana version
solana --version

# Check Rust version
rustc --version

# Use Anchor
anchor --version

# Use SPL Token CLI
spl-token --help

# Use Metaboss
metaboss --help
```

## AVM and Anchor

This image uses [AVM (Anchor Version Manager)](https://github.com/coral-xyz/anchor) to install and manage Anchor versions:

```bash
# List available versions
avm ls-remote

# Switch to a specific version
avm install 0.29.0
avm use 0.29.0
```

* * *

## Docker Hub Usage

To publish your image to Docker Hub and use it from anywhere:

### Create Dockerfile

Write your build instructions:

```bash
nano Dockerfile
```

### Build Docker Image

```bash
sudo docker build -f Dockerfile -t yourdockerhubuser/image-name .
```

### Login to Docker Hub

```bash
sudo docker login -u <username>
```

### Push the Image

```bash
sudo docker push yourdockerhubuser/image-name
```

### Pull the Image

```bash
sudo docker pull yourdockerhubuser/image-name
```

### Start the Container

```bash
sudo docker run -it yourdockerhubuser/image-name bash
```

* * *

## Cleanup & Optimization

* The image is configured with `noninteractive` frontend to avoid manual prompts during package installation.
* `apt clean`, `autoremove`, and `autoclean` help reduce the image size.

* * *

## Credits

* [Solana Labs](https://solana.com/)
* [Coral Anchor](https://github.com/coral-xyz/anchor)
* [Metaboss](https://github.com/samuelvanderwaal/metaboss)

* * *

## License

This script is open source under the [MIT License](LICENSE).
