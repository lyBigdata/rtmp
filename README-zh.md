# docker nginx rtmp
一个Dockerfile从源代码安装NGINX，nginx-rtmp-module和FFmpeg
HLS实时流媒体的默认设置。 建立在Alpine Linux上。

* Nginx 1.13.9 (compiled from source)
* nginx-rtmp-module 1.2.1 (compiled from source)
* ffmpeg 3.4.2 (compiled from source)
* Default HLS settings (See: [nginx.conf](nginx.conf))

[![Docker Stars](https://img.shields.io/docker/stars/alfg/nginx-rtmp.svg)](https://hub.docker.com/r/alfg/nginx-rtmp/)
[![Docker Pulls](https://img.shields.io/docker/pulls/alfg/nginx-rtmp.svg)](https://hub.docker.com/r/alfg/nginx-rtmp/)
[![Docker Automated build](https://img.shields.io/docker/automated/alfg/nginx-rtmp.svg)](https://hub.docker.com/r/alfg/nginx-rtmp/builds/)
[![Build Status](https://travis-ci.org/alfg/docker-nginx-rtmp.svg?branch=master)](https://travis-ci.org/alfg/docker-nginx-rtmp)

## 用法:

### 服务端
* 拉取docker镜像并运行:
```
docker pull alfg/nginx-rtmp
docker run -it -p 1935:1935 -p 8080:80 --rm jun3/rtmp
```
或者 

* 构建docker镜像并运行:
```
docker build -t jun3/rtmp .
docker run -it -p 1935:1935 -p 8080:80 --rm jun3/rtmp
```

* 将实时内容串流到服务端:
```
rtmp://<server ip>:1935/stream/$STREAM_NAME
```

### OBS配置
* 流类型: `自定义流媒体服务器`
* 流地址: `rtmp://localhost:1935/stream`
* 流密钥: `hello`

### 观看流
* 在Safari，VLC或任何HLS播放器中，打开:
```
http://<server ip>:8080/live/$STREAM_NAME.m3u8
```
* 例如: `http://localhost:8080/live/hello.m3u8`


### FFMPEG构建
```
ffmpeg version 3.4.2 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 5.3.0 (Alpine 5.3.0)
  configuration: --enable-version3 --enable-gpl --enable-nonfree --enable-small --enable-libmp3lame --enable-libx264 --enable-libx265 --enable-libvpx --enable-libtheora --enable-libvorbis --enable-libopus --enable-libfdk-aac --enable-libass --enable-libwebp --enable-librtmp --enable-postproc --enable-avresample --enable-libfreetype --enable-openssl --disable-debug
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100

  configuration:
    --enable-version3
    --enable-gpl
    --enable-nonfree
    --enable-small
    --enable-libmp3lame
    --enable-libx264
    --enable-libx265
    --enable-libvpx
    --enable-libtheora
    --enable-libvorbis
    --enable-libopus
    --enable-libfdk-aac
    --enable-libass
    --enable-libwebp
    --enable-librtmp
    --enable-postproc
    --enable-avresample
    --enable-libfreetype
    --enable-openssl
    --disable-debug
```

## 资源
* https://alpinelinux.org/
* http://nginx.org
* https://github.com/arut/nginx-rtmp-module
* https://www.ffmpeg.org
* https://obsproject.com
