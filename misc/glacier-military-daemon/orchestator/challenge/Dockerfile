FROM debian:stable-slim

RUN DEBIAN_FRONTEND=noninteractive; \
    apt-get -y update; \
    apt-get -y install zsh file; \
    rm -rf /var/lib/apt/lists/*;

RUN adduser --home /home/sci33098 --shell /bin/zsh sci33098
RUN usermod --shell /sbin/nologin root

COPY grhealth /sbin/
RUN chown root:root /sbin/grhealth
RUN chmod +s /sbin/grhealth
RUN chmod +x /sbin/grhealth

WORKDIR /home/sci33098

COPY zshrc .zshrc
COPY Makefile .
COPY main.c .
COPY glacier_resilience.h .

USER 1000:1000

CMD ["zsh"]
