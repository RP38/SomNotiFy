# Fonctionnement

Lorsqu'une alerte se déclenche et que la fonction « SMS par Internet » est activée, la centrale Somfy envoie une requête HTTP GET au service `123-sms.net`. Grâce à une redirection DNS (via dnsmasq), cette requête est interceptée et redirigée vers SomeNotify, qui la retransmet ensuite au backend de notification configuré (Pushover, Free Mobile SMS, etc.).

> **Note** : la fonction « SMS par Internet » n'est disponible que sur les centrales équipées d'un module RTC (transmetteur téléphonique analogique). Ce service avait été conçu pour permettre l'envoi de SMS sur des centrales ne disposant pas de module GSM, le RTC ne permettant pas l'envoi de SMS nativement. Les centrales plus récentes disposant d'un module GSM intégré (ex. : Protexium ~2017) n'exposent pas cette fonction et ne sont donc pas compatibles avec SomeNotify.

## Schéma explicatif

![Schéma explicatif du fonctionnement de SomeNotify](schema_explication.png)

## Format de la requête

```
GET /http.php?email=x&pass=y&numero=z&message=hello
```

| Paramètre | Description                          | Requis |
|-----------|--------------------------------------|--------|
| `message` | Contenu de l'alerte                  | oui    |
| `numero`  | Numéro de téléphone du destinataire  | non    |
| `email`   | Email du compte                     | non    |
| `pass`    | Mot de passe du compte              | non    |
