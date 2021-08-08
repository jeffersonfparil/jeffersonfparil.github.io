# SARS-Cov-2 and COVID-19

[2020-02-08]

[SARS-CoV-2](https://www.nature.com/articles/s41564-020-0695-z) (formerly 2019-nCoV or Wuhan Coronavirus) which causes the disease designated as [COVID-19](https://twitter.com/WHO/status/1227248333871173632).\*

```
curl -s "https://www.ncbi.nlm.nih.gov/sviewer/viewer.cgi?report=fasta&id=MG772933.1" > bat_SARSlike.fasta

curl -s "https://www.ncbi.nlm.nih.gov/sviewer/viewer.cgi?report=fasta&id=MN988713.1" > 2019-nCoV.fasta

makeblastdb -in 2019-nCoV.fasta -dbtype nucl

blastn -query bat_SARSlike.fasta -db 2019-nCoV.fasta

blastn -query bat_SARSlike.fasta -db 2019-nCoV.fasta -outfmt '6 qseqid staxids pident evalue qcovhsp bitscore stitle'
```

\* Which is confusing since SARS (severe acute respiratory syndrome) is already a part of the official virus name but then why is the disease called COVID-19 instead of just SARS-2 or SARS-2019?