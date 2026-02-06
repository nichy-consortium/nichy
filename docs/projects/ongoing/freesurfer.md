# FreeSurfer project - brain morphology

## About the project

**Full title:** Brain morphology in central disorders of hypersomnolence: First analysis from the global multi-site neuroimaging consortium NICHY

**Analysis leads:** Eva van Heese, Niels de Joode, and Keetje Voogd

**Contact details:** nichy@amsterdamumc.nl

This project represents the **first analysis of the NICHY consortium**. This first study focuses on **brain morphology** of the **cortex and subcortex** using **T1-weighted MRI** data. Specifically, we aim to:  

- Improve understanding of **brain morphometry** differences between narcolepsy type 1, type 2, idiopathic hypersomnia, and controls.  
- Examine relationships between brain morphometry alterations and **clinical characteristics**, such as disease severity, diagnostic outcomes (MSLT, PSG), onset, duration, and medication use.  

The preregistration of this analysis is available at [the open science framework](https://osf.io/8fdqc).

---

## Before you start

### Leaderboard

To help monitor each site's progress, we maintain a **leaderboard** that outlines all the steps detailed in these guidelines. If you are responsible for data processing at your site, please:

1. **Request access** to the NICHY Leaderboard.  
2. **Regularly update your progress** as you complete each step of the analysis pipeline.

You can view the leaderboard here:  
👉 [NICHY Leaderboard](https://docs.google.com/spreadsheets/d/1t4-qiyZM0aJkHxsnCzTBjaEYqRw58aoUS0GbYrUE9fw/edit?gid=0#gid=0)

> **Note:** With the above link, you can **view** the leaderboard but cannot make edits.  
> To update your site’s progress, please **request editor rights** from the coordinating team.

### Site survey

If you have not done so yet, please complete this **short survey** (under 5 minutes).  
It helps us understand the **current status of your data**, your **processing environment**, and any **support you may need**:  
[Site survey](https://docs.google.com/forms/d/e/1FAIpQLSdORyRZCVdTuiS87djCiUK1fPGj6C6Ylt42YGFNKoDAZDmSNg/viewform)

### Responsible person

Each site should identify a **responsible person** to run the analysis.  

- This **does not** need to be a radiologist or someone with extensive technical expertise.  
- A motivated student or researcher can perform the processing steps using our manual and guidance.  
- The key requirements are **motivation, time, and access to the MRI data**.  

We estimate that **data organization and processing** will take a few hours per week for ~3 months. Sites who can dedicate more time may finish faster.  
This responsible person will be listed as a **co-author** on the resulting manuscript.

### General timeline

- Data organisation and processing can begin **immediately** after the workshops (Oct 8/9) if your site is ready.  
- We aim for **most centres to start preprocessing by the end of October**.  
- We expect **most sites to finish by spring 2026**. Extensions into the first months of 2026 are possible after consulting with the NICHY analysis team.

### Analysis workflow and documentation

The workflow used for this project has been developed and thoroughly tested by the [**ENIGMA consortium**](https://enigma.ini.usc.edu/), which has a very similar structure to NICHY. On this page, we will link to ENIGMA resources for step-by-step guidance, and provide additional NICHY-specific information.

The tools selected for the analysis were chosen for two main reasons:

1. **Consistency across sites:**  
   To make sure that the analysis is performed in the **exact same way** at each participating site.  
   This harmonized approach is essential to reduce **site effects** in large-scale neuroimaging studies.

2. **Ease of use:**  
   The tools are designed to be as **user-friendly** as possible, even for researchers or students with limited experience in MRI processing.  
   They require **no programming background**, only access to a **server** and the **MRI data**. Some **basic skills** in working with files, command-line tools, or general computer usage can help speed up the setup and processing.

While there may be an **initial learning curve**, once you complete the setup you will find the tools highly efficient and reliable for running analyses at your site.

The figure below shows how the steps for data organisation and processing. Most of these steps will be performed using the **Nipoppy framework**, which automates and streamlines the workflow. The links in each section in this document will take you to the **ENIGMA-infra** documentation, which provides more detailed instructions.

![NICHY Freesurfer workflow](../../assets/images/NICHY_freesurfer_workflow.jpg)

### Guidance

This page contains all the **relevant information** you need to run the analysis at your site. In addition, each site will be assigned **one of the three analysis team members** — Eva van Heese, Niels de Joode, or Keetje Voogd — for **personal guidance**.

With your assigned team member, you will have:  

- An **introduction meeting** to go over the workflow, tools, and any site-specific questions.  
- **Regular check-ins** to monitor progress, troubleshoot issues, and ensure your site stays on track with the analysis.  

---

## System requirements

### Linux server

To run the analysis, you need access to a **Linux server**. The server should have enough storage and memory to handle MRI data and the processing steps. 

If you are not sure whether you have access to a Linux server, please ask around at your institute, your IT department or colleagues in neuroimaging/research computing may be able to help.  

If a suitable server is not available, **please reach out to the NICHY analysis team** for advice.

### Using containers

We will be using **containerized pipelines** for running FreeSurfer 7 segmentation, subsegmentations, the quality control script, and potentially BIDSification.  

#### What are containers? 
We will be using containerized pipelines or "containers" for data processing. Containers are self-contained software environments that package **all the tools, dependencies, and code** needed to run an analysis. This ensures that each step is run **reproducibly and consistently**, regardless of the system you are using. Containers help avoid problems with software versions, missing packages, or different operating systems, which can otherwise make large-scale analyses difficult to replicate.

To use containers, you need a **container platform**. We strongly recommend **Apptainer** (previously Singularity). These programs allow you to **download, manage, and run containerized pipelines** safely on Linux systems without needing admin rights. 

![NICHY Freesurfer workflow](../../assets/images/container_infographic.png)

#### Checking for an existing installation
You may already have Apptainer/Singularity installed on your machine. You can try this by simply running `apptainer` or `singularity` in your command line and see if it throws an error. Sometimes you will need to load it to your environment, for example by running `module load apptainer`. If you don't have a container platform installed, you can find how to do this below.

#### Installing container software
[Install Apptainer here](https://github.com/apptainer/apptainer/blob/main/INSTALL.md) 

> **Note:** In some environments (e.g. shared servers), you may not be allowed to install software yourself. 
> In that case, please contact your system administrators and request that they install Apptainer for you. 

#### Building and pulling containers
Most containers used in scientific pipelines are built by developers and then hosted online (for example, on [Docker Hub](https://hub.docker.com/) or other registries). What you actually download is a **container image**, which is a file that packages all the necessary software and dependencies.  

For Apptainer, this image is stored as a single `.sif` file (Singularity Image Format). You do not need to build everything from scratch, instead, you can **pull** the image from the cloud and convert it into a `.sif` container with a single command.  

This process is:
- **Reproducible** – everyone pulls the exact same software environment.  
- **Safe** – the build command only creates the `.sif` file and does not change your system. 

***Example command:**
For Apptainer, run:
```bash
apptainer build <pipeline>_<version>.sif \
                    docker://<repository>/<pipeline>:<version>
```

## Storing container images
Nipoppy encourages the use of a common directory for storing container images, which can be shared across datasets/individuals. This directory can be anywhere on a system. 

> **Note:** In the global config file, `<NIPOPPY_DPATH_CONTAINERS>` should be replaced by the actual path to that directory. We encourage you to create a symlink (= a shortcut pointing to another file or directory, allowing access from a different location without copying the original) from the `<DATASET_ROOT>/containers directory` inside the Nipoppy dataset to the shared container store location. This makes it easy for anyone inspecting the dataset to find the containers. If you create this symlink, you don’t need to set `<NIPOPPY_DPATH_CONTAINERS>` manually, because Nipoppy will automatically use `<DATASET_ROOT>/containers` by default.

## **1) Data organisation: Setting up Nipoppy**

**Summary:**  
Nipoppy is a lightweight framework for standardized data organization and processing of neuroimaging-clinical datasets. It helps users adopt the [FAIR principles](https://www.go-fair.org/fair-principles/){:target="_blank"} and improves reproducibility. The collaboration between large consortia (such as ENIGMA, NICHY) and the Nipoppy team has streamlined data curation, processing, and analysis workflows, simplifying tracking of data, addition of new pipelines, and upgrades of existing pipelines.  

**Aim:**  
To standardize dataset organization, ensure reproducibility, and facilitate smooth use of processing pipelines.  

**Support:**  
Join the [Nipoppy Discord channel](https://discord.gg/dQGYADCCMB){:target="_blank"} for questions and community support.  
Full Nipoppy documentation is available [here](https://nipoppy.readthedocs.io/en/stable/index.html){:target="_blank"}.

> **NICHY-specific note**
> We recommend to name your data root folder (the folder that includes all data): `<your_cohort_nichy>`

[Link to instructions](https://enigma-infra.github.io/resources/how_to_guides/setting_up_nipoppy/){:target="_blank"}

---

## **2) Data processing**

When you reach this point, the hardest part is behind you! We will now use the nipoppy framework to run three different processing pipelines. Check out [this page](https://nipoppy.readthedocs.io/en/latest/how_to_guides/user_guide/processing.html){:target="_blank"} for additional information about running processing pipelines with Nipoppy.

### **Part A: Running FreeSurfer 7**

**Summary:**  
We will run FreeSurfer 7 using the fMRIPrep pipeline.  

**Aim:**  
To perform cortical and subcortical segmentation and extract standard brain morphometry measures.  

**Pipeline name:** fmriprep 

[Link to instructions](https://enigma-infra.github.io/resources/how_to_guides/freesurfer7/){:target="_blank"}

### **Part B: Running the Subsegmentations** 

**Summary:**  
This **custom pipeline**, developed by the NICHY analysis team, uses the FreeSurfer output generated in part A. The pipeline runs additional FreeSurfer functionalities to extract **subnuclei volumes** from subcortical regions (e.g., thalamus, hippocampus, brainstem, hypothalamus, amygdala). It also runs [**Sequence Adaptive Multimodal SEGmentation (SAMSEG)**](https://surfer.nmr.mgh.harvard.edu/fswiki/Samseg) to calculate a better estimate for intracranial volume.

**Aim:**  
To obtain detailed subregional volumetric measures and a better estimate for intracranial volume for more precise morphometric analyses. 

**Pipeline name:** freesurfer_subseg

[Link to instructions](https://enigma-infra.github.io/resources/how_to_guides/freesurfer_subseg/){:target="_blank"}  

### **Part C: Running the FreeSurfer Quality Control Toolbox (fsqc)**

**Summary:**  
[FreeSurfer Quality Control (FS-QC)](https://github.com/Deep-MI/fsqc) is used to assess the quality of FreeSurfer outputs, producing summary metrics and visual overviews, including tables and .html pages with screenshots for easy inspection.

**Aim:**  
To provide all the necessary information to perform reliable quality checks on cortical, subcortical, subnuclei segmentations.

**Pipeline name:** fsqc

[Link to instructions](https://enigma-infra.github.io/resources/how_to_guides/fsqc/){:target="_blank"}  

---

## **3) Quality control: visual inspection**  

**Summary:**  
Careful visual inspection of segmentations is the **most manual step** of this workflow and is essential to ensure the outputs are accurate and reliable. Even small errors or artifacts in images can lead to major mistakes in the brain segmentation. We will follow **standardized ENIGMA protocols**, with adjustments made for the Parkinson’s Disease working group, to assess the quality of cortical and subcortical segmentations.  

> **Note:** At this stage, visual quality assessment of the **subsegmentations** is **not required**, as there are no established protocols and the process would be highly time-consuming. Instead, statistical checks (e.g., outlier detection) will be used. A dedicated quality control procedure for subsegmentations may be developed in a future project when the necessary anatomical expertise is available.  

**Aim:**  
To verify whether cortical and subcortical regions, or participants, can be safely included in the final analysis.

[Link to instructions](https://enigma-infra.github.io/resources/how_to_guides/qa/){:target="_blank"}

---

## **4) Data sharing**
After completing all of the above steps, you're ready to share your derived data with the NICHY analysis team. Please:

- Review the .tsv and Excel spreadsheets for completeness, ensuring all participants are included, there are no missing or unexpected data points, and quality assessment scores have been assigned to each ROI and participant.
- Confirm whether you are authorized to share the quality check .png files. These will be used, along with your quality assessment scores, to help train automated machine learning models and (in the future) eliminate the need for manual checking in the future.

Once these checks are complete, email your analysis contact person to receive instructions for uploading the .csv files and, if applicable, the QA .png files, via SFTP to our central storage on the Compute Canada server.
