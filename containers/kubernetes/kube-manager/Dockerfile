ARG CONTRAIL_REGISTRY
ARG CONTRAIL_CONTAINER_TAG
FROM ${CONTRAIL_REGISTRY}/contrail-base:${CONTRAIL_CONTAINER_TAG}

ARG CONTAINER_NAME

RUN yum install -y python-eventlet python-setuptools python-kazoo \
                   python-bitarray python-pycassa python-bitstring \
                   contrail-kube-manager python-enum34 && \
    yum clean all -y && \
    rm -rf /var/cache/yum

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
CMD ["/usr/bin/python", "/usr/bin/contrail-kube-manager", "-c", "/etc/contrail/contrail-kubernetes.conf"]

LABEL net.juniper.contrail.pod=kubernetes
LABEL net.juniper.contrail.service=kube-manager
LABEL net.juniper.contrail.container.name=$CONTAINER_NAME
