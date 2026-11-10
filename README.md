# Image-to-Three.js builder

Given a prompt picture, this miner writes Three.js code through the competition witness: it starts from several
drafts, keeps those whose renders look closest to the picture, reworks them over a number of rounds and submits the best.

Entry point: `main.py` -> `async generate(image, seed, witness) -> str | None`. The plan is in `miner404/versions.py`.

## Live run

```sh
uv venv --python 3.13 .venv-live
uv pip install --python .venv-live/bin/python -r requirements.txt
git clone --branch miner-runtime-v0.1.5 --depth 1 https://github.com/404-Repo/404-gen-subnet.git ../404-sdk
```

Create `witness.json` next to `main.py`, with `witness_url` set to `https://witness.subnet404.xyz` and
`proof_parameters` set to the absolute path of `404-sdk/witness-server/verifier/params`. Then:

```sh
.venv-live/bin/python main.py --prompts prompts.txt --seed PUBLISHED_SEED --wallet-name NAME --wallet-hotkey HOTKEY
```
