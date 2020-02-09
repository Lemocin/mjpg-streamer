FROM alpine

MAINTAINER Kim Müller <https://github.com/Lemocin>
LABEL Description="A minimal Docker image for mjpg_streamer." Version="0.4"


COPY * /mjpeg_streamer

WORKDIR /mjpg-streamer

RUN apk add cmake make jpeg-dev gcc libgcc linux-headers 
RUN make  
RUN make install 
RUN chmod +x docker-start.sh

EXPOSE 8080/TCP

ENTRYPOINT ["/mjpg-streamer/mjpg-streamer-experimental/docker-start.sh", "output_http.so -w ./www"]

CMD ["input_httpout.so -H pizero -p 8080"]