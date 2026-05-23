# cloudfit-io

**Cloud-agnostic machine type advisor for computational workloads.**

> Like a load balancer for cloud instances that recommends the best machine type for your workload across AWS, GCP, and Azure, and stays current as providers deprecate and release new types.

Built with bioinformatics workloads as the primary use case, especially, workflow orchestration in mind but designed to be domain-agnostic.

---

## Libraries

| Package | Description | Status |
|---|---|---|
| [`cloudfit-core`](https://github.com/cloudfit-io/cloudfit-core) | Scoring engine · workload profiles · hard floor filters | ![PyPI](https://img.shields.io/pypi/v/cloudfit-core) |
| `cloudfit-provider-gcp` | GCP Compute Engine machine type fetcher | coming soon |
| `cloudfit-provider-aws` | AWS EC2 instance fetcher | coming soon |
| `cloudfit-api` | REST API — `/recommend` · `/instances` · `/diff` | coming soon |
| `cloudfit-cli` | CLI — `cloudfit recommend --workload demux` | coming soon |

## Quick example

```python
from cloudfit import WorkloadProfile, MachineType, rank

profile = WorkloadProfile(
    vcpu=60,
    ram_gb=224,
    workload="io-intensive",
    optimize_for="balanced",   # cost | performance | availability | balanced
)

# Candidate instances come from a cloudfit-provider-* package (coming soon),
# or supply your own list:
candidates = [
    MachineType(id="t2d-standard-60",      provider="gcp", vcpu=60, ram_gb=240, price_hr=2.31),
    MachineType(id="c3d-standard-60-lssd", provider="gcp", vcpu=60, ram_gb=240, price_hr=3.39),
]

best = rank(profile, candidates)[0]
print(f"{best.instance.provider} {best.instance.id}  ${best.instance.price_hr}/hr  score: {best.score}")
# → gcp t2d-standard-60  $2.31/hr  score: 0.8143
```

## Related projects

- [`samplesheet-parser`](https://github.com/chaitanyakasaraneni/samplesheet-parser) — Format-agnostic Illumina SampleSheet parser (BCLConvert V2 + IEM V1)
- [`clinops`](https://github.com/chaitanyakasaraneni/clinops) — Clinical ML data quality library

---

**Author:** [Chaitanya Krishna Kasaraneni](https://ckasaraneni.com)
&nbsp;·&nbsp; [Google Scholar](https://scholar.google.com/citations?user=Y2S8D2UAAAAJ)
&nbsp;·&nbsp; [ORCID 0000-0001-5792-1095](https://orcid.org/0000-0001-5792-1095)
