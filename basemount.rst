

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
   
   /export/NFS/Saranga/BaseSpace/Projects/MiSeq v3: TruSeq Targeted RNA Expression (NFkB & Cell Cycle: Human Brain-Liver-UHRR)/Samples/Brain10/Files/:
   total 85M
   85M -r--r--r-- 1 root root 85M Oct  5 14:09 Brain10_S22_L001_R1_001.fastq.gz

   /export/NFS/Saranga/BaseSpace/Projects/MiSeq v3: TruSeq Targeted RNA Expression (NFkB & Cell Cycle: Human Brain-Liver-UHRR)/Samples/Brain11/Files/:
   total 62M
   62M -r--r--r-- 1 root root 62M Oct  5 14:09 Brain11_S23_L001_R1_001.fastq.gz


2.4. Basic analysis on fastq files
----------------

You can get basic information about your "fastq" files, such as:

- View sequences inside "fastq" files
- Number of reads for each "fastq" file
- Read length distribution 

without having to download them.



**Example: View your data**

--------------

.. code-block:: bash
   :linenos:

   zcat /export/NFS/Saranga/BaseSpace/Projects/MiSeq\ v3\:\ TruSeq\ Targeted\ RNA\ Expression\ \(NFkB\ \&\ Cell\ Cycle\:\ Human\ Brain-Liver-UHRR\)/Samples/Brain1/Files/Brain1_S13_L001_R1_001.fastq.gz | head -n 4

.. parsed-literal::

   @M03438:48:000000000-AGGNU:1:1101:11792:1006 1:N:0:13
   NTCAATCCCCAGCAGTGGAATAAGGCCTGTTGTTCCTTGCAGTGGATCCTG
   +
   #88ABFFGCFEEG<FF<FDFFEGGFGGFCFGFFGGEGGGGGGFGGFGGGGG


**Example: Count the  number of sequneces using native Linux commands**

--------------

.. code-block:: bash
   :linenos:

   zcat  /export/NFS/Saranga/BaseSpace/Projects/MiSeq\ v3\:\ TruSeq\ Targeted\ RNA\ Expression\ \(NFkB\ \&\ Cell\ Cycle\:\ Human\ Brain-Liver-UHRR\)/Samples/Brain1/Files/Brain1_S13_L001_R1_001.fastq.gz | grep -c "@M03438:"

.. parsed-literal::

   838876

:FILE SIZE: 85M
:TIME TAKEN: 1.327s



**Example: Count the  number of sequneces using using `fastqutils <http://ngsutils.org/modules/fastqutils/>`_**

--------------

.. code-block:: bash
   :linenos:

   fastqutils names /export/NFS/Saranga/BaseSpace/Projects/MiSeq\ v3\:\ TruSeq\ Targeted\ RNA\ Expression\ \(NFkB\ \&\ Cell\ Cycle\:\ Human\ Brain-Liver-UHRR\)/Samples/Brain1/Files/Brain1_S13_L001_R1_001.fastq.gz | wc -l

.. parsed-literal::

   838876

:FILE SIZE: 85M
:TIME TAKEN: 23.00s

.. toctree::
   :maxdepth: 3

   


