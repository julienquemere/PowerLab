# Xl2Collection Tool

Générateur de formules Power FX pour importer des données Excel dans des collections Power Apps.

## Fonctionnalités

- ✅ **Détection automatique des types** (Text, Value, DateValue, DateTimeValue)
- 🔄 **Mode Unpivot** : transforme des colonnes en lignes
- 📋 **Copier-coller** depuis Excel directement
- ⚡ **Formules optimisées** prêtes à l'emploi

## Utilisation

1. **Copiez** vos données Excel (incluant le header)
2. **Cliquez** sur "Importer Excel" et collez (`Ctrl+V`)
3. **Configurez** les colonnes (type, sélection, unpivot)
4. **Copiez** la formule générée
5. **Collez** dans l'événement `OnSelect` de votre bouton Power Apps

## Installation

Téléchargez `Xl2Collection.html` et ouvrez-le dans votre navigateur. C'est tout !

- Aucune dépendance
- Fonctionne 100% offline
- Fichier HTML unique

## Exemple Unpivot

**Avant :**
```
Produit    Jan    Fév    Mars
Pommes     100    120    150
```

**Après (unpivot Jan, Fév, Mars) :**
```
Produit    Attribut    Valeur
Pommes     Jan         100
Pommes     Fév         120
Pommes     Mars        150
```
