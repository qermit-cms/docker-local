FROM jenkins/jenkins

USER root

# Install Java
ENV JAVA_HOME /usr/lib/java
RUN url="http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz" \
 && sha256="e8a341ce566f32c3d06f6d0f0eeea9a0f434f538d22af949ae58bc86f2eeaae4" \
 && curl -L -H "Cookie: oraclelicense=accept-securebackup-cookie" -k "$url" -o "oracle-jdk.tar.gz" \
 && echo "$sha256  oracle-jdk.tar.gz" | sha256sum -c \
 && mkdir -p $JAVA_HOME \
 && tar -zxf oracle-jdk.tar.gz --strip 1 -C $JAVA_HOME \
 && rm oracle-jdk.tar.gz \
 && apt-get update \
 && apt-get install -y --no-install-recommends unzip \
 && secUrl="http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip" \
 && sha256="f3020a3922efd6626c2fff45695d527f34a8020e938a49292561f18ad1320b59" \
 && curl -L -H "Cookie: oraclelicense=accept-securebackup-cookie;" -k "$secUrl" -o "jce-policy.zip"  \
 && unzip -jo -d "${JAVA_HOME}/jre/lib/security" "jce-policy.zip" \
 && echo "$sha256  jce-policy.zip" | sha256sum -c \
 && rm jce-policy.zip
ENV PATH "$JAVA_HOME/bin:$PATH"

# Install Maven


# Back to the regular jenkins user
USER jenkins
