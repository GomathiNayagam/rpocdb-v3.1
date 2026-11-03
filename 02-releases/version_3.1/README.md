# rpoCdb v3.1

Built from GTDB release r232. 178,199 unique, high-quality bacterial sequences.

## What's new since v2.0

- Rebuilt from the full current GTDB r232 genome set (up from v2.0's snapshot).
- vsearch+LCA and Kraken2 added as fully GTDB-based classification options, built from
  the same sequence set and directly comparable to the DADA2 formats.
- mothur and QIIME2 formats added.
- Validated on a defined mock community (Zymo gut microbiome standard) against 16S
  V3-V4 using three independent, identically-applied classification methods. rpoC
  detected 1.86-3.2x more species than 16S depending on method.
  
## Formats in this release

| Format | Files | Notes |
|---|---|---|
| `dada2/` | toGenus, toSpecies, addSpecies FASTAs | `assignTaxonomy()` + `addSpecies()` |
| `vsearch/` | single FASTA, GTDB taxonomy in header | exhaustive search recommended (`--maxaccepts 0 --maxrejects 0`) |
| `kraken2/` | FASTA (build your own index) | prebuilt index too large for GitHub - see Zenodo |
| `mothur/` | FASTA + `.taxonomy` | standard mothur reference format |
| `qiime2/` | FASTA + 2-column taxonomy TSV | import with `qiime tools import`, train your own classifier |

The full archive (all formats + the prebuilt Kraken2 index) is on Zenodo:
**[DOI: PENDING ]**
