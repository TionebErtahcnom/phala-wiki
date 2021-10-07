---
titre : "1.2 Installer les outils Phala"
---

## Conditions préalables

Avant d'aller plus loin, assurez-vous d'avoir correctement configuré votre matériel, votre BIOS et votre système d'exploitation conformément à la [section précédente]({{< relref "docs/khala-mining/1-1-hardware-requirements">}}) .

## Télécharger les scripts Phala

Les outils Phala sont disponibles sur [https://github.com/Phala-Network/solo-mining-scripts/archive/refs/heads/main.zip](https://github.com/Phala-Network/solo- mining-scripts/archive/refs/heads/main.zip), ils peuvent être téléchargés avec `wget` en exécutant les commandes suivantes dans le terminal :

```bash
sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y
sudo apt install wget unzip
cd ~
wget https://github.com/Phala-Network/solo-mining-scripts/archive/refs/heads/main.zip
unzip main.zip
```
{{< conseil "avertissement" >}}
Si vous utilisez testnet, veuillez vous référer à : [Para2 testnet mining]({{< relref "docs/para-mining" >}})
{{< /astuce >}}

## Activer le logiciel SGX avec sgx_enable
Exécutez les commandes suivantes dans le terminal, l'ordinateur doit redémarrer après l'exécution.

```shell
cd ~/solo-mining-scripts-main
sudo chmod +x sgx_enable
sudo ./sgx_enable
sudo reboot
```

## Installer les outils Phala

Exécutez les commandes suivantes dans votre terminal :

```bash
cd ~/solo-mining-scripts-main
chmod +x install.sh
sudo ./install.sh fr
```
> Ce script installera docker, le pilote sgx et extraira toutes les images des containers docker de Phala.

Félicitations ! Vous avez installé avec succès les outils Phala nécessaires.
