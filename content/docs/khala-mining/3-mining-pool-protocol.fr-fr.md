---
titre : "3 la passerelle Runtime de Phala"
draft : true
---


<script>
  MathJax = {
    tex : {
      inlineMath : [['$', '$'], ['\\(', '\\)']],
      displayMath : [['$$','$$'], ['\\[', '\\]']],
      processEscapes : true,
      processEnvironments : true
    },
    options : {
      skipHtmlTags : ['script', 'noscript', 'style', 'textarea', 'pre']
    }
  } ;
  window.addEventListener('load', (event) => {
      document.querySelectorAll("mjx-container").forEach(function(x){
        x.parentElement.classList += 'has-jax'})
    }) ;
</script>
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

Github : https://github.com/Phala-Network/runtime-bridge

## Qu'est-ce que le composant de développement de gestion Phala ?

Phala Management Development Component est un composant de développement open-source destiné à servir les mineurs Phala. Il fournit une interface Cloud Native RPC pour gérer le cycle de vie des workers Phala via Redis. Il peut être utilisé par :
- La pool de minage public, un service tiers qui permet à ses membres de partager leur puissance de traitement et de partager la récompense en fonction de la quantité de travail qu'ils ont contribué ;
- Le cluster de minage, un réseau privé composé de plusieurs travailleurs TEE.

Notez que le composant de développement de gestion Phala est un composant de développement qui peut être personnalisé par les développeurs, et il ne doit pas être utilisé directement par les utilisateurs finaux.


## Exigences matérielles

Contrairement au travailleur normal qui s'exécute dans SGX, le composant de développement de gestion Phala lui-même **** n'a pas besoin de capacités TEE (c'est-à-dire SGX)***. Nous listons le matériel recommandé comme suit.

| Matériel | Exigence |
| :--- : | :--- : |
| Processeur Intel E5/8th Core I7
| Mémoire : 64 G$.
| Stockage | $\geq$ 1TB SSD (NVME PCIE 3.0 * 4) |
| Système d'exploitation : Ubuntu 18.04/20.04 Server.
| Réseau : bande passante LAN : 1 Go.


## Fonctionnalités

Le composant de développement de gestion Phala fournit des fonctionnalités qui incluent :
<!-- TODO.zhe : Je pense que les comptes Worker et Controller ont été abandonnés -->.

<!-- TODO.zhe : nous ferions mieux de donner une licence à ce composant -->


## Support technique

N'hésitez pas à demander de l'aide pendant le développement dans :
- Forum Phala : https://forum.phala.network/t/topic/2379
- Télégramme : https://t.me/phaladeveloper
