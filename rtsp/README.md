1. Install dependencies:

```
$ sudo apt install ffmpeg
```

2. Download and run media server:

```
$ cd
$ wget https://github.com/bluenviron/mediamtx/releases/download/v1.11.0/mediamtx_v1.11.0_linux_arm64v8.tar.gz
$ tar xf mediamtx_v1.11.0_linux_arm64v8.tar.gz
$ ./mediamtx
```

3. Run ffmpeg:

```
$ ffmpeg -f video4linux2 -video_size 1280x720 -i /dev/video1 -f rtsp rtsp://localhost:8554/mystream
```
Although ffmpeg listens on localhost, mediamtx listens on `0.0.0.0`, making the RTSP stream accessible from the outside.

4. Watch the stream:

```
rtsp://<ip>:8554/mystream
```
