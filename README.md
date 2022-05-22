# Dockerfile for build

- Build docker:
    ```
    cd <source-path>
    docker build -t eraa/env-build:v1 . -f .\dockerfile-build
    ```
- Run docker:
    ```
    docker run -it -v <source-path>:/source eraa/env-build::v1 bash
    ```


# Old docker document

- Build docker image
    - Build for develop
        ```
        docker build \
            --build-arg REMOTE_PASSWORD=<Password user remote> \
            --build-arg ROOT_PASSWORD=<Password user root> \
            --build-arg ARG_SA_PASSWORD=<Password user sa of sql server> \
            -t <image-name>:<version> . -f .\Dockerfile-env
        ```
    - Build for release
        ```
        docker build -t <image-name>:<version> . -f .\Dockerfile-release
        ```
    - Build custom mssql
        ```
        docker build \
            --build-arg ROOT_PASSWORD=<Password user root> \
            --build-arg ARG_SA_PASSWORD=<Password user sa of sql server> \
            -t <image-name>:<version> . -f .\Dockerfile-sql
        ```

- Run docker
    - Run environment
        ```
        docker run -e "MAX_RAM_USAGE_SQL=2048" \
        -p 1433:1433 -p 22:22 -p 80:80 -p 443:443 -p 7005:7005 \
        -d -t `<image-name>`
        ```
        - `-p`: `<port export to local>:<port from container>`
        - `-e`: environment avalible 
    - Run custom sql
        ```
        docker run -e "MAX_RAM_USAGE_SQL=2048" \
        -p 1433:1433 -d -t `<image-name>`
        ```