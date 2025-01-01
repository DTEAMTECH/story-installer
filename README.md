# Story installer  

This is a simple command line tool to spin up Story protocol node. It is designed to be simple and easy to use. 

python 3.8 or python3.10 or python3.11 is required to run this tool. 

## Installation

To install simply download the latest release from the [releases page]()

You can use command for download
```bash
wget <release_url>
chmod +x story-installer  
```

## Usage

Install with default settings 

```bash
story-installer   install
```
## Example of usage 

You can override any setting from `story-installer show` output by passing `-e` flag with `key=value` pairs. 

For example, let's check the settings for story_testnet

```bash
story-installer show 
```

```json
{
"moniker": "validator",
"consensus_install_from": "none",
"geth_install_from": "none",
"chain_id": "odyssey",
"netname": "story_testnet",
"go_version": "go1.21.11",
"base_folder": ".story",
"binary_conensus": "story",
"binary_geth": "geth",
"version_consensus": "v0.13.0",
"version_geth": "v0.11.0",
"repo_consensus": "https://github.com/piplabs/story.git",
"repo_geth": "https://github.com/piplabs/story-geth.git",
"geth_binary_url": "https://github.com/piplabs/story-geth/releases/download/v0.11.0/geth-linux-amd64",
"story_binary_url": "https://github.com/piplabs/story/releases/download/v0.13.0/story-linux-amd64",
...etc
```
Any of these settings can be overridden with `-e` flag. 

Here is few examples of usage:

1. Install from snapshot

```bash
# Check modified settings 
story-installer show -e "geth_install_from=snapshot;consensus_install_from=snapshot"
# Run `story-installer` to Install story_testnet from state_sync
story-installer install -e "geth_install_from=snapshot;consensus_install_from=snapshot"
# Run `story-installer` to install from archive snapshot
story-installer install -e "geth_install_from=archive;consensus_install_from=archive"
```

2. Install with custom port prefix 

```bash
story-installer install story_testnet -e "custom_port_prefix=137;"
```
This command will install with custom port prefix 137 

RPC port will be 13757, P2P port will be 13756, GRPC port will be 13790, REST port will be 13717; instead of default 26657, 26656, 9090, 1317


## Install story-installer from source

1. Clone the repository

2. Create venv and install dependencies

```bash
python3 -m venv venv
source venv/bin/activate
pip install .
```
3. Run story-installer

```bash
python story-installer.py install
```



