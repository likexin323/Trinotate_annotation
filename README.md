# Trinotate_annotation_note
de nove transcriptome annotation

before you start:
download and intall software as fellows: Trinity|TransDecoder|CD-HIT|NCBI-Blast+|HMMER (new and old version)|sqlite

1. download and install Trinotate (https://github.com/Trinotate/Trinotate/archive/Trinotate-v3.1.1.tar.gz)

tar zxvf Trinotate-v3.1.1.tar.gz
(此软件不需要设置环境变了，因为包含了大量的Perl预写脚本，直接设置路径调取)

#安装sqlite软件，需要进行一系列设置
#下载(https://www.sqlite.org/download.html)或者(https://www.sqlite.org/2018/sqlite-autoconf-3230100.tar.gz)
#tar zxvf sqlite-autoconf-3230100.tar.gz
#cd sqlite-autoconf-3230100
#./configure >>>> make

2. 安装Trinota软件所需的所有组件 (均需要提交教育邮箱地址验证，以下是直接的下载地址)
### signalP v4 (http://www.cbs.dtu.dk/download/C794ABB8-643C-11E8-9420-A999465A7DCF/)
#需要对signalp中的语句进行修改
#(以下引自官网https://trinotate.github.io/)
#You should edit the following line to read like so, increasing the max number of entries that can be processed:
my $MAX_ALLOWED_ENTRIES=2000000;  # default is only 10000
#also update the path to where you have the signalP software installed eg.:
$ENV{SIGNALP} = '/usr/local/src/signalp-4.1';
(将默认值10000修改成2000000, 同时需要将signalp的具体地址进行替代)

### tmhmm v2 (http://www.cbs.dtu.dk/download/A878AF6E-643B-11E8-AED3-5983465A7DCF/)
#(以下引自官网https://trinotate.github.io/)
#You might need to edit the header lines of the scripts 'tmhmm' and 'tmhmmformat.pl' to read:
#!/usr/bin/env perl (软件中自带的脚本是#!/usr/local/bin/env perl, 需要删除/local)

### RNAMMER (http://www.cbs.dtu.dk/download/EC65393A-643C-11E8-ABD7-5F9B465A7DCF/)
#(以下引自官网https://trinotate.github.io/)
#mkdir RNAMMER
#cd RNAMMER
#mv /path/to/rnammer-1.2.src.tar.Z .
#tar zxvf rnammer-1.2.src.tar.Z
RNAMMER requires the older version of hmmsearch (v2). You can obtain the hmmsearch_v2 at http://eddylab.org/software/hmmer/2.3/hmmer-2.3.tar.gz. After building the software, rename this version of hmmsearch as hmmsearch2.

#Hack the rnammer script like so; In the rnammer software configuration, edit the rnammer script to point

$HMMSEARCH_BINARY = "/path/to/hmmsearch2";
    # be sure to give the complete path to where you installed hmmsearch2.
    # update the INSTALL_PATH setting:
$INSTALL_PATH = "/dir/where/you/installed/RNAMMER";
Hack the core-rnammer script like so:

#There are two places where you'll find '--cpu 1 --compat'.  Remove the '--cpu1' at each of these places, and retain the '--compat'.
#
#
#
#
#
#
#
#
#
#
#
#
#
#
#
