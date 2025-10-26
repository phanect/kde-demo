FROM invent-registry.kde.org/neon/docker-images/plasma:user

ENV TZ=Asia/Tokyo
ENV DISPLAY=:7
ENV KDE_FULL_SESSION=true
ENV SHELL=/bin/bash
ENV HOME=/home/neon
ENV XDG_RUNTIME_DIR=/run/neon

RUN echo keyboard-configuration keyboard-configuration/layout select 'Japanese' | sudo debconf-set-selections && \
    echo keyboard-configuration keyboard-configuration/layoutcode select 'jp' | sudo debconf-set-selections

RUN sudo apt-get update -qq
RUN sudo apt-get install -y fcitx5-mozc
RUN sudo apt-get remove -y --purge im-config anthy-common maliit-framework maliit-keyboard

# RUN curl -sSLO https://cdn.fastly.steamstatic.com/client/installer/steam.deb
# RUN sudo dpkg -i ./steam.deb
# RUN rm -f steam.deb

RUN sudo apt-get install -f
RUN sudo apt-get autoremove -y

COPY ./home/neon/.config/fcitx5 /home/neon/.config/fcitx5
RUN sudo chown neon:neon -R /home/neon/.config/fcitx5/



# COPY ./etc/default/keyboard /etc/default/keyboard
# # RUN sudo dpkg-reconfigure console-setup --frontend noninteractive
# RUN sudo dpkg-reconfigure keyboard-configuration --frontend noninteractive
# RUN setupcon --keyboard-only

WORKDIR /home/neon
CMD startplasma-x11
