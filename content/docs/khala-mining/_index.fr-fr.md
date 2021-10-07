---
title: "Guide minage Khala Pre-mainnet"
weight: 6
draft: false
---

Khala Network est le réseau canari de Phala sur la Parachain Kusama avec une minage TEE décentralisée. Nous fournissons un aperçu de la configuration de l'environnement de minage, suivi d'une explication détaillée de chaque étape.

Nous recommandons fortement aux mineurs de lire d'abord sur la [tokenomic]({{< relref "docs/tokenomic" >}}) et le [mécanisme du stacking]({{< relref "docs/tokenomic/1-mining-staking" >}} de Phala ) pour comprendre le calcul des rewards et le déroulement du minage.

Si vous avez des questions, vous pouvez toujours demander de l'aide : 
- Télégramme : https://t.me/phalaminer
               https://t.me/phalaminer       
- Discord : https://discord.gg/DWdHXFm8 
- Forum : https://forum.phala.network

Voici quelques notes dont Khala a besoin. 

- Khala Polkadot.js UI: [Link](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fkhala.api.onfinality.io%2Fpublic-ws#/explorer) 
- 2 comptes Khala : [Link](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fkhala.api.onfinality.io%2Fpublic-ws#/accounts) 
- Khala RPC Endpoint : `wss : //khala.api.onfinality.io/public-ws` 
- L'Explorateur de blockchain Khala : <https://khala.subscan.io/> 
- L'application Khala：<https://app.phala.network/> 
- Console Khala : <https://app.phala.network/mining/> 

### I. Demarrage 

- [1.1 Vérifiez votre matériel, votre BIOS et votre système]({{< relref "docs/khala-mining/1-1-hardware-requirements" >}})
- [1.2 Installez les outils Phala]({{< relref "docs/khala-mining/1-2-download-setup-scripts" >}})
- [1.3 Vérifier la compatibilité SGX et le niveau de confidentialité ]({{< relref "1-3-confidential-level-evaluation" >}})
- [1.4 Benchmarking]({{< relref "docs/khala-mining/1-4-benchmarking" >}})

### II. Déploiement du réseau Khala

- [2.1 Configuration]({{< relref "docs/khala-mining/2-solo-mining" >}})
- [2.2 Déploiement d'un noeud Worker]({{< relref "docs/khala-mining/2-1-deploy-worker-node" >}})
- [2.3 Vérifier l'état du worker]({{< relref "docs/khala-mining/2-2-verify-worker-status" >}})
- [2.4 Mise à jour du Worker]({{< relref "docs/khala-mining/2-3-upgrade-worker-node" >}})
- [2.5 Utilisez la console pour manager votre minage]({{< relref "docs/khala-mining/2-4-console" >}})

### III. FAQ

- [Questions fréquemment posées]({{< relref "docs/khala-mining/4-faq" >}})
- [Comment obtenir une meilleure connectivité entre pairs]({{< relref "docs/khala-mining/4-1-How-to-get-better-peers-connectivity" >}})
- [Comment synchroniser rapidement votre nœud si vous n'avez pas encore complètement synchronisé]({{< relref "docs/khala-mining/4-2-How-to-fast-sync-node-use-snapshot" >}})
