# Contenido:

- [Practica 1 - Analisis de calidad de las lecturas y limpieza de adaptadores](#practica1) - 21 Feb 2023
- [Practica 2 - Ensamblaje con el transcriptoma de referencia (kallisto)](#practica2) - 22 Feb 2023
- [Practica 3 - Expresión diferencial con DESeq2](#practica3) - 21 Feb 2023
- [Practica 4 - Expresión diferencial con edgeR](#practica4) - 21 Feb 2023
- [Practica 5 - Análisis de terminos GO](#practica5) - 21 Feb 2023

## Practica 1 - Analisis de calidad de las lecturas y limpieza de adaptadores  <a name="practica1"></a>

### 1) Analisis de calidad de las lecturas crudas (raw data)

```
qlogin
cd /mnt/Timina/bioinfoII/rnaseq/BioProject_2023/rawData
ls
```

```
Desgloce de carpetas:
|-Athaliana_Fe_def/           # PRJNA256121
|-Athaliana_phosphate/        # PRJNA821620
|-COVID_virus/                # PRJNA858106
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
fastqc ./data/*.fastq.gz -o ./FastQC_rawData
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

# Crear symlink
ln -s /mnt/Timina/bioinfoII/rnaseq/BioProject_2023/rawData/adapters/TruSeq3-PE.fa .
ln -s /mnt/Timina/bioinfoII/rnaseq/BioProject_2023/rawData/adapters/TruSeq3-SE.fa .

# single-end
cd /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP111941/fastq_files
mkdir /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP111941/TRIM_results
for i in *;
do echo
trimmomatic SE -threads 2 -phred33 $i ../TRIM_results/"${i%.fastq}_trimmed.fq.gz" ILLUMINACLIP:/mnt/Timina/bioinfoII/rnaseq/BioProject_2023/rawData/adapters/TruSeq-SE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:35
done

# paired-end
mkdir /mnt/Citosina/amedina/ssalazar/meta/RNA2/fastq_files/SRP322015/TRIM_results
cd data
for i in *_1.fastq.gz;
do echo
trimmomatic PE -threads 8 -phred33 $i "${i%_1.fastq.gz}_2.fastq.gz" \
../data_trimmed/"${i%_1.fastq.gz}_1_trimmed.fastq.gz" ../data_trimmed/"${i%_1.fastq.gz}_1_unpaired.fastq.gz" \
../data_trimmed/"${i%_1.fastq.gz}_2_trimmed.fastq.gz" ../data_trimmed/"${i%_1.fastq.gz}_2_unpaired.fastq.gz" \
ILLUMINACLIP:../TruSeq3-PE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:5:20 MINLEN:60
done

# Regresar
cd ../
```

Notas:

- Remove adapters (ILLUMINACLIP:TruSeq3-PE.fa:2:30:10)
- Remove leading low quality or N bases (below quality 3) (LEADING:3)
- Remove trailing low quality or N bases (below quality 3) (TRAILING:3)
- Scan the read with a 4-base wide sliding window, cutting when the average quality per base drops below 15 (SLIDINGWINDOW:4:15)
- Drop reads below the 36 bases long (MINLEN:36)

Description:

- ILLUMINACLIP: Cut adapter and other illumina-specific sequences from the read.
- SLIDINGWINDOW: Perform a sliding window trimming, cutting once the average quality within the window falls below a threshold.
- LEADING: Cut bases off the start of a read, if below a threshold quality
- TRAILING: Cut bases off the end of a read, if below a threshold quality
- CROP: Cut the read to a specified length
- HEADCROP: Cut the specified number of bases from the start of the read
- MINLEN: Drop the read if it is below a specified length
- TOPHRED33: Convert quality scores to Phred-33
- TOPHRED64: Convert quality scores to Phred-64

Nota = ASCII_33 contiene los simbolos # y $ mientras que ASCII_64 no los contiene.

### 3) Analisis de calidad de las lecturas sin adaptadores

```
mkdir FastQC_trimmed
fastqc ./data_trimmed/*.fastq.gz -o ./FastQC_trimmed

# Reporte en MultiQC
multiqc ./FastQC_trimmed
```

### 4) Descarga de los archivos en tu computadora

```
rsync -rptuvl ecoss@dna.liigh.unam.mx:/mnt/Timina/bioinfoII/rnaseq/BioProject_2023/rawData/COVID_virus/data/multiqc_report.html . 
```

## Practica 2 - Ensamblaje con el transcriptoma de referencia (kallisto) <a name="practica2"></a>
## Practica 3 - Expresión diferencial con DESeq2 <a name="practica3"></a>
## Practica 4 - Expresión diferencial con edgeR <a name="practica4"></a>
## Practica 5 - Análisis de terminos GO <a name="practica5"></a>




