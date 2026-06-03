# Data Sharing for NICHY FreeSurfer 7

## Important things to consider
Once you have completed all the steps, your derived data is ready to be shared with the server in Amsterdam, where it will be accessible to the NICHY core team and project leads (following opt-in). All data will remain on this server. Before transferring, please take the following steps:

- **Review the .tsv and Excel files to confirm completeness**. Verify that all participants are included, there are no missing or unexpected values, and that quality assessment scores have been assigned to each ROI and participant.
- If your site has a preferred data transfer method (different from the one described below), please let us know and we will do our best to accommodate it. Be sure to confirm this with your PI and consult your data transfer agreement beforehand.

## Data to be shared

The following data will be shared with the Amsterdam server as part of this project:

### MRI Outcomes (nipoppy workflow)

FreeSurfer output (5 spreadsheets)

From: `<dataset_root>/derivatives/freesurfer/7.3.2/idp/fs_stats-0.2.1/`

- Surface area: `fs7.3.2-aparc-area.tsv`

- Thickness: `fs7.3.2-aparc-thickness.tsv`

- Curvature: `fs7.3.2-aparc-meancurv.tsv`

- Subcortical volume: `fs7.3.2-aseg-volume.tsv`


From: `<dataset_root>/derivatives/freesurfer_subseg/1.0/idp/fs_subseg_stats-0.2/`

- Subsegmentations: `subsegmentation_volumes.tsv`

Quality control output (2 spreadsheet, optionally .png files)

- Cortical quality assessment scores

- Subcortical quality assessment scores

- Quality control .png files (if authorized)

## Clinical and Demographic Data

Depending on your site's situation, we ask you to share clinical and demographic data using one of the following three options:

### Option 1: Manual entry via Castor (prospective sites or small N)

If your site is just getting started or has a relatively small number of participants, you can enter your data directly into our Castor database. Please send us an email and we will provide you with access and instructions. No data dictionary is needed for this option.

### Option 2: EU-NN data sharing

If your site is part of the EU-NN, we can request the relevant data directly from the EU-NN on your behalf, with your permission. Please reach out to the NICHY core team to arrange this. For this option, we ask you to create a data dictionary using [Neurobagel](https://enigma-infra.github.io/ENIGMA-PD/resources/how_to_guides/neurobagel/).

### Option 3: Sharing an existing spreadsheet

If your site already has a spreadsheet containing the clinical and demographic variables for all participants, you can share this directly. Please make sure the file is in a machine-readable format: a single CSV or TSV file is preferred, with all variables as columns and all participants as rows. Avoid Excel files with multiple tabs, merged cells, or comments. For this option, we ask you to create a data dictionary using [Neurobagel](https://enigma-infra.github.io/ENIGMA-PD/resources/how_to_guides/neurobagel/). 

## Data sharing protocol

### Sending data using SURFfilesender
We provide the possibility to send the data securely and encrypted using [SURFfilesender](https://www.surf.nl/en/services/storage-data-management/surffilesender). 

#### Option 1: Upload files via browser
For this, you can use the personal invitation link that you will receive by email. This email has been sent from **SURFfilesender <noreply@surf.nl\>** on behalf of our team, so please check your spam or junk folder if you do not see it in your inbox. The email will contain a voucher link and will look something like this:
>*"Please find below a voucher which grants access to SURFfilesender. You can use this voucher to upload one set of files and make it available for download."*

The voucher link will be valid for 60 days, so please use it in time. If you did not receive the email, cannot find it, or need a new link, please reach out to the NICHY core team.

#### Option 2: Upload files via the command line

This option is available if you have a SURF account (available to all Dutch educational institutions) or an eduID (a guest account for SURF services). If you do not have either, you can request an eduID at [eduid.nl](eduid.nl). Full instructions for setting up and using the SURF CLI client can be found [here](https://servicedesk.surf.nl/wiki/spaces/WIKI/pages/198967770/SURFfilesender+CLI+client). In short, the process involves downloading the Python CLI client from your SURFfilesender profile page, installing a few standard Python dependencies (which are present on most systems), configuring the client with your username and API key from the same profile page, and then running the client with the recipient address and file path to upload your data.
