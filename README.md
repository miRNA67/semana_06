# Semana 06: Anotación de genomas

## Logro de la sesión: 

Al finalizar la unidad, el estudiante utiliza herramientas bioinformáticas para realizar la anotación de un genoma ensamblado.

# Estructura de la práctica:

1. Acceso al servidor de cómputo
2. Anotación global de un genoma
3. Validación de la anotación global
4. Identificación de genes de virulencia
5. Identificación de genes de resistencia a antibióticos
6. Identificación de rutas metabólicas
7. Identificación de genes de biosíntesis de metabolitos secundarios
8. Identificación de elementos móviles 
9. Visualización de la anotación de un genoma

## Programas requeridos:

### Programas de acceso al servidor:

PuTTY v0.79 https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
   - **Descripción:** PuTTY es un cliente SSH, Telnet y Rlogin gratuito y de código abierto para Windows y sistemas Unix. Se utiliza principalmente para establecer conexiones seguras de línea de comandos a servidores remotos.

WinSCP v6.1 https://winscp.net/eng/download.php
   - **Descripción:** WinSCP es un cliente SFTP, FTP, WebDAV, Amazon S3 y SCP gratuito y de código abierto para Windows. Permite la transferencia segura de archivos entre un ordenador local y servidores remotos mediante una interfaz gráfica de usuario. 

### Programas bioinformáticos:

Bandage v0.8.1 http://rrwick.github.io/Bandage/
   - **Descripción:** Bandage es una herramienta para visualizar grafos de ensamblaje de genomas. Permite explorar las relaciones entre los contigs (fragmentos de ADN ensamblados) y puede ayudar a identificar problemas en el ensamblaje, como colapsos de repeticiones o errores. Su nombre es un acrónimo de "Bandage is a nice de novo assembly graph explorer".
Canu v2.2 http://canu.readthedocs.org/

Barrnap v0.9 https://github.com/tseemann/barrnap
   - **Descripción:** Barrnap (Bacterial rRNA prediction program) es un programa que predice las secuencias de ARN ribosomal (rRNA) en genomas bacterianos y arqueales. La identificación de los genes de rRNA es importante para estudios filogenéticos y metagenómicos.

CheckM v1.2.2 https://ecogenomics.github.io/CheckM/
   - **Descripción:** CheckM es una herramienta que evalúa la calidad de los metagenomas ensamblados y de los genomas ensamblados a partir de metagenomas (MAGs). Proporciona estimaciones de completitud y contaminación basadas en marcadores genéticos.

Flye v2.9.2 https://github.com/fenderglass/Flye/
   - **Descripción:** Flye es un ensamblador de novo enfocado en lecturas largas. Se destaca por su velocidad y eficiencia en el uso de memoria, lo que lo hace adecuado para ensamblar genomas grandes en recursos computacionales limitados.
Kraken2 v2.1.3 https://ccb.jhu.edu/software/kraken2/

Minimap2 v2.29.0 https://github.com/lh3/minimap2
   - **Descripción:** es un alineador de secuencias rápido y versátil diseñado para alinear secuencias largas de ADN o ARN, como lecturas de Nanopore y PacBio contra genomas de referencia o ensamblajes, así como lecturas largas entre sí para el ensamblaje de novo y lecturas cortas contra genomas; se destaca por su velocidad, sensibilidad robusta frente a errores en lecturas largas, su formato de salida PAF y una amplia gama de opciones de personalización mediante indexación eficiente basada en minimizadores, siendo una herramienta fundamental para diversas tareas de análisis genómico.

Quast v5.2.0 http://quast.sourceforge.net/
   - **Descripción:** QUAST (Quality Assessment Tool for Genome Assemblies) es una herramienta que calcula una amplia variedad de métricas para evaluar la calidad de los ensamblajes de genomas. Proporciona estadísticas detalladas sobre la contigüidad, la precisión y la completitud del ensamblaje.

Racon v1.5.0 https://github.com/lbcb-sci/racon
   - **Descripción:** Racon es una herramienta para el pulido (polishing) de ensamblajes de genomas, especialmente aquellos generados a partir de lecturas largas. Utiliza las lecturas originales para corregir errores y mejorar la precisión del ensamblaje final.

