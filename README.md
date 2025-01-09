# Uncommon Dockerfile Bug: Using `ubuntu:latest`

This repository demonstrates a common but often overlooked issue in Dockerfiles: using the `ubuntu:latest` tag. While seemingly convenient, it lacks reproducibility and can lead to unexpected behavior between builds due to updates in the underlying Ubuntu image.

**The Bug:**

The provided `Dockerfile` uses `FROM ubuntu:latest`. This makes the build non-deterministic.  A build today might work differently than a build tomorrow, as `latest` updates automatically.

**The Solution:**

The `Dockerfile.fixed` shows the corrected version.  It specifies a particular Ubuntu version (`ubuntu:22.04`), ensuring consistency and predictability across builds.  Always prefer a specific version tag for production-level Docker images.

**How to Reproduce:**

1. Clone this repository.
2. Build both Dockerfiles: `docker build -t latest-ubuntu -f Dockerfile .` and `docker build -t specific-ubuntu -f Dockerfile.fixed .`
3. Compare the results.  While visually similar, their underlying images differ, leading to potential runtime inconsistencies.

This example emphasizes best practices for maintaining reproducible Docker builds and is relevant to all languages and frameworks using Docker.