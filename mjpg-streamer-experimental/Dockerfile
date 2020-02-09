FROM alpine

MAINTAINER Kim Müller <https://github.com/Lemocin>
LABEL Description="A minimal Docker image for mjpg_streamer." Version="0.4"


COPY . /mjpg-streamer-experimental/

WORKDIR /mjpg-streamer-experimental
RUN ls -lisah
RUN apk add cmake make jpeg-dev gcc g++ linux-headers 
RUN cd /mjpg-streamer-experimental
RUN make  
RUN make install 
RUN apk del cmake make jpeg-dev gcc g++ linux-headers
RUN chmod +x docker-start.sh

EXPOSE 8080/TCP

ENTRYPOINT ["/mjpg-streamer-experimental/docker-start.sh", "output_http.so -w ./www"]

CMD ["input_httpout.so -H pizero -p 8080"]