Unicycler v0.5.1 https://github.com/rrwick/Unicycler
   - **Descripción:** Unicycler es una herramienta bioinformática de código abierto diseñada para ensamblar genomas bacterianos (y otros genomas pequeños) a partir de datos de secuenciación. Su principal fortaleza radica en su capacidad para manejar conjuntos de datos híbridos, que combinan lecturas cortas y precisas (como las de Illumina) con lecturas largas que abarcan más distancia (como las de Oxford Nanopore o PacBio). Al aprovechar las ventajas de ambos tipos de datos, Unicycler puede generar ensamblajes más completos y contiguos, especialmente en regiones complejas como repeticiones.
     
### Herramientas bioinformáticas en línea:

16S-based ID https://www.ezbiocloud.net/identify
   - **Descripción:** Esta es una herramienta en línea proporcionada por EzBioCloud que permite la identificación taxonómica de bacterias y arqueas basada en la secuencia del gen 16S rRNA, un marcador molecular comúnmente utilizado en estudios de diversidad microbiana.

blastn https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastn&BLAST_SPEC=GeoBlast&PAGE_TYPE=BlastSearch
   - **Descripción:** BLASTn (Basic Local Alignment Search Tool - nucleotide) es una herramienta en línea del NCBI (National Center for Biotechnology Information) que permite buscar secuencias de nucleótidos (ADN o ARN) contra bases de datos de secuencias de nucleótidos. Encuentra regiones de similitud local entre tu secuencia de consulta y las secuencias en la base de datos, lo que te permite identificar secuencias relacionadas o similares. 

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

conda activate abricate

mkdir abricate

cd abricate

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

## 5. Identificación de genes de resistencia a antibióticos

```bash
cd ~/genomics/annotation

mkdir rgi

cd rgi

mkdir card

cd card

conda activate annotation_02

wget https://card.mcmaster.ca/latest/data

tar -xvf data ./card.json

cd ..

rgi load --card_json card/card.json --local

rgi main --input_sequence /home/ins_user/genomics/assembly/nanopore/m01_flye.racon.fasta --output_file m01_rgi --clean --local --num_threads 2
```

> **Comentario:** 
> - `--clean`: Elimina archivos temporales.
> - `--local`: Especifica que RGI debe utilizar la base de datos local instalada en tu sistema. 

