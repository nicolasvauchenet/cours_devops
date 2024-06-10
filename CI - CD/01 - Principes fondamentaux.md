# Les principes fondamentaux du CI / CD

## Intégration Continue (CI)

### Définition

L'intégration continue est une pratique de développement logiciel où les développeurs intègrent régulièrement leur code
dans un dépôt partagé. Chaque intégration est vérifiée par une build automatique et des tests (unitaires, d'intégration)
pour détecter rapidement les erreurs.

### Objectifs

1. **Détection précoce des bugs :** En intégrant fréquemment, les erreurs sont détectées rapidement.
2. **Réduction des conflits d'intégration :** Les conflits de code sont minimisés car les modifications sont intégrées
   souvent et en petites quantités.
3. **Feedback rapide :** Les développeurs reçoivent des retours rapidement, ce qui permet de corriger les problèmes
   immédiatement.

### Principes

1. **Dépôt de code partagé :** Tous les développeurs travaillent sur un dépôt centralisé.
2. **Build automatique :** Chaque commit déclenche une build automatique.
3. **Tests automatisés :** Les tests sont exécutés automatiquement pour chaque build.

### Outils

GitLab CI, Travis CI, CircleCI

## Déploiement Continu (CD)

Le terme CD peut désigner deux pratiques : Continuous Delivery et Continuous Deployment. Il est essentiel de les
distinguer.

## Continuous Delivery

### Définition

La livraison continue est une pratique où le code est déployé automatiquement dans un environnement de staging après
avoir passé les tests automatisés. Le déploiement en production nécessite une intervention manuelle.

### Objectifs

1. **Livraisons fréquentes et fiables :** Le code est toujours dans un état déployable.
2. **Réduction du risque :** Les déploiements sont petits et fréquents, réduisant le risque d'erreur.
3. **Feedback de l'utilisateur final :** Les fonctionnalités peuvent être validées plus tôt par les utilisateurs.

### Principes

1. **Build, test, déploiement automatisé :** Les builds et tests sont automatisés, et le déploiement sur staging est
   également automatisé.
2. **Intervention humaine pour la production :** Le déploiement en production est une décision manuelle.

### Outils

Jenkins, GitLab CI/CD, Bamboo, Octopus Deploy

## Continuous Deployment

### Définition

Le déploiement continu pousse plus loin la livraison continue en déployant automatiquement chaque changement qui passe
les tests directement en production.

### Objectifs

1. **Déploiement automatique :** Chaque modification validée par les tests automatisés est immédiatement déployée en
   production.
2. **Livraison en continu de la valeur :** Les utilisateurs reçoivent les nouvelles fonctionnalités dès qu'elles sont
   prêtes.

### Principes

1. **Tests rigoureux :** Tous les tests (unitaires, intégration, end-to-end) doivent être extrêmement fiables.
2. **Automatisation complète :** Tout le processus, y compris le déploiement en production, est automatisé.

### Outils

Les mêmes que pour la livraison continue, souvent avec des configurations supplémentaires pour la production.

## Conclusion

Intégration Continue (CI) et Déploiement Continu (CD) sont des pratiques clés pour améliorer la qualité et la rapidité
du développement logiciel. Tandis que l'intégration continue se concentre sur la vérification fréquente du code, la
livraison et le déploiement continus visent à rendre le processus de mise en production aussi fluide et automatisé que
possible.
