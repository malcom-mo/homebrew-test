# Test tap

## Where does `brew install` download bottles if there is no `root_url` in the formula?

Online documentation was confusing, so the behavior can be tested (from macOS Sequoia) with

    brew install malcom-mo/test/globallyuniquename

which will try to download a bottle that does not exist.

## Answer

It uses `ghcr.io/v2/homebrew/core` -- even for custom taps.

(That was surprising, I thought it would generate the URL based on the tap.)

From the command's output:

```
==> Downloading https://ghcr.io/v2/homebrew/core/globallyuniquename/manifests/0.1.0
curl: (56) The requested URL returned error: 404
```

```
==> Downloading https://ghcr.io/v2/homebrew/core/globallyuniquename/blobs/sha256:19f54fac6101d9c5cb1a838c4091be0dba85f0faff00bc2d986a30763c050fd8
curl: (56) The requested URL returned error: 404
```
