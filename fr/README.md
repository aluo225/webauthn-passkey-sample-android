# Exemple d'application IBM Security Verify pour Passkey sur Android

Une implémentation d'Android Passkeys avec IBM Security Verify en tant que service FIDO.

## Mise en route

Les liens de ressources dans les conditions préalables expliquent et démontrent comment créer une nouvelle application locataire et configurer les paramètres de sécurité pour permettre l'utilisation de FIDO dans l'application d'exemple.

### Prérequis

- Mise en route

> Voir [Avant de commencer](https://github.com/ibm-security-verify/webauthn-relying-party-server-swift/blob/main/README.md)

## Mise en route
1. Ouvrez Terminal et clonez le dépôt et ouvrez le dossier du projet dans Android Studio.
   ```
   git clone https://github.com/ibm-security-verify/webauthn-passkey-sample-android.git
   ```

2. Assurez-vous qu'un fichier `assetlinks.json` est présent sur votre domaine dans le répertoire `.well-known`, et qu'il contient un hachage SHA256 de la clé de signature de votre application. Par exemple :
```
{
    "relation": [
      "delegate_permission/common.handle_all_urls",
      "delegate_permission/common.get_login_creds"
    ],
    "target": {
      "namespace": "android_app",
      "package_name": "com.ibm.security.passkeydemo",
      "sha256_cert_fingerprints": [
        "1D:17:1A:FF:B2:01:DC:69:3D:44:D1:68:17:41:57:43:B4:B1:FC:C5:65:F9:0C:C2:B9:F1:AF:5A:E4:87:2F:1F"
      ]
    }
  }
```

3. Mettez à jour le fichier `keystore.properties` avec vos informations de signature.

4. Le hash SHA1 de l'application doit être ajouté en tant que `ogirin` à la configuration du serveur. Cette valeur devrait ressembler à ceci : `android:apk-key-hash:HRca_7IB3Gk9RNFoF0FXQ7Sx_MVl-QzCufGvWuSHLx8`

5. Remplacez la variable **SERVER** dans `Constants.kt` par le nom d'hôte de la partie utilisatrice.


## Ressources
Obtenir le hachage des clés de signature : `./gradlew signingReport`

[Authentification Web du W3C](https://www.w3.org/TR/webauthn-2/)

<!-- v2.3.7 : caits-prod-app-gp_webui_20241231T140326-6_en_fr -->