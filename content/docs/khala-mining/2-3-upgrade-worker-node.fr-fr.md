---
title: "2.3 Mettre à niveau le nœud du mineur"
---

Pour mettre à niveau votre mineur, il faut d'abord l'arrêter. Notez que vous n'êtes pas obliger d'arrêter le minage sur la blockchain (via Phala App). Cette commande n'arrête que le logiciel et non l'état de la blockchain.

```bash
sudo phala stop
```

Le nœud de travail peut être mis à jour :

```bash
sudo phala update
```

Enfin, redémarrez votre travailleur avec :

```bash
sudo phala start
```

### Mise à jour et effacement des données

Cette commande mettra à jour les images docker ET supprimera toutes les données enregistrées.

{{< tip "warning" >}}
Cette opération est dangereuse car elle supprime l'identité du travailleur, entraînant le changement de la clé publique du travailleur. Lorsque la clé d'identité est perdue, votre mineur ne répondra plus et risque de s'effondrer. Vous devrez arrêter manuellement le mineur d'origine, attendre une période de refroidissement complète, puis retirer votre mise et recommencer. Cette commande supprime également tout l'historique de la blockchain, dont la synchronisation qui prend quelques jours. Si vous ne comprenez pas ce que vous faites, n'exécutez pas une mise à jour avec ce paramètre ('clean').
{{< /tip >}}

```bash
sudo phala update clean
```
