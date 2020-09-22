FROM ruby:2.7.1

ARG USERNAME=app
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
  && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
  && apt-get update \
  && apt-get install -y sudo \
  && echo "$USERNAME ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME \
  && chmod 0440 /etc/sudoers.d/$USERNAME

ENV BUNDLE_PATH=/app/vendor/bundle
RUN mkdir -p /app /original $BUNDLE_PATH
RUN chown -R $USERNAME /app /original $BUNDLE_PATH

USER $USERNAME

WORKDIR /app
