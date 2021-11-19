<img src="https://venidium.io/images/Logo.png" width="100">

# Venidium Docker Container
https://venidium.io/

## Configuration
Required configuration:
* Publish network port via `-p 5744:5744`
* Bind mounting a host plot dir in the container to `/plots`  (e.g. `-v /path/to/hdd/storage/:/plots`)
* Bind mounting a host config dir in the container to `/root/.venidium`  (e.g. `-v /path/to/storage/:/root/.venidium`)
* Bind mounting a host config dir in the container to `/root/.venidium_keys`  (e.g. `-v /path/to/storage/:/root/.venidium_keys`)
* Set initial `venidium keys add` method:
  * Manual input from docker shell via `-e KEYS=type` (recommended)
  * Copy from existing farmer via `-e KEYS=copy` and `-e CA=/path/to/mainnet/config/ssl/ca/` 
  * Add key from mnemonic text file via `-e KEYS=/path/to/mnemonic.txt`
  * Generate new keys (default)

Optional configuration:
* Pass multiple plot directories via PATH-style colon-separated directories (.e.g. `-e plots_dir=/plots/01:/plots/02:/plots/03`)
* Set desired time zone via environment (e.g. `-e TZ=Europe/Berlin`)

On first start with recommended `-e KEYS=type`:
* Open docker shell `docker exec -it <containerid> sh`
* Enter `venidium keys add`
* Paste space-separated mnemonic words
* Restart docker cotainer
* Enter `venidium wallet show`
* Press `S` to skip restore from backup

## Operation
* Open docker shell `docker exec -it <containerid> sh`
* Check synchronization `venidium show -s -c`
* Check farming `venidium farm summary`
* Check balance `venidium wallet show` 
