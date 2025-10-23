FROM invent-registry.kde.org/neon/docker-images/plasma:user

ENV TZ=Asia/Tokyo
ENV DISPLAY=:7
ENV KDE_FULL_SESSION=true
ENV SHELL=/bin/bash
ENV HOME=/home/neon
ENV XDG_RUNTIME_DIR=/run/neon

RUN sudo apt-get update -qq
RUN sudo apt-get install -y fcitx5-mozc
RUN sudo apt-get remove -y --purge im-config anthy-common maliit-framework maliit-keyboard

RUN sudo apt-get install -f
RUN sudo apt-get autoremove -y

COPY ./home/neon/.config/fcitx5 /home/neon/.config/fcitx5
RUN sudo chown neon:neon -R /home/neon/.config/fcitx5/

COPY ./etc/default/keyboard /etc/default/keyboard
RUN dpkg-reconfigure keyboard-configuration --frontend noninteractive

WORKDIR /home/neon
CMD startplasma-x11
