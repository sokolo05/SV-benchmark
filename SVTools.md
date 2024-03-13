## NanoSV 
### 1. 生成bed文件
```
cd ~/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam
samtools view -h PacBio_CCS_15.minimap2.sorted.bam | awk '{print $3, $4-1, $5}' > PacBio_CCS_15.minimap2.sorted.bed
samtools view -h PacBio_CCS_15.ngmlr.sorted.bam | awk '{print $3, $4-1, $5}' > PacBio_CCS_15.ngmlr.sorted.bed
samtools view -h PacBio_CCS_15.winnowmap.sorted.bam | awk '{print $3, $4-1, $5}' > PacBio_CCS_15.winnowmap.sorted.bed
```
### 2. SV检测
```
# minimap2-NanoSV
NanoSV -t 8 -b ~/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/PacBio_CCS_15.minimap2.sorted.bed
            -o /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/PacBio_CCS_15.minimap2.NanoSV.vcf
                /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/PacBio_CCS_15.minimap2.sorted.bam
# ngmlr-NanoSV
NanoSV -t 8 -b ~/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/PacBio_CCS_15.ngmlr.sorted.bed
            -o /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/PacBio_CCS_15.ngmlr.NanoSV.vcf
                /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/PacBio_CCS_15.ngmlr.sorted.bam
# winnowmap-NanoSV
NanoSV -t 8 -b ~/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/PacBio_CCS_15.winnowmap.sorted.bed
            -o /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/3_SV_calls/PacBio_CCS_15.winnowmap.NanoSV.vcf
                /home/laicx/study/02.svcode/07.nextsv/04.nextsv_output/2_aligned_bam/PacBio_CCS_15.winnowmap.sorted.bam 
```
