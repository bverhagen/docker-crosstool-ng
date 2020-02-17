docker-crosstool-ng
====================
[![pipeline status](https://gitlab.com/bverhagen/docker-crosstool-ng/badges/master/pipeline.svg)](https://gitlab.com/bverhagen/docker-crosstool-ng/-/commits/master)

Docker images for crosstool-ng

# Pre-built images
Pre-built images can be found on Docker hub at [bverhagen/crosstool-ng](https://hub.docker.com/r/bverhagen/crosstool-ng).

The tags are structured in the following way:

```
<distribution>_<crosstool-ng version>
```
where:
- `<distribution>` is the desired base distribution to use for crosstool-ng.
  Currently supported distributions are:
    - Debian: Latest stable and testing
    - Ubuntu: Latest LTS and latest stable
- `<crosstool-ng version>` is the target crosstool-ng version to use.
  If you want to automatically follow the latest stable crosstool-ng release, use _latest_.

# Usage
1. Pull the desired pre-built image
1. Make sure the desired input and output folder (`CT_PREFIX_DIR` variable in your crosstool-ng config) is writable by all users
1. Run the image by:
    - Mounting the input and output folder in the container
    - appending crosstool-ng specific commands to the end of the command line
    ```
    $ docker run --rm --volume=<host output folder>:<CT_PREFIX_DIR>:rw --volume=<host input folder>:/workspace:rw ctng-example "--directory=/workspace" build
    ```

    _Note_: Make sure to to replace all variables between angular brackets `<>` with their respective values.
