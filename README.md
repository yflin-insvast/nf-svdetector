# nf-svdetector
svdetector
检测的类型：common sv and CNV


## short reads methods
- delly
- lumpy
- wham
- pindel(too old)
- sentieon SVsolver
- manta(tumor)

还有其他的方法、流程，要去TCGA上去找（肿瘤起码有四个流程，除了manta之外还有其他不少于3个）


### 二代short reads
检测结果可信度优先级
- deletion
- dup
- insertion
- others

## tools
- svtools
- gatk-sv  (文献例子，孤独症项目)


## long reads methods
- sentieon LongReadSV
- ONT: cuteSV, Sniffles
- PacBio: pbsv

## cliping stats


## citations


## merging and compare results
- SURVIVOR(可能有坑，不同长度参数出来的结果一致性较差)


## SV的注释

## 结果处理
通常有不同方法间“取交集”和“取并集”两种方案
最常见的就是取交集，基本上多个算法都能检测出来的事件，大概率就是真实存在的
一般不做什么特别的过滤，什么样本支持数等等
最重要的处理其实是注释，AnnotSV（人类）
通过注释功能意义，从而寻找出与表型变化/差异的主效SV

SV的数据库，目前只有人的，dbVar
研究 dbVar，ClinVar， TCGA


人工核对，客户自己做
可视化，SAMplot

人类基因组重复区域的lackness
Structural variants (SVs) in repetitive regions are often missed when using short-read sequencing data. This is because short-read-based algorithms have a lower recall rate in repetitive regions than long-read-based algorithms. To obtain a more complete variant dataset, improved strategies are needed, such as incorporating multiple variant detection algorithms or alternative algorithms specific to SVs in repetitive regions.

有明确群体做的SV通常比个体的结果要好得多

根据项目的要求来，做一个SV是有其目的的

## 样本异常，比如说SV特别多，运行很慢
可以考虑做个PCA，看看异常样本和其他样本的关系，是否有一些实验上的特殊处理


## 影响运行效率的问题
基因组复杂程度，样本与参考基因组个体的差异



# components github repo
- https://github.com/dellytools/delly/
- https://github.com/arq5x/lumpy-sv
- https://github.com/zeeev/wham
- https://github.com/genome/pindel
- https://github.com/fritzsedlazeck/SURVIVOR

# blue print
use lumpy and delly to detecting SV events, then use SURVIVOR gets intersection between
lumpy's results and delly's. inters-SV is the final results.

# parameters
defaults


