# Virtual Embryo Challenge: Task 1 First Submission

A short, runnable notebook that gets you from a freshly registered [Virtual Embryo
Challenge](https://virtualembryo.ai) account to a valid, locally validated Task 1 submission.

This is a Community Contribution to the Challenge, not an official resource. It contains no
Challenge data. See [Data](#data) below.

## What this covers

The official [`veckit`](https://github.com/aristoteleo/veckit) tutorial shows you how to *score* a
prediction once you have one, using tiny bundled samples. It stops at "swap `--input` for your own
model's prediction." This notebook picks up there: building that first prediction for Task 1
(temporal scRNA-seq extrapolation), from raw `.h5ad` files to a correctly shaped submission. It
covers a floor (`copy_last`) baseline, one honest step above it (pseudobulk mean-shift
extrapolation), and how to package and locally sanity-check the result before you spend a
submission slot on it.

Task 1 asks you to predict the gene-expression distribution of mouse embryo cells at a developmental
stage you haven't observed, given earlier stages. Full task definition:
[virtualembryo.ai/challenge/tasks](https://virtualembryo.ai/challenge/tasks).

## Data

This repo ships no Challenge data. Per the Challenge Terms of Use (clause 14), the released
datasets are unpublished and may not be redistributed or re-hosted. You must register at
[virtualembryo.ai](https://virtualembryo.ai) yourself and download `E8.5_RNA.h5ad` and
`E9.5_RNA.h5ad` from [virtualembryo.ai/challenge/data](https://virtualembryo.ai/challenge/data).
The notebook does not run without them.

## Running it

Three ways. Pick whichever fits where you work.

### On your own machine

Needs [uv](https://docs.astral.sh/uv/) and Python 3.11 or newer.

```bash
git clone https://github.com/Scigantic/virtual-embryo-challenge-t1-baseline.git
cd virtual-embryo-challenge-t1-baseline
uv sync
# put E8.5_RNA.h5ad and E9.5_RNA.h5ad in data/ (gitignored)
uv run jupyter lab notebooks/getting-started.ipynb
```

`uv.lock` pins the exact versions this was checked against. Without uv, `pip install -r
requirements.txt` in a fresh virtualenv installs the same packages unpinned.

### From your own S3 bucket

If you keep your downloaded copy of the two files in a bucket you control, point the notebook at it
and it copies them into `data/` with boto3, using whatever AWS credentials your shell already has:

```bash
DATA_DIR=s3://your-bucket/path/to/files uv run jupyter lab notebooks/getting-started.ipynb
```

This reads from your bucket only. Nothing here fetches from, or uploads to, anyone else's storage.

### Hosted, one click

[scigantic.com/sample/virtual-embryo-challenge-t1](https://scigantic.com/sample/virtual-embryo-challenge-t1)
opens the same notebook in a browser session with the dependencies preinstalled, no account needed.
You still register at virtualembryo.ai and upload the two files into the session yourself. The
session keeps the files only for as long as it runs. This is a convenience, not a requirement:
everything the notebook does runs identically from this repo.

## Credit

Built against the Challenge as of September 2026. Data, task design, and the `veckit` scorer are the
work of Dr. Neil Chi's group and the Qiu Lab ([virtualembryo.ai](https://virtualembryo.ai),
[github.com/aristoteleo](https://github.com/aristoteleo)). This notebook only adds a worked example
on top of their public tooling.

## License

MIT. See [LICENSE](LICENSE). Applies to the code in this repo only, not to any Challenge data you
download separately.
