# Semana 06: Anotación de genomas

## Logro de la sesión: 

Al finalizar la unidad, el estudiante utiliza herramientas bioinformáticas para realizar la anotación de un genoma ensamblado.

# Estructura de la práctica:

1. Acceso al servidor de cómputo
2. Anotación global de un genoma
3. Identificación de genes de virulencia
4. Identificación de genes de resistencia a antibióticos
5. Identificación de elementos móviles
6. Identificación de plásmidos
7. Identificación de rutas metabólicas
8. Identificación de clústeres de genes de biosíntesis de metabolitos secundarios
9. Visualización del genoma
10. Anotación del genoma generado en el curso

## Programas requeridos:

### Programas de acceso al servidor:

PuTTY v0.79 https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
   - **Descripción:** PuTTY es un cliente SSH, Telnet y Rlogin gratuito y de código abierto para Windows y sistemas Unix. Se utiliza principalmente para establecer conexiones seguras de línea de comandos a servidores remotos.

WinSCP v6.1 https://winscp.net/eng/download.php
   - **Descripción:** WinSCP es un cliente SFTP, FTP, WebDAV, Amazon S3 y SCP gratuito y de código abierto para Windows. Permite la transferencia segura de archivos entre un ordenador local y servidores remotos mediante una interfaz gráfica de usuario. 

### Programas bioinformáticos:

Abricate v1.0.1 https://github.com/tseemann/abricate
   - **Descripción:** Abricate es una herramienta bioinformática de línea de comandos para la detección rápida de genes de resistencia a antibióticos (ARG) en genomas bacterianos completos o ensamblajes de contigs. Compara secuencias genómicas con bases de datos de genes de resistencia conocidos (como CARD, ResFinder y NCBI AMR). Abricate solo soporta contigs, no lecturas FASTQ, y detecta genes de resistencia adquiridos, no mutaciones puntuales. Requiere BLAST+ >= 2.7 y any2fasta.

MGCplotter v1.0.1 https://github.com/moshi4/MGCplotter/
   - **Descripción:** MGCplotter es una herramienta de línea de comandos para la visualización de clústeres de genes metabólicos (MGCs) en genomas microbianos, utilizando un diseño circular con Circos. Toma archivos Genbank como entrada y permite visualizar características básicas del genoma (CDS, ARNr, ARNt, contenido de GC), asignar la clasificación funcional COG y buscar CDS conservados entre especies. Requiere Circos, COGclassifier y MMseqs2.

MobileElementFinder v1.1.2 https://pypi.org/project/MobileElementFinder/
   - **Descripción:** MobileElementFinder es un servidor web y una herramienta de Python para detectar elementos genéticos móviles (MGEs) en datos de secuencias ensambladas. Anota su relación con la resistencia a antibióticos, genes de virulencia y plásmidos. Puede detectar MITEs, ISs, ComTns, Tns, ICEs, IMEs y CIMEs. Requiere secuencias contiguas ensambladas como entrada.

MOB-suite v3.1.9 https://github.com/phac-nml/mob-suite
   - **Descripción:** Es una colección de herramientas bioinformáticas para el análisis de elementos genéticos móviles (MGEs) en ensamblajes de genomas bacterianos. Incluye herramientas como MOB-typer y MOB-recon. MOB-typer, dentro de MOB-suite, analiza ensamblajes genómicos para identificar y clasificar plásmidos basándose en la presencia de genes clave como replicones y sistemas de movilización, prediciendo así su tipo, capacidad de transferencia y posible rango de huéspedes. Por otro lado, MOB-recon utiliza esta información, junto con bases de datos de referencia, para intentar reconstruir las secuencias completas de los plásmidos a partir de ensamblajes fragmentados, agrupando contigs que se cree que pertenecen al mismo plásmido y proporcionando informes detallados sobre sus características.

Prinseq v0.20.4 https://prinseq.sourceforge.net/
   - **Descripción:** Es un programa bioinformático escrito en Perl que se utiliza para el control de calidad, el filtrado y el formateo de datos de secuencias de alto rendimiento (high-throughput sequencing), como las lecturas obtenidas de secuenciadores Illumina, PacBio o Nanopore. La versión lite es una versión "ligera" de PRINSEQ (PRocessing and INformation of SEQuence data). En esencia, PRINSEQ-lite te permite limpiar y preparar tus datos de secuenciación antes de realizar análisis posteriores, como el ensamblaje de genomas, el mapeo de lecturas o el análisis de expresión génica.
     
Prokka v1.14.6 https://github.com/tseemann/prokka
   - **Descripción:** Prokka es una herramienta para la anotación rápida de genomas bacterianos, arqueales y virales. Predice genes codificantes de proteínas, ARNr, ARNt, regiones CRISPR y otras características genómicas. Prokka genera archivos de salida listos para la presentación a GenBank/ENA/DDBJ. Puede usar bases de datos BLAST específicas del género y mejorar las predicciones de genes para genomas altamente fragmentados.

RGI v6.0.3 https://card.mcmaster.ca
   - **Descripción:** RGI (Resistance Gene Identifier) predice genes de resistencia a antibióticos (ARG) y sus mecanismos en datos de proteínas o nucleótidos, basándose en la base de datos CARD. Puede analizar datos genómicos y metagenómicos. Utiliza Prodigal para la predicción de ORF y DIAMOND para la detección de homólogos.
   
### Herramientas bioinformáticas en línea:

AntiSMASH https://antismash.secondarymetabolites.org/#!/start
   - **Descripción:** AntiSMASH (antibiotics & Secondary Metabolite Analysis SHell) es una herramienta web para la identificación, anotación y análisis de clústeres de genes de biosíntesis de metabolitos secundarios en genomas bacterianos y fúngicos. Integra varias herramientas in silico de análisis de metabolitos secundarios, como NCBI BLAST+, HMMer 3 y Muscle 3.

KAAS https://www.genome.jp/kegg/kaas/
   - **Descripción:** KAAS (KEGG Automatic Annotation Server) es un servicio web que asigna información funcional a los genes de un genoma consultado, comparándolos con la base de datos KEGG. Permite obtener anotaciones de vías metabólicas, enzimas y otras funciones biológicas.

Proksee https://proksee.ca/
   - **Descripción:** Proksee es una herramienta web interactiva para la visualización y exploración de genomas procariotas. Genera mapas genómicos circulares y lineales personalizables que muestran características genómicas como genes, ARNs, regiones CRISPR y resistencia a antibióticos. Utiliza CGView.js como motor de dibujo del genoma.

## Metodología:

## 1.	Acceso al servidor de cómputo:

### Abrir el programa PuTTY, colocar el hostname ( 10.142.250.66 ) y port ( 22 ), y dar clic en Open:

<img width="500" alt="image" src="https://github.com/user-attachments/assets/92f89dbb-1a21-411d-adb5-38fe486a5567" />



### En la terminal abierta, escribir su usuario y contraseña correspondiente para tener acceso al servidor de cómputo Tensor:
 
<img width="700" alt="image" src="https://github.com/user-attachments/assets/4d246e93-c59c-4749-a2dd-03db25c53654" />



### Abrir el programa WinSCP, colocar el hostname ( 10.142.250.66 ) y port ( 22 ), escribir su usuario y contraseña correspondiente para tener acceso al servidor de cómputo Tensor, y hacer clic en Login:

<img width="500" alt="image" src="https://github.com/user-attachments/assets/ef4dc253-ce4a-417d-b761-39692d2a011a" />

