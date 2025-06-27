## FFmpeg-vaapi and FFmpeg-qsv upstream patches commits tested:

cartwheel-ffmpeg: https://github.com/intel/cartwheel-ffmpeg/releases/tag/2025q1 (tag: 2025q1)

## Supported Intel Platforms:
- PTL (Panther Lake - experimental)
- BMG (Battlemage)
- ARL (Arrow Lake)
- LNL (Lunar Lake)
- MTL (Meteor Lake)
- DG2 (Discrete Graphics 2)
- ADL-S (Alder Lake-S/P/N)
- TGL (Tiger Lake)
- CFL (Coffee Lake)

## Tested Features:

- Decode: VVC (8/10bit), AVC/H264, HEVC/H265 (8/10/12bit), AV1 (8/10bit), VVC, VP9 (8/10/12bit), VP8, JPEG/MJPEG, MPEG2
- Encode: AV1 (8/10), AVC/H264, HEVC/H265 (8/10/12bit), VP9 (8/10bit), VP8, JPEG/MJPEG, MPEG2
- VPP: procamp (brightness/contrast/saturation/hue), csc, deinterlace, denoise, scale, sharpen, mirroring, rotation, transpose

## Supported Features among Intel platforms:

For features supported on each Intel platform, please refer to links below:

- decode/encode features: https://github.com/intel/media-driver/#decodingencoding-features
- VPP features: https://github.com/intel/media-driver/#video-processing-features

## Build configures
GStreamer build configure:

```shell
./configure --prefix=$ROOT_INSTALL_DIR --enable-shared --enable-vaapi --enable-libvpl
make
make install
```

## Reference Configure Used: Intel Libva/iHD driver, MediaSDK, oneVPL and oneVPL GPU Runtime
- VPL Dispatcher: intel/libvpl@c45b5d7
- VPL Runtime: intel/vpl-gpu-rt@93b58fb
- Media SDK: Intel-Media-SDK/MediaSDK@7a72de3
- Media driver: intel/media-driver@cf4cd1d
- Libva: intel/libva@0d1d351
- Libva-utils: intel/libva-utils@deff975
- Gmmlib: intel/gmmlib@af5f033
- Binary: these components binary of media stack (LibVA/iHD/VPL/GmmLib) can be found from https://github.com/intel/libvpl/releases

## New Details
2025Q1:
- FFmpeg experimental support for PTL
- Clean up cartwheel-ffmpeg patches to support 2025WW19 ffmpeg

2024Q4:
- FFmpeg added Intel new BMG platforms support

2024Q3:
- FFmpeg added Intel new LNL and ARL platforms support 
- firstly added Windows OS ffmpeg-qsv on D3D11 support for Intel LNL and Gen12(TGL)+ platforms
- firstly added Windows OS ffmpeg-d3d11 (only decode) support for Intel LNL and Gen12(TGL)+ platforms
- ffmpeg-vaapi and ffmpeg-qsv supported Intel new XE driver
- ffmpeg-qsv enabled Alpha Encode for HEVC
- ffmpeg-qsv enabled Screen Content Tool encode for AV1
- ffmpeg-qsv added support for calculating encoded frame quality (MSE/PSNR)

2024Q2:
- ffmpeg-vaapi added VVC decode support
- ffmpeg-qsv added VVC decode support
- added zero copy support between ffmpeg-ddn openvio backend and ffmpeg-vaapi

2024Q1:
- Added new ffmpeg-raisr filter, which can be used by content creators and broadcasters to transform older content or user generated content created in non-digital and pre-high-definition (HD) formats into today's HD and 4K formats for use with NAS, Streaming and Video-on-Demand services
- ffmpeg-dnn added support of libtorch as dnn backend
- ffmpeg-vaapi added support of BLBRC(Block level bitrate control), which assigns different bitrate block by block
- ffmpeg-qsv changed default BRC mode to CQP
- ffmpeg added d3d12va encoder
- cartwheel-ffmpeg patches supported the latest ffmpeg 6.1.1 release

2023Q4:
- FFmpeg added Intel new MTL platform support
- ffmpeg-dnn added support of openvino yolov1 v2 v3 v4
- ffmpeg-dnn added support of SSD model with two outputs tensors
- ffmpeg-dnn added support of model with dynamic output tensor shape
- ffmpeg-dnn libtorch backend added support for using multi-devices to accelerate inference
both ffmpeg-vaapi and ffmpeg-qsv can use user-specified card on multi-gpu platform (such as dGPU+iGPU configure)
- ffmpeg-vaapi and ffmpeg-qsv added icq encode mode support