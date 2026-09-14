# Third‑party notices

SHIKARDOS AUDIO for Android includes the open‑source components listed below.
Each LGPL component is shipped as its own shared library (`.so`) and is linked
dynamically, so it can be replaced with a compatible build.

If you need the corresponding source code or build instructions and cannot get
them from the links below, open an [issue](https://github.com/89002521040g-sudo/shikardos-audio/issues)
and we will provide them.

---

## FFmpeg 7.1.1

Libraries: `libavcodec.so`, `libavformat.so`, `libavutil.so`, `libswresample.so`.

License: **GNU Lesser General Public License, version 3 or later** (the build
uses `--enable-version3` because it links Mbed TLS). No GPL‑only parts are
enabled. Full text: [licenses/ffmpeg/COPYING.LGPLv3](licenses/ffmpeg/COPYING.LGPLv3)
(which builds on [COPYING.LGPLv2.1](licenses/ffmpeg/COPYING.LGPLv2.1)).

Source: the official, unmodified FFmpeg 7.1.1 release —
https://ffmpeg.org/releases/ffmpeg-7.1.1.tar.xz

Build configuration (arm64‑v8a; armeabi‑v7a differs only in architecture flags):

```
--enable-cross-compile --target-os=android --arch=aarch64 --cpu=armv8-a
--enable-shared --disable-static --enable-pic --disable-programs --disable-doc
--disable-debug --disable-avdevice --disable-swscale --disable-avfilter
--disable-postproc --enable-network --enable-mbedtls --enable-version3
--disable-autodetect --enable-zlib --disable-everything --disable-hwaccels
--enable-protocol='file,http,https,tcp,tls,crypto,httpproxy,data'
--enable-demuxer='ape,wv,tta,mpc,mpc8,flac,mp3,aac,mov,ogg,wav,aiff,asf,dsf,iff,matroska,tak,ac3,eac3,oma,w64,caf,voc,dts,truehd,mlp,amr,shorten,hls,mpegts,loas'
--enable-decoder='ape,wavpack,tta,mpc7,mpc8,alac,flac,mp3float,mp3,aac,aac_latm,vorbis,opus,wmav1,wmav2,wmapro,wmalossless,tak,ac3,eac3,atrac3,atrac3p,dsd_lsbf,dsd_msbf,dsd_lsbf_planar,dsd_msbf_planar,truehd,mlp,dca,shorten,als,amrnb,amrwb,cook,pcm_u8,pcm_s16le,pcm_s16be,pcm_s24le,pcm_s24be,pcm_s32le,pcm_s32be,pcm_f32le,pcm_f32be,pcm_f64le,pcm_alaw,pcm_mulaw'
--enable-parser='flac,mpegaudio,aac,aac_latm,vorbis,opus,ac3,dca,tak,mlp'
--extra-libs='-lmbedtls -lmbedx509 -lmbedcrypto'
```

Toolchain: Android NDK 27.0.12077973, API level 21.

FFmpeg is a trademark of Fabrice Bellard, originator of the FFmpeg project.

---

## Mbed TLS 3.6.7

Used for HTTPS internet radio. Built as static libraries and linked into
`libavformat.so`.

License: Mbed TLS is dual‑licensed under Apache License 2.0 or
GPL‑2.0‑or‑later; this build uses **Apache License 2.0**.
Full text: [licenses/mbedtls/LICENSE](licenses/mbedtls/LICENSE).

Source: https://github.com/Mbed-TLS/mbedtls/releases/tag/mbedtls-3.6.7

---

## libusb 1.0.27

Library: `libusb-1.0.so` — USB access for bit‑perfect output to USB DACs.

License: **GNU Lesser General Public License, version 2.1 or later**.
Full text: [licenses/libusb/COPYING](licenses/libusb/COPYING), authors:
[licenses/libusb/AUTHORS](licenses/libusb/AUTHORS).

Source: https://github.com/libusb/libusb/releases/tag/v1.0.27 — built with
libusb's own Android configuration (`android/config.h`, `android/jni/libusb.mk`).

---

## Oboe

Low‑latency audio output on Android.

License: **Apache License 2.0**. Full text: [licenses/oboe/LICENSE](licenses/oboe/LICENSE).

Source: https://github.com/google/oboe
