---
titre : "4.1 Comment obtenir une meilleure connectivité entre pairs"
---

## Le problème

Certains de nos amis qui utilisent nos nœuds peuvent constater que leurs nœuds ont du mal à se connecter à un pair, ce qui entraîne l'exclusion de nœuds de tout le réseau. Dans cette KB, vous trouverez pourquoi et ce qu'il faut faire.

## Pare-feu dynamique

Comme IPv4 est épuisant, il y a aussi des problèmes de sécurité ou des considérations de conception. Il y a beaucoup de pare-feu stateful entre vous et vos pairs qui exécutent le NAT, le filtre pour motif politique, ou les deux. Cela augmente considérablement la complexité de la connectivité et cause des tonnes de problèmes.

### Que font ces pare-feux dynamiques ?

#### NAT de source

La NAT de source est utilisée pour permettre à un grand nombre de périphériques d'utiliser la même adresse publique routable en traçant la connexion que votre hôte ouvre à l'Internet à l'extérieur du pare-feu. Tout datagramme envoyé à l'extérieur du pare-feu voit son adresse source modifiée en une adresse retenue par le pare-feu. Lorsque l'hôte distant répond à votre datagramme dont la destination est le pare-feu, ce dernier sait quelle est la véritable cible et l'envoie simplement.

Mais s'il y a des hôtes distants à l'extérieur du pare-feu qui veulent établir une nouvelle connexion avec un hôte derrière le pare-feu, il n'y a aucun moyen. Lorsque le datagramme atteint le pare-feu, celui-ci vérifie sa table de connexion et, dans la plupart des cas, il ne trouve rien, si bien que le datagramme est abandonné.

Le pare-feu peut tracer la connexion en utilisant différentes informations et cela provoquera des résultats différents, vous pouvez vérifier <https://fr.wikipedia.org/wiki/Network_address_translation#Methods_of_translation> pour l'idée.

Veuillez noter que le NAT source peut être exécuté à la fois par vous et par votre fournisseur de réseau. et vous pouvez être derrière plusieurs couches de NAT source.

#### Filtre basé sur les politiques

Certains fournisseurs de réseau et d'hébergement peuvent appliquer un filtre basé sur une politique qui supprime tous les datagrammes envoyés depuis ou vers vous pour des raisons de sécurité ou de prévention des abus, car les connexions P2P sont souvent utilisées pour la distribution de contenu illégal. Cela peut interrompre certaines de vos connexions entre pairs.

## Ce qu'il faut faire

### Débarrassez-vous du NAT ou du filtre.

La première chose à faire est de vérifier que votre fournisseur de réseau n'exécute pas de NAT à la source ou de filtres basés sur des règles pour vous. Si c'est le cas, essayez de lui demander de ne pas les appliquer pour vous.

### Configurez votre propre appareil pour obtenir une meilleure connectivité

Si vous devez configurer vous-même la NAT de source, vous pouvez toujours faire quelque chose pour obtenir une meilleure connectivité de votre nœud.

#### NAT de destination, DMZ ou UPnP

Vous pouvez configurer le NAT de destination pour exposer les ports que vos nœuds écoutent. Certains périphériques réseau conçus pour un usage domestique peuvent vous permettre de configurer un hôte DMZ qui recevra tous les datagrammes entrants qui ne sont connus d'aucune connexion.

Certains périphériques réseau conçus pour un usage domestique peuvent également être en mesure d'écouter UPnP, ce qui peut faciliter la configuration de la destination nat. Mais l'utilisation d'UPnP est souvent problématique et non sûre. L'UPnP ne doit donc être considéré qu'en dernier recours.
