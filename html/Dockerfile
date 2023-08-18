FROM python:slim
MAINTAINER Denis Bitouzé <denis.bitouze@univ-littoral.fr>

LABEL org.opencontainers.image.authors = "Mirounga Sphinx Team <https://github.com/mga-sphinx> and Denis Bitouzé <https://github.com/dbitouze>"
LABEL org.opencontainers.image.documentation = "https://sphinx-doc.org/"
LABEL org.opencontainers.image.source = "https://github.com/dbitouze/docker-sphinx"
LABEL org.opencontainers.image.version = "7.1.2"
LABEL org.opencontainers.image.licenses = "BSD-2-Clause"
LABEL org.opencontainers.image.description = "HTML container image for Sphinx"

WORKDIR /docs
RUN apt-get update \
 && apt-get install --no-install-recommends -y \
      graphviz \
      imagemagick \
      make \
      git-restore-mtime \
 && apt-get autoremove \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rf /tmp/* /var/tmp/* \
 && rm -f /etc/ssh/ssh_host_*

RUN python3 -m pip install --no-cache-dir -U pip
RUN python3 -m pip install --no-cache-dir Sphinx==7.1.2 Pillow \
      furo \
      sphinx_comments \
      sphinx_design \
      sphinxext.opengraph \
      myst_parser \
      linkify-it-py
      
CMD ["make", "html"]
