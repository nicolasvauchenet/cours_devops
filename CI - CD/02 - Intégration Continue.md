# L'Intégration Continue

## Définition

L'intégration continue (CI) est une pratique de développement où les développeurs intègrent fréquemment leur code dans
un dépôt partagé, avec chaque intégration vérifiée par une build automatisée et des tests.

## Principes

- **Intégration fréquente :** Les développeurs intègrent leur code plusieurs fois par jour.
- **Build automatisé :** Chaque commit déclenche une build et une suite de tests automatisés.
- **Détection rapide des bugs :** Les erreurs sont détectées rapidement, ce qui facilite leur correction.
- **Réduction des conflits :** Les intégrations fréquentes minimisent les conflits de fusion.

## Outils

- **GitLab CI :** Un système CI/CD intégré dans GitLab.
- **Travis CI :** Un service CI hébergé pour les projets open-source et privés.

## Rapports avec Extreme Programming

Extreme Programming (XP) est une méthodologie agile qui valorise la communication, le feedback et l'amélioration
continue. CI est une pratique clé dans XP, car elle encourage l'intégration fréquente de petites modifications,
réduisant ainsi le risque de conflits de code et améliorant la qualité du logiciel.

## Les Tests automatisés

### Tests unitaires :

- **Définition :** Tests qui vérifient le bon fonctionnement des plus petites unités de code (fonctions, méthodes).
- **Exemple :** Tester une fonction de calcul de la somme de deux nombres.

```php
function sum($a, $b) {
    return $a + $b;
}

class SumTest extends \PHPUnit\Framework\TestCase {
    public function testSum() {
        $this->assertEquals(4, sum(2, 2));
    }
}
```

### Tests d'intégration :

- **Définition :** Tests qui vérifient l'interaction entre plusieurs unités ou modules.
- **Exemple :** Tester la communication entre une API et une base de données.

```php
class ApiIntegrationTest extends \PHPUnit\Framework\TestCase {
    public function testApiDatabaseInteraction() {
        $api = new Api();
        $result = $api->fetchDataFromDatabase();
        $this->assertNotEmpty($result);
    }
}
```

### Tests fonctionnels :

- **Définition :** Tests qui vérifient que l'application fonctionne comme prévu du point de vue de l'utilisateur.
- **Exemple :** Tester un formulaire de connexion.

```php
class LoginTest extends \PHPUnit\Framework\TestCase {
    public function testLogin() {
        $client = new Client();
        $crawler = $client->request('GET', '/login');
        $form = $crawler->selectButton('Login')->form();
        $form['username'] = 'user';
        $form['password'] = 'pass';
        $client->submit($form);
        $this->assertTrue($client->getResponse()->isRedirect('/dashboard'));
    }
}
```

## Le Test Driven Development

### Définition

Le Test Driven Development (TDD) est une pratique de développement où les tests sont écrits avant le code. Le processus
se déroule en trois étapes : écrire un test qui échoue, écrire le code pour le faire passer, et refactorer le code.

### Exemple

Développer une fonction de calcul de factorielle.

1. Écrire le test :

```php
class FactorialTest extends \PHPUnit\Framework\TestCase {
    public function testFactorial() {
        $this->assertEquals(120, factorial(5));
    }
}
```

2. Écrire le code :

```php
function factorial($n) {
    if ($n <= 1) {
        return 1;
    }
    return $n * factorial($n - 1);
}
```

3. **Refactoriser :** Optimiser le code si nécessaire.

## Les normes et standards de code

### ES6, StandardJS :

- **ES6 :** Une version de JavaScript qui introduit de nouvelles fonctionnalités telles que les classes, les modules,
  les
  promesses, etc.
- **StandardJS :** Un style guide pour JavaScript qui fournit des règles et des conventions de codage.

### PSR (PHP Standards Recommendations) :

- **PSR-1 :** Normes de base de codage.
- **PSR-2 :** Guide de style pour le formatage du code.
- **PSR-4 :** Autoloading des classes.

## Les linters

### ESLint :

- **Définition :** Un linter pour JavaScript qui analyse le code pour trouver des problèmes de syntaxe, de style, et des
  erreurs potentielles.
- Exemple de configuration :

```json
{
  "env": {
    "browser": true,
    "es6": true
  },
  "extends": "eslint:recommended",
  "parserOptions": {
    "ecmaVersion": 2018,
    "sourceType": "module"
  },
  "rules": {
    "indent": [
      "error",
      2
    ],
    "linebreak-style": [
      "error",
      "unix"
    ],
    "quotes": [
      "error",
      "double"
    ],
    "semi": [
      "error",
      "always"
    ]
  }
}
```

### CodeSniffer, PHPStan :

- **CodeSniffer :** Un outil pour détecter les violations des standards de codage PHP.
- **PHPStan :** Un analyseur statique pour détecter les bugs dans le code PHP sans l'exécuter.

## Intégration Continue avec GitHub et GitLab

### GitHub Actions :

- **Définition :** Une plateforme d'automatisation de workflow CI/CD intégrée dans GitHub.
- **Exemple de workflow :**

```yaml
name: CI

on: [ push, pull_request ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: 7.4
      - name: Install dependencies
        run: composer install
      - name: Run tests
        run: vendor/bin/phpunit
```

### GitLab CI/CD :

- **Définition :** Une fonctionnalité de GitLab pour automatiser le processus de build, test et déploiement.
- **Exemple de configuration :**

```yaml
stages:
  - build
  - test

build:
  stage: build
  script:
    - composer install

test:
  stage: test
  script:
    - vendor/bin/phpunit
```