<img width="500" alt="image" src="https://github.com/user-attachments/assets/577debca-6085-47c5-9bbd-73688bfa8bb0" />


## 2. Anotación global de un genoma

```bash
cd ~/genomics

mkdir annotation

cd annotation

conda activate pgcgap

prokka --outdir prokka --cpus 10 --kingdom Bacteria --gcode 11 --addgenes --rfam --prefix m01 /data/2025_1/database/m01_flye.racon.fasta
```

> **Comentario:** 
> - `--outdir prokka`: Especifica el directorio de salida donde Prokka guardará todos los archivos de resultados. En este caso, se creará una carpeta llamada "prokka" en el directorio donde se ejecute el comando.
> - `--cpus 10`: Indica el número de núcleos de procesamiento (CPUs) que Prokka puede utilizar. Se usarán hasta 10 núcleos para acelerar la anotación.
> - `--kingdom Bacteria`: Define el reino del genoma como Bacteria, lo que ayuda a Prokka a utilizar las bases de datos y modelos de predicción de genes más relevantes para bacterias.
> - `--gcode 11`: Establece el código genético utilizado para la traducción de genes. El código 11 es el estándar para la mayoría de las bacterias.
> - `--addgenes`: Esta opción le indica a Prokka que intente añadir nombres de genes a las anotaciones en el archivo GFF resultante, lo cual es útil para visualizaciones posteriores.
> - `--rfam`: Le dice a Prokka que busque y anote secuencias de ARN no codificantes utilizando la base de datos Rfam.
> - `--prefix m01`: Establece el prefijo "m01_" para todos los nombres de los archivos de salida y las características anotadas. Esto ayuda a organizar los resultados, especialmente al anotar múltiples genomas.
> - `/data/2025_1/database/m01_flye.racon.fasta`: Especifica la ruta al archivo de secuencia de entrada en formato FASTA que contiene el genoma a ser anotado.
```

```bash
ls -lh prokka

-rw-rw-r-- 1 ins_user ins_user 483K Uya   6 12:39 m01.err
-rw-rw-r-- 1 ins_user ins_user 1,7M Uya   6 12:39 m01.faa
-rw-rw-r-- 1 ins_user ins_user 4,5M Uya   6 12:39 m01.ffn
-rw-rw-r-- 1 ins_user ins_user 4,8M Uya   6 12:35 m01.fna
-rw-rw-r-- 1 ins_user ins_user 4,8M Uya   6 12:39 m01.fsa
-rw-rw-r-- 1 ins_user ins_user  11M Uya   6 12:39 m01.gbk
-rw-rw-r-- 1 ins_user ins_user 6,7M Uya   6 12:39 m01.gff
-rw-rw-r-- 1 ins_user ins_user  80K Uya   6 12:39 m01.log
-rw-rw-r-- 1 ins_user ins_user  19M Uya   6 12:39 m01.sqn
-rw-rw-r-- 1 ins_user ins_user 1,4M Uya   6 12:39 m01.tbl
-rw-rw-r-- 1 ins_user ins_user 501K Uya   6 12:39 m01.tsv
-rw-rw-r-- 1 ins_user ins_user  106 Uya   6 12:39 m01.txt
```

> **Comentario:** 
> - `m01.err`: Este archivo contiene los mensajes de error generados durante la ejecución de Prokka. Si está vacío o contiene pocos mensajes, significa que Prokka se ejecutó sin problemas importantes.
> - `m01.faa`: Contiene las secuencias de aminoácidos (proteínas) predichas por Prokka en formato FASTA.
> - `m01.ffn`: Contiene las secuencias de nucleótidos de los genes codificantes de proteínas predichos por Prokka en formato FASTA.
> - `m01.fna`: Contiene la secuencia del genoma de entrada original en formato FASTA.
> - `m01.fsa`: Este archivo, en este caso, es identico al m01.fna, y contiene la secuencia del genoma de entrada original en formato FASTA con informaciones extras en el encabezado.
> - `m01.gbk`: Contiene la anotación completa del genoma en formato GenBank. Este es uno de los archivos de salida más importantes, ya que contiene información detallada sobre los genes, sus funciones y otras características anotadas.
> - `m01.gff`: Contiene la anotación del genoma en formato GFF (General Feature Format). Este formato es ampliamente utilizado para visualizar y manipular anotaciones genómicas.
> - `m01.log`: Contiene un registro detallado de la ejecución de Prokka, incluyendo los comandos ejecutados y los resultados intermedios.
> - `m01.sqn`: Contiene la anotación del genoma en formato Sequin. Este formato se utiliza principalmente para enviar anotaciones a GenBank.
> - `m01.tbl`: Contiene una tabla de características anotadas en un formato que se puede utilizar para crear archivos de envío a GenBank.
> - `m01.tsv`: Contiene la anotación del genoma en formato TSV (Tab Separated Values). Este formato es muy útil para trabajar con la información de la anotación en hojas de cálculo o con programas de análisis de datos.
> - `m01.txt`: Contiene un resumen muy breve de la ejecución de Prokka.

```bash
cat prokka/m01.txt

organism: Genus species strain 
contigs: 6
bases: 6068252
CDS: 5511
gene: 5738
misc_RNA: 56
rRNA: 37
tRNA: 133
tmRNA: 1
```

```bash
head prokka/m01.faa

>COIJMHOG_00007 HTH-type transcriptional regulator HdfR
MDTELLKTFLEVSRTRHFGRAAESLYLTQSAVSFRIRQLENQLGVNLFTRHRNNIRLTAA
GEKLLPYAETLMSTWQAARKEVAHTSRHNEFSIGASASLWECMLNQWLGRLYQNQDAHTG
LQFEARIAQRQSLVKQLHERQLDLLITTEAPKMDEFSSQLLGYFTLALYTSAPSKLKGDL
NYLRLEWGPDFQQHEAGLIGADEVPILTTSSAELAQQQIAMLNGCTWLPVSWARKKGGLH
TVVDSTTLSRPLYAIWLQNSDKNALIRDLLKINVLDEVY
>COIJMHOG_00008 hypothetical protein
MAESFTTTNRYFDNKHYPRGFSRHGDFTIKEAQLLERHGYAFNELDLGKREPVTEEEKLF
VAVCRGEREPVTEAERVWSKYMTRIKRPKRFHTLSGGKPQVEGAEDYTDSDD
>COIJMHOG_00009 Competence protein ComM
```

## 3. Identificación de genes de virulencia

```bash
cd ~/genomics/annotation

mkdir abricate

cd abricate

conda activate abricate

abricate --list

