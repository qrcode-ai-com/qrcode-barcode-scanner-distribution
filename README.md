# QR Code & Barcode Scanner · publish lanes

This repository holds the publish lanes of
[QR Code & Barcode Scanner](https://github.com/qrcode-ai-com/qrcode-barcode-scanner-rust) that
publish to a registry from here rather than from the engine repository. Each lane lives in its own
folder, with its own workflow and a protected environment that a reviewer approves. The VS Code
lane publishes to both registries with Trusted Publishing: each registry trades the job's GitHub
OIDC ID token for a short-lived token, so no publishing token is stored here either.

| Lane | Folder | Workflow | Destination |
| --- | --- | --- | --- |
| VS Code extension | [vscode](vscode/README.md) | `.github/workflows/vscode-publish.yml` | Visual Studio Marketplace and Open VSX |

Every lane is staged from the engine repository by a script and is never edited by hand. Its
`SOURCE.json` names the engine revision and the SHA-256 of the artifact built from it. A tag starts
the publish workflow, which rebuilds the artifact from that revision and refuses it unless the hash
matches. Pushing a branch publishes nothing.

The source code of the extension, its tests and its documentation are in
[`integrations/vscode`](https://github.com/qrcode-ai-com/qrcode-barcode-scanner-rust/tree/main/integrations/vscode)
of the engine repository.

The files in this repository are under the MIT license. The scanner engine that the extension
bundles keeps its own license, described in the engine repository.
