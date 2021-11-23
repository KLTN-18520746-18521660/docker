# Dockerfile for build and runtime environment

* Build docker image
    - Build for develop
    ```
    docker build -t <image-name>:<version> . -f .\Dockerfile-develop
    ```
    - Build for release
    ```
    docker build -t <image-name>:<version> . -f .\Dockerfile-release
    ```

* Run docker
    ```
    docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<Thesis1234>" \
    -p 1433:1433 -p 22:22 -p 80:80 \
    -d -t `<image-name>`
    ```
    * `-p`: `<port export to local>:<port from container>`
    * `-e`: environment avalible 