# Cache
This repo contains very simple code used to cache data sources related to COVID-19. The main purpose
is to download data that is updated daily and potentially overwritten. In order to ensure
reliability, the logic is kept as simple as possible.

## Installation

Setup a virtual environment in Python and
```python
pip install -r requirements.txt
```

 Make sure you have node.js locally. On Ubuntu18.04 it's done by
 ```powershell
sudo apt-get install nodejs-dev node-gyp libssl1.0-dev
sudo apt-get install npm
 ```

On MacOS 10.14.6 it's done by
 ```
brew install node
npm i puppeteer
npm i yargs
 ```

## Caching of DoH websites
To finally run the caching code,
```python
cd cache
python ./fetch.py --continue-on-error
```

## Data Sources
The list of data sources is maintained in the [`cached_sources.json`](cached_sources.json) file. It
contains a list of records with the following fields:

| Name | Description | Example |
| ---- | ----------- | ------- |
| url | The URL of the resource that should be downloaded / crawled | https://www.cdph.ca.gov/Programs/CID/DCDC/Pages/COVID-19/Race-Ethnicity.aspx |
| cmd | Command that will process the URL and download a cached copy | `static_download` |
| output | Name of the output file which will be written under the current snapshot | US_CA-mortality-stratified.html |
| `option` | Some commands use additional options, which can be defined here | `{screenshot: true}` |


## License
Each data source cached here will retain its original license. The [LICENSE file](../LICENSE) only
applies to the code and data owned and published by this repository.
