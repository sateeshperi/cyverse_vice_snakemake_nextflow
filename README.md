# cyverse_vice_snakemake_nextflow

[![CyVerse VICE](https://de.cyverse.org/Powered-By-CyVerse-blue.svg)](https://de.cyverse.org/de/?type=quick-launch&quick-launch-id=fb7d1330-9b39-458c-b760-60bde08301b6&app-id=0f4b3044-e6ef-11ea-844a-008cfa5ae621)


Tool/Service | Binder | CyVerse VICE | UArizona HPC | Notes
:----- | :----: | -----: | -----: | -----:
Cost   | Free | Free | Limited | align
Conda  | Yes  | Yes | Yes | mamba for faster management
Docker  | No  | Noo* | No | 
Singularity  | No  | No* | Yes | 
iRODS  | No  | Yes | Yes | 

Tool/Service | Snakemake | Nextflow | Makeflow | Notes
:----- | :----: | -----: | -----: | -----:
Language   | Python | Groovy | ? | 
Language   | Python | Groovy | ? | 

Conda  | Yes  | Yes | Yes | 
Conda  | Yes  | Yes | Yes | 
Conda  | Yes  | Yes | Yes | 

Snakemake builds its DAG backwards from a final set of required output files
Nextflow starts with input files and builds a DAG upwards. 
Nextflow is Groovy
Snakemake is Python.

Subjectively, I find it much more pleasing to use Snakemake. Having a dry-run option (an ability to check which files will be affected by the run without actually triggering pipeline), no need to call publishDir every time, the fact that Nextflow does not 'resume' by default, recalculating the whole pipeline if you forgot to use the flag in the command line (google Nextflow resume - there is a bunch of blog posts demystifying a and troubleshooting a feature which you shouldn't even think about), Python vs Groovy (an important difference, because for complex pipelines you will have to implement some of the workflow logic in the available language) and declarative vs imperative style of thinking are the key criteria for me.

Snakemake uses paths to identify products, while Nextflow use hashes, which means that if you change a rule, snakemake will overwrite the previous result while nextflow will keep both in its cache under two different hashes. This makes it easier to go back and forth between different versions of your pipeline in nextflow, at the cost of disk bloat.

