FROM ubuntu:20.04 AS build

ARG HADOLINT_VERSION=2.5.0

RUN apt-get update \
  && apt-get install --no-install-recommends -y ca-certificates curl xz-utils \
  && rm -rf /var/lib/apt/lists/* \
  && curl -o /usr/local/bin/hadolint -L https://github.com/hadolint/hadolint/releases/download/v${HADOLINT_VERSION}/hadolint-Linux-x86_64 \
  && chmod +x /usr/local/bin/hadolint

FROM scratch
COPY --from=build /usr/local/bin/hadolint /bin/
CMD ["/bin/hadolint", "-"]
