---
title : "1.1 Vérifiez votre matériel, votre BIOS et votre système"
---


## Configuration matérielle requise pour Khala

Un système peut potentiellement exploiter Phala s'il répond aux exigences générales suivantes :


![](/images/docs/poc3/1-3.1.png)

Il aura également besoin d'une carte mère et d'un BIOS prenant en charge l'utilisation d'Intel SGX pour exécuter un environnement d'exécution sécurisé (TEE).

## Vérifiez votre processeur

1. Recherchez le **Processeur** de votre ordinateur. Sous Windows, vous pouvez le trouver dans Panneau de configuration/Paramètres, ou cliquez avec le bouton droit sur l'icône Démarrer et sélectionnez Système. Sur Ubuntu, cliquez dans le coin supérieur droit, sélectionnez Paramètres, puis À propos.

    ![](/images/docs/poc3/1-3.2.png)

2. Confirmez que le **CPU prend en charge SGX**

    Ouvrez le site Web d'Intel à l'adresse ark.intel.com et recherchez votre processeur exact ; et confirmez que le processeur prend en charge les extensions Intel Software Guard (Intel SGX).

    ![](/images/docs/poc3/1-3.3.png)
    ![](/images/docs/poc3/1-3.4.png)

    (Cette image montre un processeur qui prend en charge SGX.)

## Vérifiez les paramètres du BIOS

1. Démarrez votre ordinateur dans le BIOS : recherchez sur Internet la bonne méthode pour démarrer le BIOS sur votre ordinateur ou recherchez les instructions à l'écran immédiatement après un démarrage à froid ; cela varie selon le modèle d'ordinateur.
2. **Désactiver le démarrage sécurisé**. Allez dans `Sécurité` -> `Démarrage sécurisé`, réglez-le sur `Désactivé`.
3. **Utilisez le démarrage UEFI**. Allez dans `Boot` -> `Boot Mode` et réglez-le sur `UEFI`.
4. **Activez les extensions SGX**. Allez dans `Sécurité` -> `SGX` (le nom exact peut varier selon le fabricant), réglez-le sur `Activé`.
    >Si vous ne voyez que l'option « SGX : contrôlé par le logiciel », vous devrez exécuter ultérieurement [Intel's sgx-software-enable](https://github.com/intel/sgx-software-enable) dans Ubuntu. Vous pouvez suivre les instructions d'Intel pour le construire à partir de la source et l'exécuter. Nous fournissons également un binaire prédéfini pour Ubuntu 18.04 / 20.04 qui peut être trouvé [ici] (https://github.com/Phala-Network/sgx-tools/releases/tag/0.1). Vous pouvez le télécharger et l'exécuter avec les commandes suivantes :
    > ```bash
    > wget https://github.com/Phala-Network/sgx-tools/releases/download/0.1/sgx_enable
    > chmod +x sgx_enable
    > sudo ./sgx_enable
    > ```
5. Enregistrez et redémarrez.

## Systèmes d'exploitation pris en charge : Ubuntu 18.04 et 20.04

Vous devrez pouvoir démarrer votre ordinateur dans une version prise en charge d'Ubuntu pour la mienne. Les versions supérieures à 18.04 et 20.04 devraient fonctionner, mais ne sont pas garanties.

[Installation d'Ubuntu Desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

### Les références

1. [Qu'est-ce qu'un environnement d'exécution sécurisé (TEE) ?
](https://www.trustonic.com/technical-articles/what-is-a-trusted-execution-environment-tee/)
2. [Qu'est-ce qu'Intel SGX](https://software.intel.com/content/www/us/en/develop/topics/software-guard
