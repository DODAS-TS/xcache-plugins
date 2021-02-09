FROM opensciencegrid/software-base:fresh
ENV XRD_VERSION=5.0.3

RUN yum groupinstall -y "Development tools"

ENV XRD_VERSION=5.1.0
RUN yum install --enablerepo=osg* -y xrootd-server-$XRD_VERSION xrootd-server-devel-$XRD_VERSION \
                   xrootd-devel-$XRD_VERSION sudo \
                   libcurl libcurl-devel jsoncpp-devel git cmake \
                   pcre-devel

RUN mkdir /tmp/decisionlib
COPY ./CMakeLists.txt /tmp/decisionlib/CMakeLists.txt
COPY ./src /tmp/decisionlib/src
COPY ./cmake /tmp/decisionlib/cmake

RUN cd /tmp/decisionlib \
       && mkdir -p build && cd build \
   && cmake .. -DCMAKE_INSTALL_PREFIX=/ \
   && make install


