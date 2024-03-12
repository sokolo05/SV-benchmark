## 1.使用nextsv生成执行的sh文件
```
python nextsv3.py -a minimap2+winnowmap+ngmlr -i /ifs1/laicx/02.human-dataset/HG002_NA24385_son/PacBio_CCS_15kb/HG002/02.fastq_file -o ./04.nextsv_output -s PacBio_CCS_15 -r /ifs1/laicx/01.reference/GRCh37-hg19/human_hs37d5/human_hs37d5.fasta  -t 8 -p hifi
```
## 2.比对的bam文件生成耗费资源
```
ln -s /ifs1/laicx/02.human-dataset/HG002_NA24385_son/PacBio_CCS_15kb/HG002/04.nextsv_output/2_aligned_bam ./2_aligned_bam
```
  ### 删除链接：rm 链接名称
  ```
    rm 2_aligned_bam
  ```
  注：rm 2_aligned_bam/ 删除的是整个文件夹（连同源文件）切记不要误删bam文件
## 3.执行nextsv工具生成的work.sh文件
需要首先注释数据清洗和序列比对过程的.sh文件，即文件夹 1_clean_reads/2_aligned_bam中的全部.sh文件
```
#!/bin/bash
#PBS -N PacBio_nextsv_work
#PBS -l mem=20gb
#PBS -o ./
#PBS -e ./

cd $PBS_O_WORKDIR
echo $PBS_O_WORKDIR

source activate nextsv3.8

# sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/1_clean_reads/get_clean_reads.sh
# sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/run_minimap2.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_sniffles_for_minimap2.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_svim_for_minimap2.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_pbsv_for_minimap2.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_nanovar_for_minimap2.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_NanoSV_for_minimap2.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_cuteSV_for_minimap2.PacBio_CCS_15.sh
# sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/run_winnowmap.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_sniffles_for_winnowmap.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_svim_for_winnowmap.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_pbsv_for_winnowmap.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_nanovar_for_winnowmap.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_NanoSV_for_winnowmap.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_cuteSV_for_winnowmap.PacBio_CCS_15.sh
# sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/run_ngmlr.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_sniffles_for_ngmlr.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_svim_for_ngmlr.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_pbsv_for_ngmlr.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_nanovar_for_ngmlr.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_NanoSV_for_ngmlr.PacBio_CCS_15.sh
sh /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/run_cuteSV_for_ngmlr.PacBio_CCS_15.sh
```
