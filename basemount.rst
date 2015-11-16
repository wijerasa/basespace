

.. MCBL documentation master file, created by
   sphinx-quickstart on Wed Sep 23 17:00:18 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. module:: Introduction
   :synopsis: Introduction to BaseMount
.. moduleauthor:: Saranga Wijeratne<wijeratne.3@osu.edu>

.. highlight:: rest

.. figure:: _static/Logo.jpg
   :align: right

**********************************************
1. Introduction
**********************************************

1.1. File Access (Traditional Way)
--------------

.. figure:: _static/basespace_web_1.png
   :align: left

1.2. File Access (with BaseMount)
--------------

.. figure:: _static/basemount_intro.jpg
   :align: left

1.4. What is BaseMount?
---------------------

**BaseMount** is a machanisum that enables access to your **basespace storage** as a **Linux file system**.

1.5. Advantages of the BaseMount?
---------------------

- Have access to your Projects, Runs, and App results as your local files.
- Can run **local apps** on basespace data **without downloading data to your local computer.**
- Can save your local storage space.:

   "Although BaseMount does facilitate file download, we would recommend that since BaseMount allows convenient, fast, cached access to your BaseSpace metadata and files, you may find that many operations can be carried out without the need to download locally. Duringour testing, we have used BaseMount to grep through fastq files, extract blocks of reads from bam files and even use IGV on the bam files directly all without downloading files locally. This can be more convenient than including a download step and saves on the overheads of local storage." -Illumina



1.6. Official page
----------------
.. raw:: html

    <div style="margin-top:10px;">
      <iframe width="900" height="600" src="https://basemount.basespace.illumina.com" frameborder="0" allowfullscreen></iframe>
    </div>


**********************************************
2. BaseMount Installation
**********************************************

2.1. Quick Install
----------------

.. code-block:: bash
   :linenos:
   
   sudo bash -c "$(curl -L https://basemount.basespace.illumina.com/install/)"

2.2. Manual install
----------------


**Supported Operating Systems:** Ubuntu, Centos

-----

Ubuntu 14 & 15


.. code-block:: bash
   :linenos:
   
   wget https://bintray.com/artifact/download/basespace/BaseSpaceFS-DEB/bsfs_1.1.631-1_amd64.deb
   wget https://bintray.com/artifact/download/basespace/BaseMount-DEB/basemount_0.1.2.463-20150714_amd64.deb
   sudo dpkg -i --force-confmiss bsfs_1.1.631-1_amd64.deb
   sudo dpkg -i basemount_0.1.2.463-20150714_amd64.deb


2.3. Mounting Your BaseSpace Account
----------------

.. code-block:: bash
   :linenos:
   
   basemount --config {config_file_prefix} {mount-point folder}
   basemount --config user1 ~/BaseSpace_Mount

**Example:**

------

.. code-block:: bash
   :linenos:

   mkdir /export/NFS/Saranga/BaseSpace
   mkdir /export/NFS/Maria/BaseSpace
   basemount --config Maria /export/NFS/Maria/BaseSpace/


.. figure:: _static/basemount_first.png
   :align: left


Then open your internet browser,

.. figure:: _static/basemount_sec.png
   :align: left



After you click "Accept",

.. figure:: _static/basemount_third.png
   :align: left

.. figure:: _static/basemount_fourth.png
   :align: left


To access the folder, type,

.. code-block:: bash
   :linenos:

   cd /export/NFS/Maria/BaseSpace/
   ls

.. parsed-literal::

   Projects  Runs

To see the contents in the Projects,

.. code-block:: bash
   :linenos:
   
   ls -lsh /export/NFS/Saranga/BaseSpace/Projects/HiSeq\ 2500\ -\ v4\ reagents\:\ TruSeq\ PCR\ Free\ \(4\ replicates\ of\ NA12877\)/Samples/NA12877_*/Files/

.. parsed-literal::
   
   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L1 (2)/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L1_S1_L001_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L1_S1_L001_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L1/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  1  2014 NA12877-L1_S1_L001_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  1  2014 NA12877-L1_S1_L001_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L2 (2)/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L2_S2_L002_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L2_S2_L002_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L2/Files/:
   total 0

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L3 (2)/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L3_S3_L003_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L3_S3_L003_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L3/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  1  2014 NA12877-L3_S3_L003_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  1  2014 NA12877-L3_S3_L003_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L4 (2)/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L4_S4_L004_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L4_S4_L004_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L4/Files/:
   total 0

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L5 (2)/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L5_S5_L005_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L5_S5_L005_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L5/Files/:
   total 0

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L6 (2)/Files/:
   total 38G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L6_S6_L006_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L6_S6_L006_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L6/Files/:
   total 0

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L7 (2)/Files/:
   total 38G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L7_S7_L007_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L7_S7_L007_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L7/Files/:
   total 0

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L8 (2)/Files/:
   total 37G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L8_S8_L008_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L8_S8_L008_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_L8/Files/:
   total 0

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_rep1/Files/:
   total 74G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L1_S1_L001_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L1_S1_L001_R2_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L2_S2_L002_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L2_S2_L002_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_rep2/Files/:
   total 74G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L3_S3_L003_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L3_S3_L003_R2_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L4_S4_L004_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L4_S4_L004_R2_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/HiSeq 2500 - v4 reagents: TruSeq PCR Free (4 replicates of NA12877)/Samples/NA12877_rep3/Files/:
   total 74G
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L5_S5_L005_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L5_S5_L005_R2_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L6_S6_L006_R1_001.fastq.gz
   19G -r--r--r-- 1 root root 19G Oct  3  2014 NA12877-L6_S6_L006_R2_001.fastq.gz

.. toctree::
   :maxdepth: 3

   


