# GitHub Actions Workflows

This directory contains GitHub Actions workflows for the WhatCoin project.

## Workflows

### 1. CI/CD Pipeline (`ci.yml`)
The main comprehensive CI/CD pipeline that includes:

- **Multi-platform builds**: Ubuntu (GCC/Clang), macOS (Clang), Windows (MSVC)
- **Dependency installation**: All required libraries and tools
- **Code linting**: Clang-format checks
- **Security scanning**: CodeQL analysis
- **Release automation**: Automatic release creation with artifacts

**Triggers:**
- Push to `master`, `main`, or `develop` branches
- Pull requests to `master`, `main`, or `develop` branches
- Release publication events

### 2. Quick CI (`quick-ci.yml`)
A simplified CI workflow for faster feedback:

- **Single platform**: Ubuntu only
- **Essential dependencies**: Core build requirements
- **Quick build and test**: Optimized for speed

**Triggers:**
- Push to `master`, `main`, or `develop` branches
- Pull requests to `master`, `main`, or `develop` branches

### 3. Dependency Cache (`dependency-cache.yml`)
Optimizes build times by caching dependencies:

- **vcpkg cache**: Caches vcpkg dependencies
- **Build cache**: Caches build artifacts

## Dependencies

The workflows install the following dependencies:

### Ubuntu
- `build-essential` - C/C++ compiler and build tools
- `cmake` - Build system
- `pkg-config` - Package configuration
- `libboost-all-dev` - Boost C++ libraries
- `libssl-dev` - OpenSSL development files
- `libzmq3-dev` - ZeroMQ library
- `libpgm-dev` - OpenPGM library
- `libunbound-dev` - DNS resolver library
- `libsodium-dev` - Cryptography library
- `libunwind8-dev` - Stack unwinding library
- `liblzma-dev` - LZMA compression library
- `libreadline6-dev` - Readline library
- `libldns-dev` - DNS toolkit library

### macOS
- `cmake` - Build system
- `pkg-config` - Package configuration
- `boost` - Boost C++ libraries
- `openssl` - OpenSSL library
- `zeromq` - ZeroMQ library
- `libpgm` - OpenPGM library
- `unbound` - DNS resolver library
- `libsodium` - Cryptography library
- `libunwind` - Stack unwinding library
- `xz` - LZMA compression library
- `readline` - Readline library
- `ldns` - DNS toolkit library

### Windows
- `vcpkg` - C++ package manager
- Dependencies installed via vcpkg: `boost`, `openssl`, `zeromq`, `libsodium`

## Usage

1. **For development**: The Quick CI workflow provides fast feedback
2. **For releases**: The full CI/CD pipeline ensures multi-platform compatibility
3. **For security**: CodeQL analysis runs automatically on all builds

## Customization

To modify the workflows:

1. Edit the appropriate `.yml` file in `.github/workflows/`
2. The workflows use GitHub's latest actions and best practices
3. Dependencies can be added/removed as needed
4. Build configurations can be adjusted in the CMake steps

## Troubleshooting

### Common Issues

1. **Build failures**: Check that all dependencies are properly installed
2. **Test failures**: Ensure the test suite is compatible with the build environment
3. **Cache issues**: Clear the cache by pushing a commit with `[skip cache]` in the message

### Debugging

- Check the Actions tab in your GitHub repository
- Review the logs for specific error messages
- Verify that the workflow files are properly formatted YAML 