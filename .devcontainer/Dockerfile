FROM mcr.microsoft.com/devcontainers/base:ubuntu

# 安装 Maven
ENV MAVEN_VERSION=3.8.8
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    && mkdir -p /opt/maven \
    && curl -fsSL https://archive.apache.org/dist/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
    | tar xzf - -C /opt/maven --strip-components=1 \
    && ln -s /opt/maven/bin/mvn /usr/local/bin/mvn \
    && rm -rf /var/lib/apt/lists/*

# 安装 Gradle
ENV GRADLE_VERSION=8.14.3
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    unzip \
    && mkdir -p /opt/gradle \
    && curl -fsSL https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o /tmp/gradle.zip \
    && unzip -q /tmp/gradle.zip -d /tmp/gradle-temp \
    && mv /tmp/gradle-temp/gradle-${GRADLE_VERSION}/* /opt/gradle/ \
    && rmdir /tmp/gradle-temp/gradle-${GRADLE_VERSION} /tmp/gradle-temp \
    && ln -s /opt/gradle/bin/gradle /usr/local/bin/gradle \
    && rm -f /tmp/gradle.zip \
    && rm -rf /var/lib/apt/lists/*

ENV PATH="/opt/maven/bin:/opt/gradle/bin:${PATH}"