DATABASE        SEQUENCES       DBTYPE  DATE
vfdb    4392    nucl    2025-Feb-8
plasmidfinder   460     nucl    2024-Dec-15
ecoli_vf        2701    nucl    2024-Dec-15
resfinder       3077    nucl    2024-Dec-15
ncbi    5386    nucl    2024-Dec-15
ecoh    597     nucl    2024-Dec-15
argannot        2223    nucl    2024-Dec-15
megares 6635    nucl    2024-Dec-15
card    2631    nucl    2024-Dec-15
```

> **Comentario:** 
> - `argannot`: A database of antibiotic resistance genes.
> - `ecoh`: A database of E. coli outer membrane proteins.
> - `ncbi`: A database of antimicrobial resistance genes from NCBI (National Center for Biotechnology Information).
> - `megares`: A database of antimicrobial resistance genes and their associated phenotypes.
> - `resfinder`: A database of acquired antimicrobial resistance genes.
> - `card`: The Comprehensive Antibiotic Resistance Database, a curated collection of antibiotic resistance genes and associated information.
> - `plasmidfinder`: A database of plasmid replicons, which are often associated with the spread of resistance genes.
> - `vfdb`: The Virulence Factors Database, a database of bacterial virulence factors.
> - `ecoli_vf`: A database of E. coli virulence factors.

```bash
abricate --db vfdb ~/genomics/annotation/prokka/m01.fna > m01_vfdb.tab
```

> **Comentario:** 
> - `--db vfdb`: Especifica la base de datos que Abricate debe usar para la comparación. En este caso, --db vfdb indica que se utilizará la base de datos VFDB (Virulence Factors Database). VFDB es una base de datos de factores de virulencia de diversos patógenos bacterianos.
> - `~/genomics/annotation/prokka/m01.fna`: Esta es la ruta al archivo de entrada que Abricate analizará. El archivo m01.fna es el archivo en formato FASTA que contiene la secuencia del genoma.
> - `m01_vfdb.tab`: Este es el nombre del archivo de salida que Abricate generará. Los resultados de la comparación de las secuencias de m01.fna contra la base de datos VFDB se guardarán en un archivo de texto plano llamado m01_vfdb.tab. El formato .tab sugiere que los datos estarán separados por tabulaciones, lo que facilita su posterior análisis con otras herramientas o programas.

```bash
head m01_vfdb.tab

#FILE   SEQUENCE        START   END     STRAND  GENE    COVERAGE        COVERAGE_MAP    GAPS    %COVERAGE       %IDENTITY       DATABASE        ACCESSION       PRODUCT RESISTANCE
/home/alumno01/genomics/annotation/prokka/m01.fna       chr01   1066783 1067151 +       cheY    1-369/369       =============== 0/0     100.00  86.18   vfdb    WP_000697869    (cheY) chemotaxis protein CheY [Flagella (VF0519) - Motility (VFC0204)] [Vibrio cholerae O1 biovar El Tor str. N16961]
/home/alumno01/genomics/annotation/prokka/m01.fna       chr01   1073402 1073896 +       cheW    1-495/495       =============== 0/0     100.00  80.00   vfdb    WP_000075896    (cheW) purine-binding chemotaxis protein CheW [Flagella (VF0519) - Motility (VFC0204)] [Vibrio cholerae O1 biovar El Tor str. N16961]
/home/alumno01/genomics/annotation/prokka/m01.fna       chr01   2439976 2440467 -       vcrH    1-489/489       ========/====== 1/3     100.00  86.79   vfdb    WP_005464462    (vcrH) type III secretion system chaperone VcrH [T3SS1 (VF0408) - Effector delivery system (VFC0086)] [Vibrio parahaemolyticus RIMD 2210633]
/home/alumno01/genomics/annotation/prokka/m01.fna       chr01   2447606 2448890 +       vscN    1-1285/1323     =============== 0/0     97.13   81.71   vfdb    WP_005477722    (vscN) type III secretion system ATPase VscN [T3SS1 (VF0408) - Effector delivery system (VFC0086)] [Vibrio parahaemolyticus RIMD 2210633]
/home/alumno01/genomics/annotation/prokka/m01.fna       chr01   2465844 2466092 -       vscF    1-249/249       =============== 0/0     100.00  85.94   vfdb    WP_005464566    (vscF) type III secretion system needle protein VscF [T3SS1 (VF0408) - Effector delivery system (VFC0086)] [Vibrio parahaemolyticus RIMD 2210633]
/home/alumno01/genomics/annotation/prokka/m01.fna       plasmid_01a     13218   14534   -       pirB    1-1317/1317     =============== 0/0     100.00  100.00  vfdb    AKC05670        (pirB) Photorhabdus insect-related toxin subunit PirB [PirAB (VF1362) - Exotoxin (VFC0235)] [Vibrio parahaemolyticus str. 3HP]
/home/alumno01/genomics/annotation/prokka/m01.fna       plasmid_01a     14547   14882   -       pirA    1-336/336       =============== 0/0     100.00  100.00  vfdb    AKC05671        (pirA) Photorhabdus insect-related toxin subunit PirA [PirAB (VF1362) - Exotoxin (VFC0235)] [Vibrio parahaemolyticus str. 3HP]	
```

> **Comentario:** 
> - `#FILE`: Indica la ruta y el nombre del archivo de entrada analizado por Abricate: /home/alumno01/genomics/annotation/prokka/m01.fna.
> - `SEQUENCE`: Muestra el identificador de la secuencia (contig o cromosoma) donde se encontró la coincidencia: chr01 o plasmid_01a.
> - `START`: Especifica la posición inicial de la coincidencia en la secuencia de entrada (en pares de bases).
> - `END`: Especifica la posición final de la coincidencia en la secuencia de entrada (en pares de bases).
> - `STRAND`: Indica la hebra de ADN de la secuencia de entrada donde se localiza la coincidencia (+ para la hebra directa, - para la hebra complementaria).
> - `GENE`: Muestra el nombre del gen encontrado en la base de datos que coincide con la secuencia analizada (ej., cheY, cheW, vcrH, vscN, vscF, pirB, pirA).
> - `COVERAGE`: Indica la proporción del gen de la base de datos cubierta por la coincidencia en la secuencia de entrada (ej., 1-369/369).
> - `COVERAGE_MAP`: Proporciona una representación visual de la cobertura de la alineación (= para regiones coincidentes, otros caracteres para gaps).
> - `GAPS`: Muestra el número y la longitud total de los gaps (inserciones o deleciones) en la alineación (ej., 0/0).
> - `%COVERAGE`: Indica el porcentaje de la longitud del gen de la base de datos que está cubierta por la secuencia de entrada.
> - `%IDENTITY`: Muestra el porcentaje de identidad entre la secuencia de entrada y la secuencia del gen en la base de datos en la región alineada.
> - `DATABASE`: Especifica la base de datos utilizada para la comparación: vfdb (Virulence Factors Database).
> - `ACCESSION`: Proporciona el número de acceso del registro coincidente en la base de datos (ej., WP_000697869, AKC05670).
> - `PRODUCT`: Describe la función o el nombre del producto génico anotado en la base de datos, incluyendo información sobre vías o sistemas relacionados.
> - `RESISTANCE`: En el contexto de VFDB, esta columna podría contener información adicional relacionada con la virulencia, aunque en este caso parece estar vacía o no directamente relacionada con resistencia a antibióticos.

## 4. Identificación de genes de resistencia a antibióticos

```bash
cd ~/genomics/annotation

mkdir rgi

cd rgi

conda activate resistance

rgi load --card_json /data/db/card/card.json  --local

rgi main --input_sequence ~/genomics/annotation/prokka/m01.fna --output_file m01_rgi --clean --local --num_threads 10
```

> **Comentario:** 
> - `--clean`: Elimina archivos temporales.
> - `--local`: Especifica que RGI debe utilizar la base de datos local instalada en tu sistema. 
> - `--output_file m01_rgi`: Define el nombre del archivo de salida donde RGI guardará los resultados de su análisis. En este caso, el archivo se llamará m01_rgi. Por defecto, RGI genera un archivo en formato .tsv (valores separados por tabulaciones).

