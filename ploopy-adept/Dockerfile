FROM debian:stable-slim

RUN apt update && apt install -y --no-install-recommends python3-pip git sudo
RUN python3 -m pip install --break-system-packages --user qmk
RUN echo 'PATH="$HOME/.local/bin:$PATH"' >> $HOME/.bashrc
RUN cd /root/ && git clone --depth=1 https://github.com/qmk/qmk_firmware.git \
    && qmk_firmware && git remote add vial https://github.com/vial-kb/vial-qmk.git \
    && git pull vial vial
ENV PATH="$HOME/.local/bin:$PATH"
RUN /root/.local/bin/qmk setup --yes
