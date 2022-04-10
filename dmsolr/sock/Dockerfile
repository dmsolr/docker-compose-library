FROM alpine:3.4

RUN apk add --no-cache gcc libc-dev tcpdump make

RUN mkdir /tmp/sock

RUN cd /tmp/sock \
	&& wget http://www.icir.org/christian/downloads/sock-0.3.2.tar.gz \
	&& tar -zxvf sock-0.3.2.tar.gz \
  && cd sock-0.3.2 \
	&& ./configure --prefix=/ \
  && make install

RUN rm -rf /tmp/sock
 
FROM alpine:3.4
RUN apk add --no-cach tcpdump
COPY --from=0 /bin/sock /usr/local/bin

