---
title : « 1.3 Vérifier la capacité et le niveau de confidentialité de SGX »
---

## Vérifiez le bon fonctionnement de SGX

Après l'installation de votre pilote, veuillez utiliser l'utilitaire suivant pour vérifier si tout se passe bien.

- Vous pouvez exécuter le test SGX par les scripts Phala

  ```bash
  sudo phala sgx-test
  ```

Veuillez faire attention aux vérifications suivantes :

1. SGX system software → Able to launch enclaves → `Production Mode`
2. Flexible launch control → `Able to launch production mode enclave`
3. `isvEnclaveQuoteStatus` and `advisoryIDs` (explained in the next section)

Parmi eux, **le premier est indispensable pour exécuter Phala Network pRuntime**. S'il n'est pas pris en charge (marqué comme ✘ dans l'exemple du rapport ci-dessous), nous craignons que vous ne puissiez pas miner PHALA avec cette configuration. Vous voudrez peut-être remplacer la carte mère et/ou le processeur.

Ces deux derniers ne sont pas obligatoires, bien qu'il soit suggéré de les vérifier car il serait essentiel d'installer le pilote DCAP.

Le rapport ci-dessous serait un résultat positif :

```txt
Detecting SGX, this may take a minute...
✔  SGX instruction set
  ✔  CPU support
  ✔  CPU configuration
  ✔  Enclave attributes
  ✔  Enclave Page Cache
  SGX features
    ✔  SGX2  ✔  EXINFO  ✘  ENCLV  ✘  OVERSUB  ✘  KSS
    Total EPC size: 94.0MiB
✔  Flexible launch control
  ✔  CPU support
  ？ CPU configuration
  ✔  Able to launch production mode enclave
✔  SGX system software
  ✔  SGX kernel device (/dev/sgx/enclave)
  ✔  libsgx_enclave_common
  ✔  AESM service
  ✔  Able to launch enclaves
    ✔  Debug mode
    ✔  Production mode
    ✔  Production mode (Intel whitelisted)

You are all set to start running SGX programs!
Generated machine id:
[162, 154, 220, 15, 163, 137, 184, 233, 251, 203, 145, 36, 214, 55, 32, 54]

Testing RA...
aesm_service[15]: [ADMIN]EPID Provisioning initiated
aesm_service[15]: The Request ID is 09a2bed647d24f909d4a3990f8e28b4a
aesm_service[15]: The Request ID is 8d1aa4104b304e12b7312fce06881260
aesm_service[15]: [ADMIN]EPID Provisioning successful
isvEnclaveQuoteStatus = GROUP_OUT_OF_DATE
platform_info_blob { sgx_epid_group_flags: 4, sgx_tcb_evaluation_flags: 2304, pse_evaluation_flags: 0, latest_equivalent_tcb_psvn: [15, 15, 2, 4, 1, 128, 6, 0, 0, 0, 0, 0, 0, 0, 0, 0, 11, 0], latest_pse_isvsvn: [0, 11], latest_psda_svn: [0, 0, 0, 2], xeid: 0, gid: 2919956480, signature: sgx_ec256_signature_t { gx: [99, 239, 225, 171, 96, 219, 216, 210, 246, 211, 20, 101, 254, 193, 246, 66, 170, 40, 255, 197, 80, 203, 17, 34, 164, 2, 127, 95, 41, 79, 233, 58], gy: [141, 126, 227, 92, 128, 3, 10, 32, 239, 92, 240, 58, 94, 167, 203, 150, 166, 168, 180, 191, 126, 196, 107, 132, 19, 84, 217, 14, 124, 14, 245, 179] } }
advisoryURL = https://security-center.intel.com
advisoryIDs = "INTEL-SA-00219", "INTEL-SA-00289", "INTEL-SA-00320", "INTEL-SA-00329"
confidenceLevel = 5
```

Si vous avez un rapport comme ci-dessous, veuillez le capturer et l'envoyer sur le [serveur Discord de Phala-network](https://discord.gg/zjdJ7d844d) ou [Telegram Miner Group](https://t.me/phalaminer) pour aider.

```txt
Detecting SGX, this may take a minute...
✔  SGX instruction set
  ✔  CPU support // if tagged with ❌: it does not suppoort SGX function, you would need to use other types of CPU.
  ✔  CPU configuration // if tagged with ❌: you would need to check BIOS updates.
  ✔  Enclave attributes // if tagged with ❌: probably caused by [CPU support issue] and [CPU configuration]
  ✔  Enclave Page Cache // if tagged with ❌: probably caused by [CPU support issue] and [CPU configuration]
  SGX features
    ✘  SGX2  ✘  EXINFO  ✘  ENCLV  ✘  OVERSUB  ✘  KSS // It's OK if SGX2 was tagged with ❌. Phala has not integrated with SGX2 technology in the current stage.
    Total EPC size: 94.0MiB
✘  Flexible launch control
  ✔  CPU support
  ✘  CPU configuration // if tagged with ❌: you can give it a try but your miner might be affected when the SGX driver upgrades in the future.
✔  SGX system software
  ✔  SGX kernel device (/dev/isgx)
  ✔  libsgx_enclave_common
  ✔  AESM service
  ✔  Able to launch enclaves
    ✔  Debug mode
    ✘  Production mode // if tagged with ❌: you would need to check BIOS updates.
    ✔  Production mode (Intel whitelisted)

🕮  Flexible launch control > CPU configuration
Your hardware supports Flexible Launch Control, but it's not enabled in the BIOS. Reboot your machine and try to enable FLC in your BIOS. Alternatively, try updating your BIOS to the latest version or contact your BIOS vendor.

debug: MSR 3Ah IA32_FEATURE_CONTROL.SGX_LC = 0

More information: https://edp.fortanix.com/docs/installation/help/#flc-cpu-configuration

🕮  SGX system software > Able to launch enclaves > Production mode
The enclave could not be launched. This might indicate a problem with FLC.

debug: failed to load report enclave
debug: cause: failed to load report enclave
debug: cause: The EINITTOKEN provider didn't provide a token
debug: cause: aesm error code GetLicensetokenError_6
```

Si vous ne pouvez pas exécuter Phala pRuntime avec les deux marqués comme ✔, vous devrez peut-être vérifier si votre BIOS est la dernière version avec les derniers correctifs de sécurité. Si vous ne parvenez toujours pas à exécuter Phala pRuntime docker avec le dernier BIOS du fabricant de votre carte mère, nous craignons que vous ne puissiez pas exploiter PHA pour le moment avec cette carte mère.

## Niveau de confiance d'un mineur

| Niveau | isvEnclaveQuoteStatus | advisoryIDs |
|---|---|---|
| Niveau 1 | D'accord | Aucun |
| Niveau 2 | SW_HARDENING_NEEDED | Aucun |
| Niveau 3 | CONFIGURATION_NEEDED, CONFIGURATION_AND_SW_HARDENING_NEEDED | Liste blanche* |
| Niveau 4 | CONFIGURATION_NEEDED, CONFIGURATION_AND_SW_HARDENING_NEEDED | Certains au-delà de la liste blanche |
| Niveau 5 | GROUP_OUT_OF_DATE | N'importe quelle valeur |

Le niveau de confiance mesure le degré de sécurité de l'environnement d'exécution de SGX Enclave. Il est déterminé par le rapport d'attestation à distance d'Intel. Parmi eux, `isvEnclaveQuoteStatus` indique si la plate-forme est vulnérable à certains problèmes connus, et `advisoryIDs` indique les problèmes réellement affectés.

{{< conseil >}}
Tous les « AdvisoryID » ne sont pas problématiques. Certains avis n'affectent pas l'hypothèse de sécurité de Phala et sont donc sur liste blanche :

- INTEL-SA-00219
- INTEL-SA-00334
- INTEL-SA-00381
- INTEL-SA-00389
{{< /astuce >}}

Les niveaux 1, 2, 3 sont considérés comme ayant le meilleur niveau de sécurité car soit ils ne sont affectés par aucune vulnérabilité connue. Il est bon d'exécuter les applications les plus sensibles sur ces travailleurs, par exemple :

- Applications financières : DEX préservant la confidentialité, DeFi, etc.
- Gestion des clés secrètes : wallet, node KMS, gestionnaire de mots de passe
- Gate-keeper Phala

Les niveaux 4 et 5 sont considérés avec une sécurité réduite, car ces machines nécessitent un correctif de configuration dans le BIOS ou le micrologiciel du BIOS (CONFIGURATION_NEEDED, CONFIGURATION_AND_SW_HARDENING_NEEDED), ou leur microcode ou le micrologiciel du BIOS correspondant sont obsolètes (GROUP_OUT_OF_DATE). Par conséquent, nous ne pouvons pas supposer que la plate-forme est adaptée aux scénarios de sécurité les plus élevés. Cependant, il est toujours bon d'exécuter des tâches de traitement par lots, des applications traitant des données de confidentialité éphémères et des applications blockchain traditionnelles :

- Travaux d'analyse de données (par exemple Web3 Analytics)
- Jeux PvP en chaîne
- VPN
- Applications Web2.0
-Oracle de la blockchain
- DApps

Une fois que Phala sera ouvert aux développeurs pour déployer leurs applications, ils auront la possibilité de choisir les niveaux qu'ils accepteront. Étant donné que les niveaux 1, 2, 3 ont une meilleure sécurité, ils peuvent potentiellement avoir plus de chances de remporter la mission de contrat confidentiel. Cependant, les niveaux 4 et 5 sont utiles dans d'autres cas d'utilisation et peuvent donc être un choix plus économique pour les développeurs.

Si votre mineur est au niveau 4 ou 5, veuillez consulter la page FAQ pour les correctifs potentiels.
