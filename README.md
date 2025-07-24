# ESIP2025 Demo
* download from Sciop 
* upload to Source.coop 
* visualize

1. Install Coiled
   [Install conda](https://conda-forge.org/download/) if not already installed
   ``` bash
   conda create -n coiled coiled -y
   conda activate coiled
   ```
1. Set a TOKEN that give you access to the ESIP-LAB Coiled account (for today only) 
   ```
   export DASK_COILED__TOKEN=0d98de5376c148cfa1a42506cabb91b4-b680b641f13363e926760686e736175e59ecf1d5
   ```
   or
   ```
   set DASK_COILED__TOKEN=0d98de5376c148cfa1a42506cabb91b4-b680b641f13363e926760686e736175e59ecf1d5
   ```
   or 
   ```
   coiled login --token 0d98de5376c148cfa1a42506cabb91b4-b680b641f13363e926760686e736175e59ecf1d5
   ```
1. To start Jupyterlab for downloading and exploring data use this: 
   ``` bash
   coiled notebook start --region us-west-2 --vm-type m5.large --software esip2025 --workspace esip-lab --disk-size 50GB
   ``` 
1. Open a terminal in Jupyterlab and type:
   ```
   git clone https://github.com/OpenScienceComputing/esip2025.git
   ```
1. Run the notebooks


## Creating your own repos on Source
1. Request permission to create repos on Source.coop 
1. Create a repo and get the AWS credentials for the repo
1. Specify the AWS credentials as environment variables
   ``` bash
   export AWS_ACCESS_KEY_ID=xxxxxxxxxxxxxxx
   export AWS_SECRET_ACCESS_KEY=xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
   ```
1. Start Jupyterlab for downloading, exploring data and pushing to Source.coop:
   ``` bash
   coiled notebook start --region us-west-2 --vm-type m5.large --software esip2025 --workspace esip-lab --disk-size 50GB --env AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID --env AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY --env AWS_REQUEST_CHECKSUM_CALCULATION=WHEN_REQUIRED 
   ``` 
## Creating the Coiled software environment
   ``` bash
   coiled env create --name esip2025 --workspace esip-lab --conda environment.yml
   ```
