# Asteroid
* executar

* Instalação
  
```bash
gitclone git clone --recursive https://github.com/BenoitMorel/Asteroid
mkdir build && cd build
cmake ..
make -j4
```

```bash
~/programas/Asteroid/build/bin/asteroid -h
 ```

* Argumentos

  
```bash
-i | --input-gene-trees <STRING>         Path to file containing one gene tree per line, in newick format
-r | --random-starting-trees <INTEGER>   Number of starting random trees. 0 to start from an ASTRID tree. Default value is 1.
-b | --bs-replicates <INTEGER>                   Number of bootstrap trees to compute. Default is 0.
--input-bs-gene-trees <STRING> | The set of gene trees used to perform boostrapping. If not set, the intput gene trees (-i) are used instead.
-p | --prefix <STRING>                   Prefix for the output files.
-m | --gene-species-mapping <STRING>     Path to the mapping file. If unset, Asteroid assumes that the gene tree leaf labels correspond to the species names. See our wiki for the format.
--seed <INTEGER>                         Random seed. Default is 1.
-n | --no-correction                     When set, Asteroid disables its missing data correction, and the algorithm is then equivalent to ASTRID.
--min-bl <REAL>                          Branches with a length under this value will be contracted into polotomies before computing the distance matrices. DEfault value is -1.0 (no contraction)
--use-gene-bl                            Use the gene tree branch lengths instead of their internode distance to build the distance matrices
(phyluce-1.7.3) (phylomissforest_env) [tiagobelintani@access2 build]$  
```

* Executar programa no servidor

```bash
#!/bin/bash  
#SBATCH --time=5:00:00
#SBATCH --cpus-per-task=4
#SBATCH --mem=16G


module load miniconda/3-2023-09
source activate /home/tiagobelintani/miniconda3/envs/phyluce-1.7.3


mpiexec -np 4 /home/tiagobelintani/programas/Asteroid/build/bin/asteroid \
  -i genes.tree \
  -r 10 \
  -p barychelidae \
  --seed 1986
```




