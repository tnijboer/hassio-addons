ARG BUILD_FROM=hassioaddons/base:2.3.1
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Copy Python requirements file
COPY requirements.txt /tmp/

# Build
RUN \
    apk add --no-cache \
    apk-tools=2.10.1-r0 \
    bash=4.4.19-r1 \
    ca-certificates=20171114-r3 \
    curl=7.61.1-r1 \
    nginx=1.14.2-r0 \
    python3=3.6.6-r0 \
    redis=4.0.11-r0 \
    nginx-mod-http-lua=1.14.2-r0 \
    lua-resty-http=0.12-r1 \
    \
    && pip3 install --no-cache-dir -r /tmp/requirements.txt \
    \
    && rm -f -r /tmp/*

# Copy root filesystem
COPY rootfs /

# Build arguments
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Custom Component Store" \
    io.hass.description="Manage all your custom components with ease" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Antoni K <antoni-k@outlook.com>" \
    org.label-schema.description="Manage all your custom components with ease" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="Custom Component Store"\
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://github.com/antoni-k/hassio-addons/" \
    org.label-schema.usage="https://github.com/ludeeus/custom-component-store/blob/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    # org.label-schema.vcs-url="" \
    org.label-schema.vendor="Miscellaneous Hass.io Addons"