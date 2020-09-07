FROM mhart/alpine-node:12
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
RUN apk add --no-cache make gcc g++ libnsl libnsl-dev freetype freetype-dev
RUN cd / && \
    wget -nv https://github.com/Caltech-IPAC/Montage/tarball/4.1 && \
    tar -xvf 4.1 && \
    rm -f 4.1 && \
    mv Caltech-IPAC-Montage-1762941 Montage && \
    cd Montage && \
    make && \
    rm -rf MontageLib && \
    rm -rf Montage
COPY handler.js ./
ENV PATH $PATH:/Montage/bin:/node_modules/.bin
CMD [ "npm", "start" ]
