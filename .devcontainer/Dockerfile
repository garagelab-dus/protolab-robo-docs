# Use Ubuntu as the base image
FROM mcr.microsoft.com/devcontainers/base:debian

# Set environment variables to avoid interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Install system dependencies
RUN apt-get update && apt-get install -y \
    wget \
    python3 \
    python3-pip \
    && apt-get clean

# Install Miniconda
# RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh && \
#     bash /tmp/miniconda.sh -b -p /opt/conda && \
#     rm /tmp/miniconda.sh && \
#     /opt/conda/bin/conda clean -afy

# Add Conda to PATH
# ENV PATH="/opt/conda/bin:$PATH"

# RUN pip install mkdocs-material

# Set the working directory
WORKDIR /workspace

# Default command
CMD ["bash"]
