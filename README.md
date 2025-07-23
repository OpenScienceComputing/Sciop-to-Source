# Sciop-to-Source
Tools for moving data from Sciop (bittorrent) to Source.coop (AWS bucket)

1. Get permission to create repos on Source.coop (I sent a DM to "Jed" on the CNG Slack)
1. Create a repo and get the AWS credentials for the repo

1. Create the Coiled environment to use the ARIA2 CLI and Jupyter Notebooks
   ```
     coiled env create --name sciop-to-source --workspace esip-lab --conda sciop-to-source_env.yml
   ```
1. Start up a notebook on Coiled using this environment with (a) sufficient disk space for the torrent you are accessing, and (b) passing in the AWS Credentials needed to write to Source.coop as environment variables:
   ```
   coiled notebook start --region us-west-2 --vm-type m5.large --software sciop-to-source --name sciop-to-source --workspace esip-lab --env AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID --env AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY --env AWS_REQUEST_CHECKSUM_CALCULATION=WHEN_REQUIRED --disk-size 50GB
   ``` 
1. Copy the Sciop-to-Source.ipynb notebook into the JupyterLab and run it!