```bash
head -n 2 m01_rgi.txt 

ORF_ID  Contig  Start   Stop    Orientation     Cut_Off Pass_Bitscore   Best_Hit_Bitscore       Best_Hit_ARO    Best_Identities ARO     Model_type      SNPs_in_Best_Hit_ARO    Other_SNPsDrug Class      Resistance Mechanism    AMR Gene Family Predicted_DNA   Predicted_Protein       CARD_Protein_Sequence   Percentage Length of Reference Sequence ID      Model_ID        Nudged    Note    Hit_Start       Hit_End Antibiotic
chr01_343 # 406662 # 407294 # -1 # ID=1_343;partial=00;start_type=ATG;rbs_motif=AGGA;rbs_spacer=11bp;gc_cont=0.447      chr01_343       406662  407294  -       Strict  400     418.313 CRP       95.24   3000518 protein homolog model   n/a     n/a     macrolide antibiotic; fluoroquinolone antibiotic; penam antibiotic efflux       resistance-nodulation-cell division (RND) antibiotic efflux pump  ATGGTTCTAGGTAAACCTCAAACCGACCCAACATTAGAGTGGTTTCTTTCACACTGTCATATTCATAAGTACCCATCAAAGAGCACGCTAATTCACGCGGGCGAAAAAGCAGAGACTTTGTACTACATCGTTAAAGGTTCTGTTGCGGTTCTTATCAAAGACGAAGAAGGTAAGGAAATGATCCTTTCTTACCTAAACCAAGGCGACTTCATTGGTGAGCTTGGTCTATTCGAAGAAGACCAAGAGCGTACAGCTTGGGTTCGCGCTAAATCTCCTTGTGAAGTGGCAGAGATTTCTTTCAAGAAATTCCGTCAACTTATCCAAGTTAACCCAGACATCCTAATGCGCCTTTCTGCGCAAATGGCTCGTCGTCTACAAGTTACTAGCCAAAAAGTGGGTGACCTAGCGTTCCTAGACGTAACTGGTCGTATCGCTCAGACTCTTCTGAACCTTGCTAAACAGCCAGATGCGATGACGCACCCAGACGGCATGCAAATCAAGATCACTCGTCAAGAAATCGGTCAAATTGTTGGCTGTTCTCGTGAGACAGTAGGCCGTATCTTGAAGATGCTAGAAGAGCAGAACCTAATTTCTGCGCACGGTAAAACTATCGTTGTTTACGGAACTCGTTAA     MVLGKPQTDPTLEWFLSHCHIHKYPSKSTLIHAGEKAETLYYIVKGSVAVLIKDEEGKEMILSYLNQGDFIGELGLFEEDQERTAWVRAKSPCEVAEISFKKFRQLIQVNPDILMRLSAQMARRLQVTSQKVGDLAFLDVTGRIAQTLLNLAKQPDAMTHPDGMQIKITRQEIGQIVGCSRETVGRILKMLEEQNLISAHGKTIVVYGTR        MVLGKPQTDPTLEWFLSHCHIHKYPSKSKLIHQGEKAETLYYIVKGSVAVLIKDEEGKEMILSYLNQGDFIGELGLFEEGQERSAWVRAKTACEVAEISYKKFRQLIQVNPDILMRLSAQMARRLQVTSEKVGNLAFLDVTGRIAQTLLNLAKQPDAMTHPDGMQIKITRQEIGQIVGCSRETVGRILKMLEDQNLISAHGKTIVVYGTR        100.00  gnl|BL_ORD_ID|801|hsp_num:0       869                     0       630     erythromycin; cloxacillin; oxacillin; norfloxacin
```

