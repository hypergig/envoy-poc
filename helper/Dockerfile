FROM ubuntu
RUN apt-get update \
 && apt-get -y install nghttp2 telnet dnsutils curl nmap
 # don't blow the cache, helpful for quick install of tools

ENTRYPOINT ["tail", "-f", "/dev/null"]
