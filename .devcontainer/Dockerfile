FROM mcr.microsoft.com/devcontainers/python:3.10

# Upgrade pip and install flit
RUN python -m pip install --upgrade pip==24.3.1 --no-cache-dir \
    && python -m pip install flit==3.9.0 --no-cache-dir

# Create a non-root user
RUN useradd -m dockerfileuser

# Set the environment variable
ENV FLIT_ROOT_INSTALL=1

# Switch to non-root user
USER dockerfileuser

# Copy pyproject.toml file
COPY pyproject.toml .

# Install dependencies
RUN touch README.md \
    && mkdir -p src/python_package \
    && python -m flit install --only-deps --deps develop \
    && rm -r pyproject.toml README.md src

# Set the default user to non-root
USER dockerfileuser

# FROM mcr.microsoft.com/devcontainers/python:3.10

# RUN python -m pip install --upgrade pip \
#     && python -m pip install 'flit>=3.8.0'

# ENV FLIT_ROOT_INSTALL=1

# COPY pyproject.toml .
# RUN touch README.md \
#     && mkdir -p src/python_package \
#     && python -m flit install --only-deps --deps develop \
#     && rm -r pyproject.toml README.md src
