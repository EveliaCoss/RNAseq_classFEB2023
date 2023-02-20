# Contenido:

- Practica 1
- Practica 2
- Practica 3



## Practica 1 - Analisis de calidad de las lecturas y limpieza de adaptadores

### 1) Analisis de calidad de las lecturas crudas (raw data)

```
qlogin
cd /mnt/Timina/bioinfoII/rnaseq/BioProject_2023/rawData
ls
```

```
Desgloce de carpetas:
|-Arabidopsis_thaliana/       # PRJNA821620
|-COVID_virus/                # PRJNA858106
|-Athaliana_phosphate/        # PRJNA87017
|-Homo_sapiens/               # PRJNA826506
|-adapters
    |- TruSeq3-PE.fa          # adaptadores para paired-end
    |- TruSeq-SE.fa           # adaptadores para single-end
    |- readme.txt
|-SRAData_dow.sh              # Descarga de SRA
|-SRA_run.sge                 # Mandar como job al cluster
```

Vamos a hacer buenas practicas de bioinformatica, acomoda tu proyecto de la siguiente manera:

```
|-Arabidopsis_thaliana/       # PRJNA821620
  |- data/                    # raw_data (fastq.gz)
  |- FastQC_out/              # Salida del analisis de FastQC
  
 # Tipo: mkdir FastQC_rawData
```

Posteriormente, vamos a iniciar el analisis de calidad de las lecturas crudas o sin procesar (raw data):

```
# cargar module FastQC
module load fastqc/0.11.3
fastqc ./data/SRR*/*.fastq.gz -o ./FastQC_rawData
```

Para el reporte en MultiQC:

```
module load multiqc/1.5
multiqc ./FastQC_rawData
```

### 2) Limpieza de adaptadores

```
module load trimmomatic/0.33
mkdir data_trimmed

# single-end
cd /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP111941/fastq_files
mkdir /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP111941/TRIM_results
for i in *;
do echo
trimmomatic SE -threads 2 -phred33 $i ../TRIM_results/"${i%.fastq}_trimmed.fq.gz" ILLUMINACLIP:../Illumina_Adapters_SE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:35
done

# paired-end
mkdir /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP322015/TRIM_results
cd /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP322015/fastq_files
for i in *_1.fastq.gz;
do echo
trimmomatic PE -threads 8 -phred33 $i "${i%_1.fastq.gz}_2.fastq.gz" \
../TRIM_results/"${i%_1.fastq.gz}_1_trimmed.fastq.gz" ../TRIM_results/"${i%_1.fastq.gz}_1_unpaired.fastq.gz" \
../TRIM_results/"${i%_1.fastq.gz}_2_trimmed.fastq.gz" ../TRIM_results/"${i%_1.fastq.gz}_2_unpaired.fastq.gz" \
ILLUMINACLIP:/mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/adapters-paired.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:66
done


cd ../..
```

### 3) Analisis de calidad de las lecturas sin adaptadores











