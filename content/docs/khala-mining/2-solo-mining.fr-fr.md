---
titre : "2 Configuration de Solo-Mining"
---


{{< conseil >}}
Si vous avez réussi à installer le pilote SGX et terminé le benchmarking, vous pouvez sauter les tutoriels suivants.
{{< /tip >}}

## Installation

Vous pouvez utiliser les commandes suivantes pour installer les outils Phala. Elle définira automatiquement le nombre de cœurs de CPU à utiliser, le nom du nœud, le mnémonique du compte de frais de gaz et le compte du propriétaire de la pool.

```bash
sudo phala install
```

Par défaut, toutes les configurations sont définies automatiquement. Si vous voulez configurer manuellement les outils, utilisez les commandes suivantes et définissez les paramètres.

{{< conseil "avertissement" >}}
NE PAS partager le même compte de frais de gaz sur plusieurs configurations de minage solo.
{{< /tip >}}

``bash
sudo phala config set
```

> Le script demandera une nouvelle saisie si le paramètre reçu est invalide.
> Pour assurer le déroulement du minage, le solde du compte de frais de gaz doit être supérieur à 0,1 PHA.

Vous pouvez afficher les paramètres de votre configuration avec

``bash
sudo phala config show
```
