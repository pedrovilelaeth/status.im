---
id: gpg_signature_verification
title: GPG Signature Verification
layout: tutorials
---
# GPG Signature Verification

You can validate the GPG signatures of some of our releases. Here is the process:

* Download the release and/or development public keys:
    ```sh
    curl -s 'https://status.im/gpg/release.asc' | gpg --import
    curl -s 'https://status.im/gpg/devel.asc' | gpg --import
    ```

* Trust our uncertified public key, to avoid warnings (__OPTIONAL__):
    ```sh
    echo '1DD92FFA442D4B5C85C039231A151FD0883555FE:6:' | gpg --import-ownertrust
    echo 'BBF05F92536BED1930A9FD44009FB3BFE20B4DFD:6:' | gpg --import-ownertrust
    ```

* Validate the signature:
    ```
    gpg --verify 'StatusIm-Desktop-v0.2.5-d7d12jd.AppImage.asc'
    ```
    ```log
    gpg: assuming signed data in 'StatusIm-Desktop-v0.2.5-d7d12jd.AppImage'
    gpg: Signature made Mon 09 Aug 2021 05:01:16 PM CEST using RSA key ID E20B4DFD
    gpg: Good signature from "Status.im Release Signing (GPG key for signing Status.im release builds.) <admin@status.im>" [ultimate]
    Primary key fingerprint: 1DD9 2FFA 442D 4B5C 85C0  3923 1A15 1FD0 8835 55FE
    ```
