# multi-pkg-uv
This is a minimal example of having two `uv`-packages in the same repository. The local links through `uv.sources` work great, however, the version pinning when releasing (`uv build`) does not work.

`pkg-b` depends on `pkg-a`, and both have the package versions of `0.1.0`. When building `pkg-b`the wheel only loosely depends on `pkg-b`, meaning that no versions are checked or set as minimum (which is in contrast to the `uv.lock`-file).

Method for building `pkg-b` and inspecting requirements.
```shell
uv build
unzip -p dist/pkg_b*.whl '*/METADATA' | grep '^Requires-Dist:'
```
