FROM projectatomic/atomicapp:0.1.1

MAINTAINER Aaron Weitekamp <aweiteka@redhat.com>

LABEL io.projectatomic.nulecule.providers="docker" \
      io.projectatomic.nulecule.specversion="0.0.2"

ADD /Nulecule /Dockerfile README.md /application-entity/
ADD /artifacts /application-entity/artifacts

LABEL RUN="docker run -it --rm \${OPT1} --privileged -v `pwd`:/atomicapp -v /run:/run -v /:/host --net=host --name \${NAME} -e NAME=\${NAME} -e IMAGE=\${IMAGE} \${IMAGE} \${OPT2} run --ask \${OPT3} /atomicapp" \
