# Application de relevés sur site – brasseurs d'air

*Brouillon v0 – 3 octobre 2026*

## 1. Objectif

Permettre au technicien / commercial de saisir chez le client, sur téléphone ou tablette, toutes les informations nécessaires à l'étude aéraulique, puis de transmettre un dossier complet et propre à Turbobrise, sans ressaisie ni aller-retour.

## 2. Parcours utilisateur

1. Créer une visite (client, site, date, intervenant).
2. Ajouter une ou plusieurs **zones** à traiter (un bâtiment peut en avoir plusieurs).
3. Pour chaque zone : saisir les dimensions, les obstacles, l'usage, prendre des photos, faire un croquis.
4. Vérifier le récapitulatif (champs obligatoires manquants signalés).
5. Envoyer à Turbobrise (fonctionne même sans réseau : l'envoi part dès que la connexion revient).

## 3. Informations à relever

### Client et site
- Raison sociale, contact, téléphone, e-mail
- Adresse du site, coordonnées GPS (automatiques)
- Type de bâtiment : entrepôt, atelier, bâtiment agricole (élevage), commerce, salle de sport, bureau, ERP…
- Date de la visite, nom de l'intervenant

### Par zone à traiter
**Géométrie**
- Longueur, largeur (m)
- Hauteur sous plafond / sous charpente, hauteur au faîtage et à la sablière si toiture inclinée
- Type de toiture (plate, 1 pan, 2 pans, shed…) et pente
- Forme non rectangulaire : croquis à main levée avec cotes
- Surface et volume calculés automatiquement

**Points d'accroche et contraintes de hauteur**
- Type de structure (charpente métallique, bois, béton, dalle)
- Entraxe des fermes / poutres
- Hauteur libre minimale (ponts roulants, éclairage, sprinklers, gaines, chemins de câbles, racks de stockage) avec leur hauteur

**Obstacles au sol et en hauteur**
- Rayonnages (hauteur, orientation, allées), machines, mezzanines, cloisons

**Ouvertures et ventilation existante**
- Portes, portails, quais, fenêtres, exutoires (dimensions, position)
- Ventilation / chauffage / climatisation existants (type, position)

**Usage et ambiance**
- Activité dans la zone, nombre de personnes, postes fixes ou mobiles
- Objectif : confort d'été, déstratification hiver, bien-être animal, séchage…
- Contraintes : poussières, humidité, ATEX, hygiène alimentaire, bruit
- Température ressentie / problème signalé par le client (optionnel : mesure de température en hauteur et au sol)

**Électricité**
- Alimentation disponible (mono / tri), emplacement du tableau, distance estimée

**Pièces jointes**
- Photos annotées (vue générale, charpente, obstacles, tableau électrique)
- Croquis / plan, éventuellement plan fourni par le client (PDF / image)
- Remarques libres, enregistrement vocal

## 4. Transmission à Turbobrise

Proposition : à l'envoi, l'appli génère **un PDF de synthèse** lisible (avec photos et croquis) **plus un fichier de données structurées** (JSON ou Excel) réutilisable par le bureau d'études, envoyés ensemble par e-mail à une adresse Turbobrise configurable. Une copie est conservée dans l'appli (historique des visites).

À valider avec Turbobrise : le format qu'ils exploitent réellement (un modèle de fiche existante serait idéal).

## 5. Approche technique proposée

- **Application web installable (PWA)** : s'ouvre dans le navigateur du téléphone ou de la tablette, s'installe sur l'écran d'accueil, **fonctionne hors connexion** (sous-sols, bâtiments agricoles sans réseau). Pas de passage par les stores, une seule version iOS + Android + PC.
- Données stockées sur l'appareil, synchronisées / envoyées au retour du réseau.
- Photos via l'appareil photo, croquis au doigt sur l'écran.
- Saisie des mesures facilitée : saisie manuelle au départ ; plus tard, possibilité de connecter un télémètre laser Bluetooth (Bosch, Leica…) si besoin.
- Hébergement simple et peu coûteux ; code dans un dépôt GitHub à créer.

## 6. Hors périmètre de la v1 (à discuter)

- Calcul du nombre / de la position des brasseurs dans l'appli (reste le rôle de l'étude Turbobrise)
- Compte multi-utilisateurs, gestion d'équipe
- Mesure automatique par réalité augmentée (LiDAR)
