# pubpypack-harmony-dane-hillard

This package does amazing things.

## Installation

```shell
$ python -m pip install pubpypack-harmony-dane-hillard
```

## CI artifacts
### actions/upload-artifact@v3
> https://github.com/actions/upload-artifact#uploading-to-the-same-artifact

File list in `artifact` is as follows:
```bash
pubpypack-harmony-dane-hillard-0.0.2.tar.gz
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-macosx_10_9_x86_64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-manylinux_2_5_i686.manylinux1_i686.manylinux_2_17_i686.manylinux2014_i686.whl
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-musllinux_1_1_i686.whl
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-musllinux_1_1_x86_64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-win32.whl
pubpypack_harmony_dane_hillard-0.0.2-cp310-cp310-win_amd64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-macosx_10_9_x86_64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-manylinux_2_5_i686.manylinux1_i686.manylinux_2_17_i686.manylinux2014_i686.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-manylinux_2_5_x86_64.manylinux1_x86_64.manylinux_2_17_x86_64.manylinux2014_x86_64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-musllinux_1_1_i686.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-musllinux_1_1_x86_64.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-win32.whl
pubpypack_harmony_dane_hillard-0.0.2-cp39-cp39-win_amd64.whl
```

### actions/download-artifact@v3
`actions/download-artifact@v3` will download this previous uploaded files in `artifact`.
```bash
Run actions/download-artifact@v3
  with:
    name: artifact
    path: ./ch07/first-python-package/dist
Starting download for artifact
Directory structure has been setup for the artifact
Total number of files that will be downloaded: 15
Artifact artifact was downloaded to /home/runner/work/publishing-python-packages/publishing-python-packages/ch07/first-python-package/dist
Artifact download has finished successfully
```