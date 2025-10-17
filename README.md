# uwp-gdk-runner


### pipeline:
1. use [MsixvcPackageDownloader](https://github.com/LukeFZ/MsixvcPackageDownloader) to get the download link (build this from source, precompiled binary doesn't work) (update: this repo now uses [msixvcdl-expressjs](https://github.com/Yakov5776/msixvcdl-expressjs) instead.)

2. after installing roblox normally using Microsoft Store, compile & use [cikextractor](https://github.com/LukeFZ/CikExtractor) with [workaround patch](https://github.com/LukeFZ/CikExtractor/issues/9#issuecomment-2677569101) to dump cik. alternatively, you can use our [pre-dumped cik file](https://github.com/Roblox-DeployHistory-Updates/uwp-gdk-runner/raw/refs/heads/main/5ef5d34b-1201-d8dd-921f-635e939947e0.cik).

3. use [xvdtool](https://github.com/emoose/xvdtool/releases/tag/v0.53) with these 2 commands to decrypt & extract files:

```shell
# To decrypt (Note: will in-place-decrypt, so replacing the existing file):
./xvdtool.exe -nd -eu -cik "<cik-guid-here>" -cikfile "<path-to-.cik-file>" <path-to-msixvc-file>

# Then, to extract the files within:
./xvdtool.exe -nd -xf "<path-to-output-folder>" <path-to-decrypted-msixvc-file>
```


## some facts:

##### Content ID for roblox is `51b27c18-6082-4877-8d9f-8b78b1bf356b`.
##### cik guid is `5ef5d34b-1201-d8dd-921f-635e939947e0` and blob can be found [here](https://github.com/Roblox-DeployHistory-Updates/uwp-gdk-runner/raw/refs/heads/main/5ef5d34b-1201-d8dd-921f-635e939947e0.cik).
##### product id is `9PMF91N3LZ3M` and products json can be found [here](https://displaycatalog.mp.microsoft.com/v7.0/products?bigIds=9PMF91N3LZ3M&market=US&languages=en-US,neutral&MS-CV=DGU1mcuYo0WMMp+F.1).