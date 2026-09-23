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
`E9.5_RNA.h5ad` from [virtualembryo.ai/challenge/data](https://virtualembryo.ai/challenge/data) into
the local `data/` folder (already gitignored). The notebook does not run without them.

## Setup

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

Then open `notebooks/01_first_submission_task1.ipynb`.

## Credit

Built against the Challenge as of August 2026. Data, task design, and the `veckit` scorer are the
work of Dr. Neil Chi's group and the Qiu Lab ([virtualembryo.ai](https://virtualembryo.ai),
[github.com/aristoteleo](https://github.com/aristoteleo)). This notebook only adds a worked example
on top of their public tooling.

## License

MIT. See [LICENSE](LICENSE). Applies to the code in this repo only, not to any Challenge data you
download separately.
