FROM ghcr.io/mrsimonemms/gitpod-centos-base-image:latest

### Node.js ###
LABEL dazzle/layer=lang-node
LABEL dazzle/test=tests/lang-node.yaml
USER gitpod
ENV NODE_VERSION=16.13.0
ENV TRIGGER_REBUILD=1
RUN curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | PROFILE=/dev/null bash \
  && bash -c ". .nvm/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && npm install -g typescript yarn node-gyp" \
  && echo ". ~/.nvm/nvm-lazy.sh"  >> /home/gitpod/.bashrc.d/50-node
# above, we are adding the lazy nvm init to .bashrc, because one is executed on interactive shells, the other for non-interactive shells (e.g. plugin-host)
COPY --chown=gitpod:gitpod nvm-lazy.sh /home/gitpod/.nvm/nvm-lazy.sh
ENV PATH=$PATH:/home/gitpod/.nvm/versions/node/v${NODE_VERSION}/bin

USER gitpod
