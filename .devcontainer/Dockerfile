ARG VARIANT="stable"
FROM bellyels/modus-linux-30:${VARIANT}

USER root
RUN mkdir /home/vscode
WORKDIR /home/vscode

RUN groupadd -r vscode && \
    useradd --no-log-init -r -g vscode -s /bin/bash vscode && \
    chown -R vscode /home/vscode

USER vscode

RUN mkdir /home/vscode/mtb-workspace
RUN mkdir /home/vscode/mtb-workspace/mtb-example-hal-hello-world
WORKDIR /home/vscode/mtb-workspace/mtb-example-hal-hello-world

ENV CY_TOOLS_PATHS=/opt/ModusToolbox/tools_3.0

COPY --chown=vscode:vscode . .

ARG TARGET="CY8CPROTO-062-4343W"
RUN /opt/ModusToolbox/tools_3.0/library-manager/library-manager-cli -p . --add-bsp-name ${TARGET}
