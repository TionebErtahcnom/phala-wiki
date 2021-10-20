---
title: "2.4 Utilisez la console pour gérer votre minage"
---

> Nous vous recommandons fortement de lire [mécanisme de staking]({{< relref "docs/tokenomic/1-mining-staking" >}}) avant d'utiliser la console.

[La Console](https://app.phala.network/mining/)

Les mineurs et les propriétaires de pools peuvent utiliser la Console pour gérer les mineurs et les StakePools. Elle fournit également une vue d'ensemble de l'état de tous les mineurs et StakePools gérés.

## Manuel de la console

### Conditions préalables

1. [Créer un compte Khala]({{< relref "docs/khala-user" >}}) en tant que propriétaire et opérateur de la pool;
2. Obtenez la WorkerPublicKey du mineur et le lié au compte Khala ci-dessus.


### Opérations sur la console

<!-- TODO.zhe: the link in yuque is outdated -->
1. Connectez votre compte Khala ([Vous pouvez suivre cette page pour créer/importer votre compte]({{< relref "docs/khala-user" >}}));
2. Créer un StakePool
    - Cliquez sur « Créer une pool »;
    ![](/images/docs/khala-mining/create-pool.png)
    - Cliquez sur « Confirmer » dans la fenêtre contextuelle;
    - Signez la transaction dans l'extension Polkadot{.js} et attendez environ 20 secondes ;
    - Le pool créé sera répertorié dans Stakepool;
3. (Optionel) Configurer le StakePool
    - Définir la préférence de paiement
        - La préférence de paiement vous permet de définir la commission d'un pool. Le taux de commission détermine combien le propriétaire du pool peut gagner avant que les récompenses minées ne soient distribuées aux jalonneurs. Exemples:
            - S'il est défini sur 0%, toutes les récompenses minées vont aux délégateurs;
            - S'il est défini sur 100 %, toutes les récompenses extraites vont au propriétaire de la pool;
            - S'il est fixé à 50 %, la moitié des récompenses va au propriétaire de la piscine et une autre moitié aux délégateur.
        - Cliquez sur "Set Payout Pref" du pool cible pour définir le taux de commission;
        - Tapez le paiement dans la fenêtre contextuelle; le paiement par défaut est de 0 % (tous donnés aux joueurs), et il peut être défini entre 0 et 100 %;
        - Cliquez sur « Confirmer » pour envoyer la transaction;
        - Le taux de commission sera mis à jour dans la liste StakePool;
    - Définir la capacité de jalonnement
        - La capacité signifie combien le pool accepte de la part des déléguateurs au total. Ceci est utile si vous ne voulez pas qu'un jalonneur aléatoire se jette dans la piscine, ajoutant l'enjeu que vous n'allez pas utiliser mais prenne également une proportion de votre récompense minée
        - Cliquez sur "set Cap" du pool cible;
        - Tapez la capacité de Staking dans la fenêtre pop-up; la capacité par défaut est illimitée et peut être définie entre "le total stacké actuellement" et un nombre illimité;
        - Soumettre la transaction;
        - La valeur de capacité sera mise à jour dans la liste Stakepool;
4. Lier le Worker
    - Cliquez "Add Worker" du pool cible;
    ![](/images/docs/khala-mining/add-worker.png)
    - Tapez la WorkerPublicKey du mineur dans la fenêtre contextuelle;
    - Soumettre la transaction;
    - Le mineur lié sera répertorié;
5. Staking
    - Après avoir créé le StakePool, vous pouvez inviter d'autres Stakers à investir ou à vous investir;
    - Pour misé vous même:
        - Cliquez "Stake" du pool cible;
        - Cliquez "Contribute" dans la fenêtre contextuelle;
        - Tapez le montant à mettre, il doit être inférieur à votre « Solde transférable » et « Pool Cap Gap »;
        - soumettre la transaction;
        - Cliquez sur le boutton "Stake" du pool cible, et vous devriez voir le changement du montant « bloqué » dans « Vos informations de mise »;
6. Lancer le minage (Lorsque votre noeud sera totalement synchronisé)
    - Cliquez sur "Démarrer" du Worker à l'état "Ready";
    - Saisissez le montant de la mise pour le mineur, il doit être supérieur à "Smin" et inférieur à "Smax" et "Pool Free Balance".Notez que vous ne pouvez **PAS** modifier le montant de la mise pendant l'exploitation minière;
    - Soumettre la transaction;
    - L'état Ouvrier doit passer de « Ready » à « Exploitation minière »;
7. Obtenez des récompenses
    - Cliquez sur « Claim » du pool cible;
    - Vous pouvez voir vos récompenses de ce pool, y compris « Récompense du propriétaire » et « Récompense de l'enjeu » ;
    - Choisissez votre compte pour réclamer les récompenses;
    - Soumettre la transaction;
    - Le solde de votre compte doit être augmenté en conséquence ;

### Autres opérations

1. Retirer le Staking
    - Cliquez sur "Stake" du pool cible;
    - Cliquez sur "Withdraw" dans la fenêtre contextuelle;
    - Saisissez le montant à retirer;
    - Soumettre la transaction;
    - Vous pouvez attendre au maximum 14 jours pour obtenir tout votre staking (regarder [ le mécanisme de staking]({{< relref "docs/tokenomic/1-mining-staking" >}})). Vous pouvez vérifier le montant gelé dans la "file d'attente des retraits" de la fenêtre contextuelle "Stake" ;
2. Arrêter l'exploitation minière
    - Cliquez sur "Stop" du mineur en état "Mining" ou "Unresponsive";
    - Soumettez la transaction;
    - L'état du mineur devrait passer à "CoolingDown";
3. Retirer un mineur
    - Cliquez sur "Retirer" du mineur à l'état "Prêt";
    - Soumettez la transaction;
    - Le mineur devrait être retiré de la liste;


### Explications des champs

#### Liste des pools de stacking

1. Vous pouvez cliquer sur "Create Pool" pour créer un nouveau StakePool si la liste est vide;
2. Champs
    - Owner Reward : La récompense du propriétaire du paiement qui peut être réclamée immédiatement;
    - Total Shares : Le montant total de la mise;
    - Free Stake : Le montant de la mise libre;
    - Releasing Stake : Le montant total des enjeux des mineurs du pool en état de "CoolingDown";
3. Bouton "Show this only" : affiche uniquement les mineurs du pool cible;

#### Liste des mineurs

1. Vous pouvez cliquer sur "Add Worker" pour ajouter un nouveau mineur si la liste est vide;
2. Champs
    - Mining Core : Le nombre de cœurs de processeur utilisés;
    - State : Comprend Prêt, Exploitation, Non réactif et Refroidissement (deviendra Prêt après 7 jours);
    - Total Reward : Toutes les récompenses historiques du  miner;


#### Stake Info

1. La file d'attente des retraits répertorie tous les fonds à retirer, classés par heure d'émission. Il est à noter que les demandes de retrait non satisfaites peuvent entraîner l'arrêt de l'exploitation de **TOUS** les mineurs.
    - Staker : Le Staker qui envoie les demandes de retrait.
    - Actions : Les fonds de rappel à retirer.
    - Compte à rebours : S'il y a encore des actions après que le compte à rebours ait atteint 0, tous les mineurs du pool seront forcés à une période de gel de 7 jours.
2. Vos informations de mise
    - Locked : Le montant de votre mise dans ce pool.
    - Actions : Le montant de votre mise en commun en cours d'utilisation.
