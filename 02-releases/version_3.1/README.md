# rpoCdb v3.1

Built from GTDB release r232. 184,865 sequences total (178,199 bacterial, 6,666 archaeal).

## What's new since v2.0

- Rebuilt from the full current GTDB r232 genome set (up from v2.0's snapshot).
- vsearch+LCA and Kraken2 added as fully GTDB-based classification options, built from
  the same sequence set and directly comparable to the DADA2 formats.
- mothur and QIIME2 formats added (previously "coming soon").
- Fixed a genus-name formatting bug affecting GTDB subgenus-suffixed taxa (e.g.
  `Blautia_A`): the build scripts were replacing all underscores with spaces when
  extracting GTDB rank fields, which broke `Genus/Species` parsing for addSpecies
  and corrupted the `addSpecies` headers for these specific taxa. Fixed by preserving
  the underscore directly from the GTDB taxonomy string.
- Validated on a defined mock community (Zymo gut microbiome standard) against 16S
  V3-V4 using three independent, identically-applied classification methods. rpoC
  detected 1.86-3.2x more species than 16S depending on method, including correctly
  resolving several GTDB species-level clusters that have no cultured representative
  or binomial name yet ("dark microbes") - verified by pairwise sequence identity
  (99%+ within a cluster, consistent with a real species) rather than assumed.

## Formats in this release

| Format | Files | Notes |
|---|---|---|
| `dada2/` | toGenus, toSpecies, addSpecies FASTAs | `assignTaxonomy()` + `addSpecies()` |
| `vsearch/` | single FASTA, GTDB taxonomy in header | exhaustive search recommended (`--maxaccepts 0 --maxrejects 0`) |
| `kraken2/` | FASTA (build your own index) | prebuilt index too large for GitHub - see Zenodo |
| `mothur/` | FASTA + `.taxonomy` | standard mothur reference format |
| `qiime2/` | FASTA + 2-column taxonomy TSV | import with `qiime tools import`, train your own classifier |

The full archive (all formats + the prebuilt Kraken2 index) is on Zenodo:
**[DOI: PENDING — to be added once uploaded]**
