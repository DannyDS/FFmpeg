FFmpeg README
=============

FFmpeg is a collection of libraries and tools to process multimedia content
such as audio, video, subtitles and related metadata.

## Changes for Onvif streaming

* RTSP.c parses clock value from rtsp header to get stream start time and end time
* RTSPDec.c uses unused Opaque value from AV_Context so we can pass a Clock value to set stream start point
* RTPDec.c stores RTP header extension in AV_Frame_Side_Data so we can extract frame time and when the stream has ended

##Building using VCPKG

* To build with VCPKG open vcpkg\ports\ffmpeg\portfile.cmake
* Change REPO to point to 'DannyDS/FFmpeg'
* Change Ref to point to the latest branch 'N6.1.1-onvif'
* Run VCPKG install FFmpeg and it will fail due to mismatch of the SHA512, it will print out what the hash should be copy it and replace SHA512 in the cmake file
* If you want to rebuild FFmpeg first run vcpkg remove ffmpeg
* Delete the FFmpeg folder in vcpkg/buildtrees
* Delete User\AppData\Local\vcpkg\archives

## Libraries

* `libavcodec` provides implementation of a wider range of codecs.
* `libavformat` implements streaming protocols, container formats and basic I/O access.
* `libavutil` includes hashers, decompressors and miscellaneous utility functions.
* `libavfilter` provides means to alter decoded audio and video through a directed graph of connected filters.
* `libavdevice` provides an abstraction to access capture and playback devices.
* `libswresample` implements audio mixing and resampling routines.
* `libswscale` implements color conversion and scaling routines.

## Tools

* [ffmpeg](https://ffmpeg.org/ffmpeg.html) is a command line toolbox to
  manipulate, convert and stream multimedia content.
* [ffplay](https://ffmpeg.org/ffplay.html) is a minimalistic multimedia player.
* [ffprobe](https://ffmpeg.org/ffprobe.html) is a simple analysis tool to inspect
  multimedia content.
* Additional small tools such as `aviocat`, `ismindex` and `qt-faststart`.

## Documentation

The offline documentation is available in the **doc/** directory.

The online documentation is available in the main [website](https://ffmpeg.org)
and in the [wiki](https://trac.ffmpeg.org).

### Examples

Coding examples are available in the **doc/examples** directory.

## License

FFmpeg codebase is mainly LGPL-licensed with optional components licensed under
GPL. Please refer to the LICENSE file for detailed information.

## Contributing

Patches should be submitted to the ffmpeg-devel mailing list using
`git format-patch` or `git send-email`. Github pull requests should be
avoided because they are not part of our review process and will be ignored.
