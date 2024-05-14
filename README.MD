## docker-compose-project 入门基本概念

1. What is Docker Compose?

2. What problems it solves?
    - demo1:
        2.1 create a docker network

        ```shell
        docker network create mongo-network
        docker network ls
        ```

        2.2 start mongodb conatiner

        ```shell
        docker run -d \
        -p 27017:27017 \
        -e MONGO_INITDB_ROOT_USERNAME=mongoadmin \
        -e MONGO_INITDB_ROOT_PASSWORD=secret \
        --network mongo-network \
        --name mongodb \
        mongo
        ```

        2.3 start mongo express container

        ```shell
        docker run -d \
        -p 8081:8081 \
        -e ME_CONFIG_MONGODB_ADMINUSERNAME=mongoadmin \
        -e ME_CONFIG_MONGODB_ADMINPASSWORD=secret \
        -e ME_CONFIG_MONGODB_SERVER=mongodb
        --network mongo-network \
        --name mongo-express \
        mongo-express

        docker ps 
        docker logs <containerId>
        admin:pass

        ```

    - configure and run our services
        2.4 You use a single YAML file to configure and maintain your application's services
        2.5 With a single command, you create and start all the service from your configuration
        2.6 Declarative definition

        2.7 map docker commands to definition(将docker的命令转化成docker的定义)

        2.8 docker 先停止服务，然后删除
            ```shell
            docker stop <containerId>
            docker rm <containerName>
            docker-compose -f mongo-service.yaml up
            ```
        这里会根据项目目录默认创建一个网络: directory_default,其次撞见容器的时候会默认是这样的
        directory-containerName-1
            ```shell
            docker-compose -f mongo-service.yaml up -d
            docker-compose -f mongo-service.yaml down
            docker-compose -f mongo-service.yaml stop
            docker-compose -f mongo-service.yaml start
            ```
        这里需要理解up and down 和 start and stop之间的区别

3. Common use case.

4. Hands-on demos.

5. Limitations of Docker Compose

## Dcoker 基本概念

1. What containers are?

2. What images are?

3. What probles Docker solves?

4. Main Dcoker commands.

5. Dockerize Application
