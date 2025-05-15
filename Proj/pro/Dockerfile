FROM maven:3.9.2-amazoncorretto-11 as builder

# 创建/app目录并将当前文件夹下的所有内容复制到其中
WORKDIR /app
COPY . /app

# 设置Maven镜像源为阿里云
RUN mkdir -p /root/.m2 && \
    echo "<settings><mirrors><mirror><id>aliyun</id><mirrorOf>central</mirrorOf><url>https://maven.aliyun.com/repository/central</url></mirror></mirrors></settings>" > /root/.m2/settings.xml

# Build a release artifact.
RUN mvn package -DskipTests

# Run the web service on container startup.
CMD ["java", "-jar", "/app/target/pro-0.0.1-SNAPSHOT.jar"]