> **Comentario:**
> - `ORF_ID`: Identificador único del Open Reading Frame (ORF) o gen predicho en tu archivo de entrada. Incluye información como el contig (chr01), un número interno (343), las coordenadas (406662 # 407294), la orientación (-1 indica hebra reversa), y metadatos de la predicción del gen.
> - `Contig`: Nombre del contig (o cromosoma) en el que se localiza el ORF (chr01).
> - `Start`: Posición inicial (en pares de bases) del ORF en el contig (406662).
> - `Stop`: Posición final (en pares de bases) del ORF en el contig (407294).
> - `Orientation`: Dirección de la transcripción del ORF en el contig (- indica la hebra reversa).
> - `Cut_Off`: El criterio de corte (threshold) utilizado por RGI para clasificar la coincidencia. En este caso, es Strict, lo que indica un alto nivel de confianza en la predicción.
> - `Pass_Bitscore`: El valor de bitscore que la coincidencia entre tu secuencia y el gen de resistencia en la base de datos CARD superó el umbral definido por el Cut_Off. Un bitscore más alto indica una mejor alineación.
> - `Best_Hit_Bitscore`: El bitscore de la mejor coincidencia encontrada en la base de datos CARD para este ORF.
> - `Best_Hit_ARO`: El identificador único (ARO Accession) del gen de resistencia con la mejor coincidencia en la base de datos CARD (3000518). Este código te permite buscar más información sobre este gen en la base de datos CARD.
> - `Best_Identities`: El porcentaje de identidad entre la secuencia de tu ORF y la secuencia del gen de resistencia con la mejor coincidencia en la base de datos CARD (95.24).
> - `ARO`: El nombre del modelo de resistencia o el gen de resistencia identificado en la base de datos CARD (CRP).
> - `Model_type`: El tipo de modelo utilizado por RGI para realizar la predicción (protein homolog model).
> - `SNPs_in_Best_Hit_ARO`: El número de polimorfismos de un solo nucleótido (SNPs) encontrados dentro de la región que coincide con el mejor hit ARO (n/a en este caso).
> - `Other_SNPs`: Información sobre otros SNPs encontrados en la secuencia del ORF que podrían estar relacionados con la resistencia (n/a en este caso).
> - `Drug Class`: La clase o las clases de antibióticos a las que confiere resistencia el gen identificado (macrolide antibiotic; fluoroquinolone antibiotic; penam antibiotic).
> - `Resistance Mechanism`: El mecanismo molecular por el cual el gen confiere resistencia (efflux).
> - `AMR Gene Family`: La familia a la que pertenece el gen de resistencia (resistance-nodulation-cell division (RND) antibiotic efflux pump).
> - `Predicted_DNA`: La secuencia de ADN predicha del ORF.
> - `Predicted_Protein`: La secuencia de proteína traducida del ORF.
> - `CARD_Protein_Sequence`: La secuencia de proteína del gen de resistencia correspondiente en la base de datos CARD.
> - `Percentage Length of Reference Sequence ID`: El porcentaje de la longitud de la secuencia de referencia (en CARD) que está cubierta por la alineación con tu secuencia (100.00).
> - `Model_ID`: Un identificador interno del modelo utilizado para la predicción (869).
> - `Nudged`: Indica si la predicción se ajustó basándose en información adicional (0 en este caso, probablemente indicando que no se ajustó).
> - `Note`: Cualquier nota o comentario adicional sobre la predicción (vacío en este caso).
> - `Hit_Start`: La posición inicial de la alineación entre tu secuencia y el gen de CARD.
> - `Hit_End`: La posición final de la alineación entre tu secuencia y el gen de CARD.
> - `Antibiotic`: Los nombres específicos de los antibióticos a los que se predice resistencia (erythromycin; cloxacillin; oxacillin; norfloxacin).

## 5. Identificación de elementos móviles

```bash
cd ~/genomics/annotation

mkdir mobile

cd mobile

mefinder find --gff --contig ~/genomics/annotation/prokka/m01.fna m01_mobile
```

> **Comentario:**
> - `--gff`: Esta opción indica a MEfinder que la información sobre las características genómicas (como genes) se proporcionará o se espera encontrar en un archivo en formato GFF (General Feature Format). Aunque en este comando se especifica el archivo FASTA (m01.fna) con la opción --contig, MEfinder a menudo utiliza archivos GFF generados por herramientas de anotación como Prokka para integrar la información de los genes en el análisis de los MGEs. Es posible que MEfinder intente generar o utilizar información de tipo GFF internamente o que esta opción esté pensada para un uso con un archivo de contigs acompañado de un GFF separado (aunque no se especifique aquí).
> - `--contig ~/genomics/annotation/prokka/m01.fna`: Esta opción especifica la ruta al archivo que contiene las secuencias de los contigs (o el genoma ensamblado). En este caso, se está utilizando el archivo FASTA (m01.fna) que presumiblemente contiene el ensamblaje del genoma que quieres analizar en busca de elementos móviles.
> - `m01_mobile`: Este es el prefijo que MEfinder utilizará para nombrar los archivos de salida que generará. MEfinder produce varios archivos con información sobre los elementos móviles identificados. Estos archivos probablemente incluirán información en formato .tsv (tab-separated values) y posiblemente archivos en formato .gff para visualizar los elementos móviles en el contexto del genoma.

```bash
head m01_mobile.csv
 
#date: 2025-05-05_22:38
#sample: m01
#mge_finder version: 1.1.2
#mgedb version: 1.1.1
#blastn version: 2.16.0+
mge_no,name,synonyms,prediction,type,allele_len,depth,e_value,identity,coverage,gaps,substitution,contig,start,end,cigar
1,ISVvu6,,predicted,insertion sequence,1092,,0.0,0.743,0.97,33,252,chr01,1504511,1505602,M123 D1 M3 I1 M24 I1 M5 D1 M103 D1 M6 I1 M69 D1 M4 I1 M195 D1 M2 D1 M6 I1 M1 I1 M26 D1 M1 D1 M5 I1 M4 I1 M138 I1 M9 D1 M6 I1 M4 D1 M74 D1 M3 I1 M19 D2 M4 D1 M2 I1 M2 I2 M40 I1 M2 D1 M105 D1 M53 D1 M3 I1 M34
2,ISVvu6,,predicted,insertion sequence,1092,,0.0,0.743,0.97,33,252,chr01,1510904,1511995,M123 D1 M3 I1 M24 I1 M5 D1 M103 D1 M6 I1 M69 D1 M4 I1 M195 D1 M2 D1 M6 I1 M1 I1 M26 D1 M1 D1 M5 I1 M4 I1 M138 I1 M9 D1 M6 I1 M4 D1 M74 D1 M3 I1 M19 D2 M4 D1 M2 I1 M2 I2 M40 I1 M2 D1 M105 D1 M53 D1 M3 I1 M34
3,ISVa6,,predicted,insertion sequence,1091,,0,0.972,1.0,0,31,chr01,1499380,1500470,M1091
4,ISVa6,,predicted,insertion sequence,1091,,0,0.972,1.0,0,31,chr01,1541800,1542890,M1091
```

> **Comentario:**
> - `mge_no`: Un número de identificación secuencial asignado por MEfinder a cada elemento genético móvil (MGE) predicho.
> - `name`: El nombre del MGE encontrado, basado en la base de datos MGEdb (ej., ISVvu6, ISVa6). IS probablemente significa "Insertion Sequence" (secuencia de inserción).
> - `synonyms`: Otros nombres o sinónimos que pueda tener el MGE en la base de datos (está vacío en estas primeras líneas).
> - `prediction`: El estado de la predicción del MGE. En este caso, todos son marcados como predicted.
> - `type`: El tipo de elemento genético móvil predicho (ej., insertion sequence).
> - `allele_len`: La longitud del alelo (variante específica) del MGE encontrado en la base de datos (en pares de bases).
> - `depth`: Una medida de la cobertura o profundidad de la lectura en los datos de secuenciación (está vacío en estas primeras líneas, lo que sugiere que probablemente se analizaron secuencias ensambladas y no lecturas sin ensamblar).
> - `e_value`: El valor E (expect value) del alineamiento BLASTn entre la secuencia genómica y la secuencia del MGE en la base de datos. Un valor E más cercano a cero indica una mayor significancia estadística de la coincidencia.
> - `identity`: La proporción de bases idénticas en la alineación entre la secuencia genómica y la secuencia del MGE en la base de datos (expresada como un valor entre 0 y 1).
> - `coverage`: La proporción de la longitud del MGE en la base de datos que está cubierta por la alineación con la secuencia genómica (expresada como un valor entre 0 y 1).
> - `gaps`: El número total de gaps (inserciones o deleciones) en la alineación.
> - `substitution`: El número total de sustituciones de bases en la alineación.
> - `contig`: El identificador del contig (o cromosoma) en tu genoma ensamblado donde se encontró el MGE (ej., chr01).
> - `start`: La posición inicial (en pares de bases) del MGE predicho en el contig.
> - `end`: La posición final (en pares de bases) del MGE predicho en el contig.
> - `cigar`: Una representación compacta de la alineación (Compact Idiosyncratic Gapped Alignment Report). Describe las operaciones de alineamiento (ej., M para match/mismatch, I para inserción, D para deleción) y sus longitudes.

## 6. Identificación de plásmidos

```bash
cd ~/genomics/annotation

mkdir plasmid

cd plasmid

mob_recon --infile ~/genomics/annotation/prokka/m01.fna --outdir m01_plasmid
```

> **Comentario:**
> - `mob_recon`: Este es el comando principal para ejecutar MOB-recon (Mobile Element Best Representative CONtigs). MOB-recon es una herramienta bioinformática diseñada para reconstruir y caracterizar plásmidos a partir de ensamblajes de genomas bacterianos. Utiliza la información de contigs y los resultados de MOB-typer para agrupar contigs que probablemente pertenezcan al mismo plásmido.
> - `--infile ~/genomics/annotation/prokka/m01.fna`: Especifica la ruta al archivo de entrada, que debe ser el ensamblaje del genoma en formato FASTA. En este caso, estás proporcionando el mismo archivo (m01.fna) que probablemente contiene tanto secuencias cromosómicas como plasmídicas ensambladas. MOB-recon analizará este archivo para identificar y agrupar los contigs plasmídicos.
> - `--outdir m01_plasmid`: Define el directorio de salida donde MOB-recon guardará los resultados de su análisis. Se creará una carpeta llamada m01_plasmid en el directorio donde ejecutas el comando. Esta carpeta contendrá los archivos generados por MOB-recon, que incluirán información sobre los plásmidos identificados, sus secuencias reconstruidas (si es posible) y otros metadatos.

```bash
ls -lh m01_plasmid

total 5,9M
-rw-rw-r-- 1 alumno04 alumno04  860 may  7 11:29 biomarkers.blast.txt
-rw-rw-r-- 1 alumno04 alumno04 5,6M may  7 11:29 chromosome.fasta
-rw-rw-r-- 1 alumno04 alumno04 1,5K may  7 11:29 contig_report.txt
-rw-rw-r-- 1 alumno04 alumno04 9,3K may  7 11:29 mge.report.txt
-rw-rw-r-- 1 alumno04 alumno04 1,1K may  7 11:29 mobtyper_results.txt
-rw-rw-r-- 1 alumno04 alumno04  68K may  7 11:29 plasmid_AD413.fasta
-rw-rw-r-- 1 alumno04 alumno04 138K may  7 11:29 plasmid_AE795.fasta
```

```bash
cat m01_plasmid/mge.report.txt

sample_id       molecule_type   primary_cluster_id      secondary_cluster_id    contig_id       size    gc      md5     mge_id  mge_acs mge_type        mge_subtype     mge_length      mge_start mge_end contig_start    contig_end      length  sstrand qcovhsp pident  evalue  bitscore
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    187     2552
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     3812    5367
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      77461   78561
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     121853  123407
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    124612  126977
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     167288  168842
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    169912  172277
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     227235  228789
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    229775  232140
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     232665  234219
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    235424  237789
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     292088  293642
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    294521  296886
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     297411  298965
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    300042  302407
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     478715  480269
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    481081  483446
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     483970  485524
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    486594  488959
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     606803  608357
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    609488  611853
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1316763 1317863
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        00699   CP021981        ISVa6   IS30    1091    1       1091      1499380 1500470
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        00699   CP021981        ISVa6   IS30    1091    1       1091      1541800 1542890
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1547965 1549065
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1550163 1551263
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1672846 1673946
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1701731 1702831
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1749814 1750914
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      1827695 1828795
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2148496 2149596
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2167787 2168887
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2213160 2214260
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2268135 2269235
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2369752 2370852
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2572760 2573860
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      2773213 2774313
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    3056367 3058733
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01399   CP016586.1      16s-rRNA        16S     1554    11544     3059895 3061449
m01_flye.racon  chromosome                      chr01   3620046 0.45565498338971383     ab3305ab19034af2b5bb4378f5ddd0e6        01106   CP022101        ISVa15  IS630   1101    1       1101      3561939 3563039
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        00699   CP021981        ISVa6   IS30    1091    1       1091      481899  482989
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      502140  503240
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      850866  851966
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      1152336 1153436
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01400   CP016586.1      23s-rRNA        23S     3027    658       3027    1296160 1298525
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01399   CP016586.1      16s-rRNA        16S     1554    11544     1299836 1301390
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      1354770 1355870
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      1603364 1604464
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      1963508 1964608
m01_flye.racon  chromosome                      chr02   2216041 0.4542068490610056      683fad9c4d08882995585b0d374d10b3        01106   CP022101        ISVa15  IS630   1101    1       1101      1982957 1984057
m01_flye.racon  plasmid AE795   AO650   plasmid_02      66980   0.42441027172290235     5b7feb13b6c297143c554f216f4ab9bc        00699   CP021981        ISVa6   IS30    1091    1       1091      34385   35475   1091    minus   100.0   97.15899999999999       0.0     1844
m01_flye.racon  plasmid AE795   AO650   plasmid_02      66980   0.42441027172290235     5b7feb13b6c297143c554f216f4ab9bc        01106   CP022101        ISVa15  IS630   1101    1       1101      41716   42816   1104    minus   100.0   90.399  0.0     1447
m01_flye.racon  plasmid AE795   AO650   plasmid_02      66980   0.42441027172290235     5b7feb13b6c297143c554f216f4ab9bc        01106   CP022101        ISVa15  IS630   1101    1       1101      46505   47605   1102    plus    100.0   90.47200000000001       0.0     1452
m01_flye.racon  plasmid AE795   AO650   plasmid_02      66980   0.42441027172290235     5b7feb13b6c297143c554f216f4ab9bc        01106   CP022101        ISVa15  IS630   1101    1       1101      54244   55344   1104    minus   100.0   90.30799999999999       0.0     1441
m01_flye.racon  plasmid AE795   AO650   plasmid_02      66980   0.42441027172290235     5b7feb13b6c297143c554f216f4ab9bc        01106   CP022101        ISVa15  IS630   1101    1       1101      56962   58062   1104    minus   100.0   90.30799999999999       0.0     1441
m01_flye.racon  plasmid AE795   AO650   plasmid_02      66980   0.42441027172290235     5b7feb13b6c297143c554f216f4ab9bc        01106   CP022101        ISVa15  IS630   1101    1       1101      58886   59986   1104    minus   100.0   90.399  0.0     1447
m01_flye.racon  plasmid AD413   AM969   plasmid_01b     69340   0.44936544563022784     352832786a442f1f1dc995e791e5f382        01106   CP022101        ISVa15  IS630   1101    1       1101      29185   30285   1104    minus   100.0   90.399  0.0     1447
```

> **Comentario:**
> - `sample_id`: Identificador único de la muestra analizada (m01_flye.racon).
> - `molecule_type`: El tipo de molécula donde se encontró el elemento genético móvil (MGE). En este caso, todos los reportados están en el chromosome. Esto podría ser inesperado si esperabas ver elementos en plásmidos. Indica que MOB-recon está identificando secuencias relacionadas con MGEs dentro del cromosoma.
> - `primary_cluster_id`: Un identificador del clúster primario al que pertenece la secuencia relacionada con el MGE. Está vacío en este reporte.
> - `secondary_cluster_id`: Un identificador del clúster secundario al que pertenece la secuencia relacionada con el MGE. Está vacío en este reporte.
> - `contig_id`: El identificador del contig (o cromosoma) donde se localiza la secuencia relacionada con el MGE (chr01).
> - `size`: El tamaño total (en pares de bases) del contig donde se encontró el MGE (3620046).
> - `gc`: El contenido de guanina-citosina (GC) promedio del contig (0.45565498338971383).
> - `md5`: El hash MD5 único del contig.
> - `mge_id`: Un identificador interno asignado por MOB-recon a la secuencia relacionada con el MGE (ej., 01400, 01399, 01106).
> - `mge_acs`: El número de acceso en una base de datos para el elemento genético móvil identificado (ej., CP016586.1, CP022101).
> - `mge_type`: El tipo general de elemento genético móvil identificado (ej., 23s-rRNA, 16s-rRNA, ISVa15). En este caso, se identifican secuencias de ARN ribosomal (que son componentes de ribosomas, no típicamente considerados MGEs) y una secuencia de inserción (ISVa15, que sí es un tipo de MGE).
> - `mge_subtype`: El subtipo más específico del MGE (ej., 23S, 16S, IS630 - familia de la secuencia de inserción).
> - `mge_length`: La longitud (en pares de bases) de la secuencia del MGE identificada en la base de datos (3027, 1554, 1101).
> - `mge_start`: La posición inicial (en la secuencia del MGE de la base de datos) de la alineación con tu genoma (658, 11544, 1).
> - `mge_end`: La posición final (en la secuencia del MGE de la base de datos) de la alineación con tu genoma (3027, 3812, 1101).
> - `contig_start`: La posición inicial (en tu contig) donde se encontró la coincidencia con el MGE (187, 5367, 77461).
> - `contig_end`: La posición final (en tu contig) donde se encontró la coincidencia con el MGE (2552, 123407, 78561).
> - `length`: La longitud de la alineación entre la secuencia del MGE de la base de datos y tu contig.
> - `sstrand`: La hebra de la secuencia del MGE de la base de datos que coincide con tu contig (vacío en este caso, podría indicar la hebra directa).
> - `qcovhsp`: El porcentaje de la longitud de la secuencia de consulta (tu genoma) que está cubierta por el hit de alta puntuación (HSP) en la alineación.
> - `pident`: El porcentaje de identidad de la secuencia entre la secuencia del MGE de la base de datos y tu contig en la región alineada.
> - `evalue`: El valor E (expect value) de la alineación BLASTn. Un valor más cercano a cero indica una mayor significancia estadística de la coincidencia.
> - `bitscore`: La puntuación de bits de la alineación BLASTn. Una puntuación más alta indica una mejor alineación.

```bash
cat m01_plasmid/mobtyper_results.txt

sample_id       num_contigs     size    gc      md5     rep_type(s)     rep_type_accession(s)   relaxase_type(s)        relaxase_type_accession(s)      mpf_type        mpf_type_accession(s)     orit_type(s)    orit_accession(s)       predicted_mobility      mash_nearest_neighbor   mash_neighbor_distance  mash_neighbor_identification    primary_cluster_id      secondary_cluster_id      predicted_host_range_overall_rank       predicted_host_range_overall_name       observed_host_range_ncbi_rank   observed_host_range_ncbi_name   reported_host_range_lit_rank      reported_host_range_lit_name    associated_pmid(s)
m01_flye.racon:AE795    2       140403  0.4417213307407961      34ce615f122132c4e8a73903eb2da43b        rep_cluster_1486,rep_cluster_557        000825__CP009849_00015,001953__CP013250_00105     MOBC    CP013250_00065  -       -       -       -       mobilizable     AP014859        0.0127293       Vibrio parahaemolyticus AE795   AO650   genus   Vibrio  genus   Vibrio  ---
m01_flye.racon:AD413    1       69340   0.44936544563022784     352832786a442f1f1dc995e791e5f382        rep_cluster_1486        000824__CP021150_00027  MOBP    CP028144_00027  -       ---       mobilizable     CP021150        0.00216198      Vibrio campbellii       AD413   AM969   genus   Vibrio  genus   Vibrio  -       -       -
```

> **Comentario:**
> - `sample_id`: Identificador único de la muestra analizada. En este caso, incluye el nombre del archivo de ensamblaje (m01_flye.racon) seguido de un sufijo que podría indicar un identificador interno del análisis (AE795, AD413).
> - `num_contigs`: El número de contigs que MOB-typer agrupó como pertenecientes a este posible plásmido.
> - `size`: El tamaño total (en pares de bases) de todos los contigs agrupados para este posible plásmido.
> - `gc`: El contenido de guanina-citosina (GC) promedio de los contigs agrupados para este posible plásmido.
> - `md5`: El hash MD5 único calculado para la secuencia concatenada de los contigs agrupados, lo que puede servir como un identificador único para esta reconstrucción de plásmido.
> - `rep_type(s)`: El tipo o los tipos de replicón (región de inicio de la replicación) identificados en los contigs agrupados. Los replicones son claves para la replicación autónoma de los plásmidos. rep_cluster_1486 y rep_cluster_557 son identificadores de clústeres de replicones en la base de datos de MOB-typer.
> - `rep_type_accession(s)`: Los números de acceso en la base de datos de replicones para los tipos identificados. Estos enlaces te permitirían obtener más información sobre esos replicones específicos (ej., 000825__CP009849_00015).
> - `relaxase_type(s)`: El tipo o los tipos de relaxasa identificados. Las relaxasas son enzimas clave para la movilización de plásmidos a través de la conjugación. MOBC y MOBP son familias de relaxasas.
> - `relaxase_type_accession(s)`: Los números de acceso en la base de datos de relaxasas para los tipos identificados (ej., CP013250_00065).
> - `mpf_type`: El tipo de sistema de apareamiento y transferencia (Mating Pair Formation - MPF) que podría estar asociado con este plásmido, basado en la presencia de genes relacionados con la conjugación. En el primer caso no se identifica (-), mientras que en el segundo tampoco (---).
> - `mpf_type_accession(s)`: Los números de acceso en la base de datos para el tipo de MPF identificado (no hay en estos casos).
> - `orit_type(s)`: El tipo o los tipos de origen de transferencia (origin of transfer - oriT) identificados, que es la secuencia de ADN donde se inicia la transferencia durante la conjugación (no se identifica en estos casos).
> - `orit_accession(s)`: Los números de acceso en la base de datos para el tipo de oriT identificado (no hay en estos casos).
> - `predicted_mobility`: La predicción de la capacidad de movilización del plásmido. mobilizable indica que el plásmido probablemente puede ser transferido a otras bacterias, a menudo con la ayuda de otro plásmido conjugativo.
> - `mash_nearest_neighbor`: El identificador del plásmido más similar encontrado en la base de datos de referencia de MOB-typer utilizando la herramienta Mash (una técnica rápida de estimación de la distancia genómica).
> - `mash_neighbor_distance`: La distancia Mash entre el plásmido reconstruido y su vecino más cercano en la base de datos de referencia. Una distancia menor indica una mayor similitud.
> - `mash_neighbor_identification`: La identificación del plásmido vecino más cercano, incluyendo información sobre la especie y, a veces, la cepa (ej., Vibrio parahaemolyticus AE795, Vibrio campbellii AD413).
> - `primary_cluster_id`: Un identificador del clúster primario al que pertenece este plásmido en la base de datos de MOB-typer.
> - `secondary_cluster_id`: Un identificador del clúster secundario al que pertenece este plásmido, proporcionando una clasificación jerárquica.
> - `predicted_host_range_overall_rank`: El rango taxonómico (ej., género) del huésped predicho para este plásmido basado en los plásmidos similares en la base de datos.
> - `predicted_host_range_overall_name`: El nombre taxonómico del huésped predicho (ej., Vibrio).
> - `observed_host_range_ncbi_rank`: El rango taxonómico del huésped observado en la base de datos NCBI para plásmidos similares.
> - `observed_host_range_ncbi_name`: El nombre taxonómico del huésped observado en NCBI (ej., Vibrio).
> - `reported_host_range_lit_rank`: El rango taxonómico del huésped reportado en la literatura para plásmidos similares.
> - `reported_host_range_lit_name`: El nombre taxonómico del huésped reportado en la literatura (ej., Vibrio).
> - `associated_pmid(s)`: Los PubMed IDs (si los hay) de artículos científicos asociados con plásmidos similares en la base de datos.

## 7. Identificación de rutas metabólicas

### Ir a la pagina web de KAAS (https://www.genome.jp/kegg/kaas/)

### Hacer clic en KAAS job request

<img width="681" alt="image" src="https://github.com/user-attachments/assets/79333efb-e92d-4ec5-ad25-1cdc4ba7be86" />

### Clic en seleccionar archivo y escoger el archivo FAA del genoma, colocar en query name e e-mail address lo que corresponda, seleccionar en GENES data set la opción for Prokaryotes, y luego presionar en Compute

<img width="521" alt="image" src="https://github.com/user-attachments/assets/a9bd91b6-8d9e-4ded-b9e7-706373a7ad6a" />

### Revisar su e-mail y dar clic en Submit

### Hacer clic en html

<img width="287" alt="image" src="https://github.com/user-attachments/assets/4e8a1196-68d9-4560-8028-052c5fd9023d" />

### Explorar los resultados

<img width="330" alt="image" src="https://github.com/user-attachments/assets/1bcea43b-3b75-4916-907a-6fd170767772" />

### Explorar los resultados

<img width="427" alt="image" src="https://github.com/user-attachments/assets/3c0a54d4-f110-4ac7-b3b1-ee38251c2b61" />

<img width="694" alt="image" src="https://github.com/user-attachments/assets/0e07f44b-355d-40e2-b5a3-613aaeb8f993" />

## 8. Identificación de clústeres de genes de biosíntesis de metabolitos secundarios

### Ir a la pagina web de antiSMASH (https://antismash.secondarymetabolites.org/#!/start)

### Clic en Upload file y escoger el archivo FASTA del genoma, colocar el Detection strictness en strict, seleccionar All on la opción Extra features, y luego presionar en Submit

<img width="534" alt="image" src="https://github.com/user-attachments/assets/3f1b86f4-3628-4f25-a5cf-5d261ba743df" />

### Explorar los resultados

<img width="509" alt="image" src="https://github.com/user-attachments/assets/06580a7f-3c4d-44d5-95ad-82f9397a69f1" />

<img width="695" alt="image" src="https://github.com/user-attachments/assets/6b030610-5686-4ebc-acd7-cd9be363f14d" />

## 9. Visualización del genoma

### Con MGCplotter:

```bash
cd ~/genomics/annotation

mkdir map

cd map

conda activate mgcplotter

MGCplotter -r ~/genomics/annotation/prokka/m01.gbk -o m01_map --assign_cog_color 
```

> **Comentario:** 
> - `--assign_cog_color`: Esta opción indica a MGCplotter que asigne colores a los genes en función de sus categorías COG (Clusters of Orthologous Groups). Las categorías COG clasifican los genes según su función.

```bash
cat m01_map/cogclassifier/classifier_stats.txt 

84.62% (4395 / 5194) sequences classified into COG functional category.
```

```bash
cat m01_map/cogclassifier/classifier_count.tsv

LETTER	COUNT	COLOR	DESCRIPTION
J	264	#FCCCFC	Translation, ribosomal structure and biogenesis
A	2	#FCDCFC	RNA processing and modification
K	266	#FCDCEC	Transcription
L	201	#FCDCDC	Replication, recombination and repair
B	0	#FCDCCC	Chromatin structure and dynamics
D	54	#FCFCDC	Cell cycle control, cell division, chromosome partitioning
Y	0	#FCFCCC	Nuclear structure
V	119	#FCFCBC	Defense mechanisms
T	160	#FCFCAC	Signal transduction mechanisms
M	267	#ECFCAC	Cell wall/membrane/envelope biogenesis
N	106	#DCFCAC	Cell motility
Z	0	#CCFCAC	Cytoskeleton
W	10	#BCFCAC	Extracellular structures
U	62	#ACFCAC	Intracellular trafficking, secretion, and vesicular transport
O	156	#9CFCAC	Posttranslational modification, protein turnover, chaperones
X	721	#9CFC9C	Mobilome: prophages, transposons
C	267	#BCFCFC	Energy production and conversion
G	373	#CCFCFC	Carbohydrate transport and metabolism
E	363	#DCFCFC	Amino acid transport and metabolism
F	105	#DCECFC	Nucleotide transport and metabolism
H	187	#DCDCFC	Coenzyme transport and metabolism
I	119	#DCCCFC	Lipid transport and metabolism
P	205	#CCCCFC	Inorganic ion transport and metabolism
Q	60	#BCCCFC	Secondary metabolites biosynthesis, transport and catabolism
R	159	#E0E0E0	General function prediction only
S	169	#CCCCCC	Function unknown
```

```bash
Exportar y visualizar el archivo circos.png
```

### Con Proksee:

### Exportar el archivo m01.gbk generado por el programa Prokka e ir al programa Proksee (https://proksee.ca/)

### Hacer clic en Browse, seleccionar el archivo g00.gbk, esperar que el archivo se cargue, y hacer clic en Create Map

<img width="566" alt="image" src="https://github.com/user-attachments/assets/8bd5970a-5b02-442b-b058-f488bee5d354" />

### Realizar zoom en el mapa utilizando la rueda del ratón y localizar los tRNA/rRNA

<img width="698" alt="image" src="https://github.com/user-attachments/assets/64f4d3aa-2636-4c72-917f-f85ead755c40" />

### Hacer clic en la herramienta GC Content

<img width="198" alt="image" src="https://github.com/user-attachments/assets/4610c60c-8ac8-49b7-bf18-6c91766efa73" />

### Hacer clic en OK

<img width="698" alt="image" src="https://github.com/user-attachments/assets/89839d38-5cf3-493c-a690-6448bbb6d628" />

### Visualizar el contenido GC en el mapa del genoma

<img width="698" alt="image" src="https://github.com/user-attachments/assets/8e603f47-ff06-46df-9fbc-73be63f7f158" />

### Hacer clic en la herramienta GC Skew y visualizar el sesgo de GC en el mapa del genoma

<img width="698" alt="image" src="https://github.com/user-attachments/assets/48a7edcb-f22a-4303-b77d-df8eed927af7" />

## 10. Anotación del genoma generado en el curso

```bash
ls -lh ~/genomics/assembly/nanopore

total 11M
-rw-rw-r-- 1 alumno04 alumno04 429K abr 30 16:14 b06_flye.fasta
-rw-rw-r-- 1 alumno04 alumno04 435K abr 30 16:14 b06_flye.gfa
drwxrwxr-x 7 alumno04 alumno04 4,0K abr 30 16:26 b06_flye_nanopore
-rw-rw-r-- 1 alumno04 alumno04 4,8M abr 30 14:17 m01_flye.fasta
-rw-rw-r-- 1 alumno04 alumno04 4,8M abr 30 14:17 m01_flye.gfa
drwxrwxr-x 7 alumno04 alumno04 4,0K abr 30 14:37 m01_flye_nanopore
drwxrwxr-x 2 alumno04 alumno04 4,0K may  7 10:41 racon
```

```bash
cd ~/genomics/assembly/nanopore

conda activate genome

prinseq-lite.pl -fasta b06_flye.fasta -min_len 500 -seq_id "b06_00" -out_good b06_genome_final.fasta
```

> **Comentario:** 
> - `-fasta b06_flye.fasta`: Esta opción especifica el archivo de entrada en formato FASTA. Este archivo contiene secuencias de contigs ensamblados con Flye.
> - `-min_len 500`: Esta opción indica que se conservarán solo las secuencias (en este caso, los contigs) que tengan una longitud mínima de 500 nucleótidos. Cualquier secuencia más corta será descartada. Esto es útil para eliminar fragmentos muy pequeños que podrían ser ruido o ensamblajes incompletos.
> - `-seq_id "b06_00"`: Esta opción establece un prefijo para los identificadores (headers) de las secuencias que pasen el filtro. En este caso, a cada secuencia válida se le asignará un ID que comience con "b06_00". Si hubiera varias secuencias resultantes, PRINSEQ-lite probablemente agregaría un número secuencial a este prefijo (por ejemplo, b06_00_1, b06_00_2, etc.). Esto ayuda a estandarizar y rastrear los identificadores de las secuencias filtradas.
> - `-out_good b06_genome_final.fasta`: Esta opción especifica el nombre del archivo de salida donde se guardarán las secuencias que pasaron todos los criterios de filtrado (en este caso, solo el criterio de longitud mínima). El archivo de salida se llamará b06_genome_final.fasta y estará en formato FASTA.
