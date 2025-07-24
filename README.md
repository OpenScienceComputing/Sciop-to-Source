# ESIP2025 Demo
* download from Sciop 
* upload to Source.coop 
* visualize

1. Get permission to create repos on Source.coop (I sent a DM to "Jed" on the CNG Slack)
1. Create a repo and get the AWS credentials for the repo
1. Specify the AWS credentials as environment variables
   ``` bash
   export AWS_ACCESS_KEY_ID=xxxxxxxxxxxxxxx
   export AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```
1. Create the Coiled environment to use the ARIA2 CLI and Jupyter Notebooks
   ``` bash
   coiled env create --name esip2025 --workspace esip-lab --conda environment.yml
   ```
1. To start Jupyterlab for downloading and exploring data use this: 
with (a) sufficient disk space for the torrent you are accessing, and (b) passing in the AWS Credentials needed to write to Source.coop as environment variables:
   ``` bash
   coiled notebook start --region us-west-2 --vm-type m5.large --software esip2025 --workspace esip-lab --disk-size 50GB
   ``` 
1. To start Jupyterlab for downloading, exploring data and pushing to Source.coop use this: 
   ``` bash
   coiled notebook start --region us-west-2 --vm-type m5.large --software esip2025 --workspace esip-lab --disk-size 50GB --env AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID --env AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY --env AWS_REQUEST_CHECKSUM_CALCULATION=WHEN_REQUIRED 
   ``` 
1. Open a terminal in Jupyterlab and type:
   ```
   git clone https://github.com/OpenScienceComputing/esip2025.git
   ```
1. Run the notebooks
