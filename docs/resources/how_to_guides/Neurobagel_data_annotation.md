# NICHY Data Annotation with Neurobagel

## Why this matters
The NICHY consortium aims to collect diverse clinical data across sites to maximize the depth and breadth of our analyses. To combine data effectively, we need a consistent way to interpret variables and ensure all sites are "using the same language". The Neurobagel annotation tool provides a structured, user-friendly way to standardize how we describe clinical data, making it easier to understand what each variable means across the consortium.

As we grow and collect more standardized annotations, we hope to eventually make it easier for NICHY to discover data availability across sites for ongoing and future projects.

---

## 1. NICHY Custom Variable List  

NICHY has compiled a curated list of variables relevant to central disorders of hypersomnolence. The list covers key domains including demographics, clinical profiling, medication use, (comorbid) diagnoses, validated questionnaires, specialized sleep assessments (PSG, MSLT, actigraphy), and fluid biomarkers. 

!!! warning "Expanding our NICHY variable list"
    We are still developing our NICHY variable list. If your site collects variables that other NICHY sites may also have, and that could be valuable for current or future NICHY projects, please reach out to us. 

**Check out the NICHY variable list [here!](https://docs.google.com/spreadsheets/d/1ubx4VcJ8pq8DuKaEKq4oYcD3IZ0A9W9TB_aDn3oyLqE/edit?gid=0#gid=0)**

---

## 2. Annotation using Neurobagel
With the NICHY vocabulary integrated into the tool, sites can annotate their spreadsheets in a structured and intuitive way.

!!! info "Privacy note"
      Although the annotation interface is a web app, it runs entirely on your computer and Neurobagel **does not upload any data or retain data**. Your data are used only to populate the annotation interface (read columns and possible values).

### What sites do in this step
- Go to [https://beta-annotate.neurobagel.org/](https://beta-annotate.neurobagel.org/).
- Select **NICHY** as configuration.

![Neurobagel-NICHY-Configuration](../assets/images/Neurobagel_NICHY_screenshot.png) 

- Upload a TSV file containing demographic and clinical variables (if you still need to convert your data from CSV or Excel, see the [Neurobagel documentation on TSVs](https://neurobagel.org/glossary/#tsv). Note: Excel does not have a native TSV export option, but you can export as "Text (Tab delimited) .txt" and then rename the file extension to .tsv). Please annotate **all clinical and demographic** variables available in your dataset.

!!! info "Item-level data is valuable"
    If your site has individual item scores available, we encourage you to share and annotate these alongside the total scores. For example, if you have the Epworth Sleepiness Scale (ESS), sharing the responses to each of the eight items provides more flexibility for future analyses. Item-level data allows for more detailed analyses across NICHY projects and may reveal patterns that total scores alone cannot capture.

- New to Neurobagel? Click through the introduction windows to get started.

#### Column annotation
**Goal:** Assign each column or group of columns to a standardized variable by clicking on them.

- Select multiple related columns at once using CTRL+click or SHIFT+click
- Can't find a column? Filter your column list by name using the search bar at the top left
- Can't find a variable? Use the search bar in the assessment tool list to narrow down options
- Note that variable names in the tool may not always match your local naming conventions, for example, what your site calls "disease duration" may be listed as "time since diagnosis". 
  If a search does not return results, try alternative terms or synonyms. You can also browse the [full NICHY variable list](https://docs.google.com/spreadsheets/d/1ubx4VcJ8pq8DuKaEKq4oYcD3IZ0A9W9TB_aDn3oyLqE/edit?gid=0#gid=0) to get an overview of all available terms before annotating.
- If no variable fits your column, please use the *description* field to provide us with more context to understand this column

#### Value annotation
**Goal:** Review all columns annotated in the previous step and describe their values.

- **Mark missing values.** Neurobagel allows you to define missing values (such as -999, NA, empty strings, etc.) all at once for your entire spreadsheet. The tool will even suggest common missing value patterns it detects in your data. Once you define these, Neurobagel will apply them across all relevant columns, so you don't need to mark missing values individually for each variable.
- Optionally add short human‑readable descriptions for uncommon variables.  

#### Sharing the data dictionary

- Done? Download the data dictionary and share it together with the clinical data as explained on the [data sharing page](./data_sharing.md). 

### Questions and support
For questions, please reach out to the NICHY team and join [the Neurobagel discord server](https://discord.gg/sxnCT4QJ7a) for support.

### Why this helps
- Produces a consistent, machine‑readable data dictionary for each cohort.  
- Reduces human error compared to manual data dictionaries (if you make a mistake during annotation, you can simply load your data dictionary into the tool again and correct it)
- Makes datasets easier to understand, reuse, and combine.  

**Interested to learn more about Neurobagel?** Check out the Neurobagel documentation [here](https://neurobagel.org/user_guide/annotation_tool/)

---

## Feedback from early adopters  
- Annotation is straightforward and user‑friendly. It typically takes under an hour for a dataset of around 100 variables. And if you cannot finish in one go, you can always save your progress and continue later.   
- The main time investment is **the column annotation step**, selecting the correct variable from the ENIGMA‑PD vocabulary.  
- Overall experience: not difficult, but requires some attention to detail.

??? info "Add your feedback to improve the tool"
    The Neurobagel team continues to improve this tool together with us. If you have an idea for an improvement or find something difficult or confusing, please use the purple button "Give us feedback" on the right edge of the screen.

---

## Summary: next steps for sites  
- Annotate your clinical spreadsheet using the NICHY variable list and Neurobagel tool.  
- Reach out to the NICHY team and join [the Neurobagel discord server](https://discord.gg/sxnCT4QJ7a) for support.
- Share feedback on missing variables with the NICHY team or usability improvements with the Neurobagel team, directly through the tool.
