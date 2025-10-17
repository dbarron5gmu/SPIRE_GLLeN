# SPIRE_GLLeN

GLLeN is a library developed at GMU to improve the correctness and explainability of LLMs in binary decompilation tasks.<br>

To run SPIRE_GLeNN 1.0 on the GMU ORC cluster:<br>
  Create a SLURM script with this template:<br>
    #!/bin/bash<br>

    #Submit this script with: sbatch GLeNN1_Script<br>

    #SBATCH --job-name=GLeNN_1.0   ##name that will show up in the queue<br>
    #SBATCH --output=/scratch/GLeNN_1.0 output.out   ##filename of the output<br>
    #SBATCH --error=/scratch/GLeNN_1.0 output.err   ##filename of the error output<br>
    #SBATCH --nodes=2  ##number of nodes to use<br>
    #SBATCH --ntasks=4  ##number of tasks to run<br>
    #SBATCH --time=2-00:00:00  ##time for analysis (day-hour:min:sec)<br>
    #SBATCH --qos=gpu  ##quality of service<br>
    #SBATCH --cpus-per-task=128  ##the number of threads the code will use<br>
    #SBATCH --mem=64GB  ##memory allocation per node<br>
    #SBATCH --partition gpuq  ##the partition to run in<br>
    #SBATCH --gres=gpu:a100.80gb:2  ##GPU(s) allocated<br>
    #SBATCH --mail-user [user]@gmu.edu  ##your email address<br>
    #SBATCH --mail-type BEGIN  ##slurm will email you when your job starts<br>
    #SBATCH --mail-type END  ##slurm will email you when your job ends<br>
    #SBATCH --mail-type FAIL  ##slurm will email you when your job fails<br>


    ## Commands to Load Modules:<br>
    module load gnu12<br>
    module load python<br>


    ## Load modules, insert code, and run your programs here.<br>
    cd./SPIRE_GLLeN1.0-main/<br>
    pip install -r requirements.txt<br>
    cd./Database_scripts<br>
    python 1_exeBenchToC.py<br>
    python 2_gccToCFG.py<br>
    python 03_dot_to_json.py<br>
    python 04_json_to_neo4k.py<br>
    python 5_jsonToNeo4j_with_counts.py<br>
    python 08_one_off_embeddings.py<br>
    cd ..<br>
    cd./demo<br>
    python assemblySearchHandler.py<br>

Modify the sciprt to what resources are needed/available and change the email to your own.<br>
To run this script in the ORC Cluster type in: sbatch GLeNN1_script.slurm (or what you have named the file as)<br>