```bash
head -n 2 m01_rgi.txt 

ORF_ID	Contig	Start	Stop	Orientation	Cut_Off	Pass_Bitscore	Best_Hit_Bitscore	Best_Hit_ARO	Best_Identities	ARO	Model_type	SNPs_in_Best_Hit_ARO	Other_SNPs	Drug Class	Resistance Mechanism	AMR Gene Family	Predicted_DNA	Predicted_Protein	CARD_Protein_Sequence	Percentage Length of Reference Sequence	ID	Model_ID	Nudged	Note	Hit_Start	Hit_End	Antibiotic
contig_1_165 # 169570 # 170943 # -1 # ID=1_165;partial=00;start_type=ATG;rbs_motif=None;rbs_spacer=None;gc_cont=0.547	contig_1_165	169570	170943	-	Perfect	890	926.391	cpxA	100.0	3000830	protein homolog model	n/a	n/a	aminoglycoside antibiotic; aminocoumarin antibiotic	antibiotic efflux	resistance-nodulation-cell division (RND) antibiotic efflux pump	ATGATAGGCAGCTTAACCGCGCGCATCTTCGCCATCTTCTGGCTGACGCTGGCGCTGGTGTTGATGTTGGTTTTGATGTTACCCAAGCTCGATTCACGCCAGATGACCGAGCTTCTGGATAGCGAACAGCGTCAGGGGCTGATGATTGAGCAGCATGTCGAAGCGGAGCTGGCGAACGATCCGCCCAACGATTTAATGTGGTGGCGGCGTCTGTTCCGGGCGATTGATAAGTGGGCACCGCCAGGACAGCGTTTGTTATTGGTGACCACCGAAGGCCGCGTGATCGGCGCTGAACGCAGCGAAATGCAGATCATTCGTAACTTTATTGGTCAGGCCGATAACGCCGATCATCCGCAGAAGAAAAAGTATGGCCGCGTGGAACTGGTCGGTCCGTTCTCCGTGCGTGATGGCGAAGATAATTACCAACTTTATCTGATTCGTCCGGCCAGCAGTTCTCAATCCGATTTCATTAACTTACTGTTTGACCGCCCGCTATTACTGCTGATTGTCACCATGTTGGTCAGTACGCCGCTGCTGTTGTGGTTGGCCTGGAGTCTGGCAAAACCGGCGCGTAAGCTGAAAAACGCTGCCGATGAAGTTGCCCAGGGAAACTTACGCCAGCACCCGGAACTGGAAGCGGGGCCACAGGAATTCCTTGCCGCAGGTGCCAGTTTTAACCAGATGGTCACCGCGCTGGAGCGCATGATGACCTCTCAGCAGCGTCTGCTTTCTGATATCTCTCACGAGCTGCGCACCCCGCTGACGCGTCTGCAACTGGGTACGGCGTTACTGCGCCGTCGTAGCGGTGAAAGCAAGGAACTCGAGCGTATTGAAACCGAAGCGCAACGTCTGGACAGCATGATCAACGATCTGTTGGTGATGTCACGTAATCAGCAAAAAAACGCGCTGGTTAGCGAAACCATCAAAGCCAACCAGTTGTGGAGTGAAGTGCTGGATAACGCGGCGTTCGAAGCCGAGCAAATGGGCAAGTCGTTGACAGTTAACTTCCCGCCTGGGCCGTGGCCGCTGTACGGCAATCCGAACGCCCTGGAAAGTGCGCTGGAAAACATTGTTCGTAATGCTCTGCGTTATTCCCATACGAAGATTGAAGTGGGCTTTGCGGTAGATAAAGACGGTATCACCATTACGGTGGACGACGATGGTCCTGGCGTTAGCCCGGAAGATCGCGAACAGATTTTCCGTCCGTTCTATCGGACCGATGAAGCACGCGATCGTGAATCTGGCGGTACAGGATTGGGGCTGGCGATTGTTGAAACCGCCATTCAGCAGCATCGTGGCTGGGTGAAGGCAGAAGACAGCCCGCTGGGCGGTTTACGGCTGGTGATTTGGTTGCCGCTGTATAAGCGGAGTTAA	MIGSLTARIFAIFWLTLALVLMLVLMLPKLDSRQMTELLDSEQRQGLMIEQHVEAELANDPPNDLMWWRRLFRAIDKWAPPGQRLLLVTTEGRVIGAERSEMQIIRNFIGQADNADHPQKKKYGRVELVGPFSVRDGEDNYQLYLIRPASSSQSDFINLLFDRPLLLLIVTMLVSTPLLLWLAWSLAKPARKLKNAADEVAQGNLRQHPELEAGPQEFLAAGASFNQMVTALERMMTSQQRLLSDISHELRTPLTRLQLGTALLRRRSGESKELERIETEAQRLDSMINDLLVMSRNQQKNALVSETIKANQLWSEVLDNAAFEAEQMGKSLTVNFPPGPWPLYGNPNALESALENIVRNALRYSHTKIEVGFAVDKDGITITVDDDGPGVSPEDREQIFRPFYRTDEARDRESGGTGLGLAIVETAIQQHRGWVKAEDSPLGGLRLVIWLPLYKRS	MIGSLTARIFAIFWLTLALVLMLVLMLPKLDSRQMTELLDSEQRQGLMIEQHVEAELANDPPNDLMWWRRLFRAIDKWAPPGQRLLLVTTEGRVIGAERSEMQIIRNFIGQADNADHPQKKKYGRVELVGPFSVRDGEDNYQLYLIRPASSSQSDFINLLFDRPLLLLIVTMLVSTPLLLWLAWSLAKPARKLKNAADEVAQGNLRQHPELEAGPQEFLAAGASFNQMVTALERMMTSQQRLLSDISHELRTPLTRLQLGTALLRRRSGESKELERIETEAQRLDSMINDLLVMSRNQQKNALVSETIKANQLWSEVLDNAAFEAEQMGKSLTVNFPPGPWPLYGNPNALESALENIVRNALRYSHTKIEVGFAVDKDGITITVDDDGPGVSPEDREQIFRPFYRTDEARDRESGGTGLGLAIVETAIQQHRGWVKAEDSPLGGLRLVIWLPLYKRS	100.00	gnl|BL_ORD_ID|131|hsp_num:0	152			0	1371	neomycin; amikacin; kanamycin A; tobramycin; novobiocin; gentamicin
```










