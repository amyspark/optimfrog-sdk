# optimfrog-sdk

OptimFROG SDK repackaged into tarballs. This is done to ensure symbolic links are properly unpackaged on extraction, for instance, when using [Python's `shutil.extract_archive`](https://docs.python.org/3/library/shutil.html#shutil.unpack_archive).

See https://stackoverflow.com/a/35783084 for more info.

## Reproducible tarballs creation

If on macOS, please `brew install gnu-tar` beforehand. Otherwise, replace `gtar` with `tar`.

Download the OptimFROG SDK files into a directory, then with a Unix shell, please execute:

```
ls -1 Optim*.zip | xargs -I % unzip %
ls -1 Optim*.zip | xargs -I % basename -s .zip % | xargs -I % env GZIP=-n gtar -caf %.tar.gz --group=0 --owner=0 --sort=name --pax-option=exthdr.name=%d/PaxHeaders/%f,delete=atime,delete=ctime ./%
```

## License

See [LICENSE](LICENSE.txt). Alternatively, see http://losslessaudio.org/License.php for details.
