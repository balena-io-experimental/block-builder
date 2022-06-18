ARG NAMESPACE=resin
ARG TAG=latest
FROM ${NAMESPACE}/yocto-block-build-env:${TAG} AS block_builder
ARG BLOCK
ARG MACHINE
ARG VERBOSE
ARG ARCH_LIST

COPY contract.json install_packages /work/
RUN mkdir "/ipk"
COPY ipk /ipk

#TODO: Remove this
ENV BRANCH=alexgg/deploy-hostos
RUN git clone -b "${BRANCH}" https://github.com/balena-os/balena-yocto-scripts.git /scripts && \
		./install_packages "/block"

FROM scratch
COPY --from=block_builder /block /
