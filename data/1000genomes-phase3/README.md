# Human 1000 Genomes Project phase 3 variant callset

The 1000 Genomes Project phase 3 callset contains analysis-ready
haplotypes from whole-genome Illumina sequencing of 2504 individuals.


## Data access

Variation data are available in VCF format from the public FTP
site:

* ftp://ftp-trace.ncbi.nih.gov/1000genomes/ftp/release/20130502/

These data have also been converted to Zarr format and deployed to a
Google Cloud Storage public bucket at the following location:

* gs://1000genomes-zarr/ALL.phase3_shapeit2_mvncall_integrated_v5a.20130502.genotypes

These data can be accessed via the following Python code, assuming the
Zarr and gcsfs packages are installed:

```python
import zarr
import gcsfs

store_path = '1000genomes-zarr/ALL.phase3_shapeit2_mvncall_integrated_v5a.20130502.genotypes'
gcs = gcsfs.GCSFileSystem(token='anon')
store = gcs.get_mapper(store_path)
callset = zarr.open_consolidated(store=store)
```


## References

* The 1000 Genomes Project Consortium (2015) A global reference for
  human genetic variation. https://www.nature.com/articles/nature15393
