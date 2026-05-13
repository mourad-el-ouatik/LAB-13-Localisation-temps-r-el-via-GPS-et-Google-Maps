# 📍 LAB-13 | GoogleMapPositions — Affichage des positions GPS sur Google Maps

Une application Android démontrant l’intégration de **Google Maps** avec récupération des positions GPS stockées dans une base MySQL via une API PHP, puis affichage dynamique des marqueurs sur une carte interactive.

---

## ✨ Fonctionnalités

* 🗺️ **Intégration Google Maps** avec `SupportMapFragment`
* 📍 **Affichage des positions GPS** sous forme de marqueurs (`Marker`)
* 🌐 **Récupération des données** depuis une API PHP/MySQL
* 🔄 **Chargement dynamique** des positions via Volley
* 📡 **Connexion HTTP** vers serveur local (`10.0.2.2`)
* 🧭 **Déplacement automatique de la caméra** vers les coordonnées reçues
* 🧩 **Parsing JSON** des positions retournées par le serveur
* 📱 **Gestion des erreurs réseau** et affichage des messages utilisateur

---

## 🛠️ Stack technique

| Composant        | Technologie            |
| ---------------- | ---------------------- |
| Langage          | Java                   |
| UI               | XML Layouts            |
| Architecture     | MVC                    |
| Cartographie     | Google Maps SDK        |
| Requêtes HTTP    | Volley                 |
| Parsing JSON     | JSONArray / JSONObject |
| Serveur back-end | PHP + MySQL            |
| Réseau émulateur | `10.0.2.2`             |

---

## 📁 Architecture du projet

```bash
com.example.googlemappositions
├── MainActivity.java                 # Contrôleur principal — gestion Google Maps
├── Position.java                     # Modèle représentant une position GPS
├── VolleySingleton.java              # Gestionnaire singleton Volley
└── res/
    ├── layout/
    │   └── activity_main.xml         # Vue principale contenant la Map
    ├── values/
    │   └── strings.xml
    └── xml/
        └── network_security_config.xml
```

---

## 📦 Dépendances

```gradle
dependencies {
    implementation 'com.android.volley:volley:1.2.1'
    implementation 'com.google.android.gms:play-services-maps:18.2.0'
    implementation 'com.google.android.gms:play-services-location:21.0.1'
}
```

---

## 🔑 Permissions requises

```xml
<!-- AndroidManifest.xml -->
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
```

---

## 🧠 Concepts Android abordés

* 📌 **Google Maps SDK** avec `SupportMapFragment`
* 📌 **Manipulation de carte** via `GoogleMap`
* 📌 **Ajout de marqueurs** avec `MarkerOptions`
* 📌 **Déplacement caméra** avec `CameraUpdateFactory`
* 📌 **Requêtes HTTP GET/POST** avec Volley
* 📌 **Parsing JSON** avec `JSONObject` et `JSONArray`
* 📌 **Architecture client ↔ serveur** Android / PHP / MySQL
* 📌 **Configuration réseau HTTP** avec `network_security_config.xml`

---

## 🔄 Fonctionnement

1. L’application démarre et initialise `GoogleMap`
2. Une requête HTTP est envoyée au serveur PHP via Volley
3. Le serveur PHP récupère les positions depuis MySQL
4. Les données JSON sont retournées à l’application Android
5. L’application parse le JSON reçu
6. Chaque position est convertie en objet `LatLng`
7. Un `Marker` est ajouté sur la carte pour chaque position
8. La caméra se déplace automatiquement vers les coordonnées affichées

---

## 🔗 Analogie Architecture Android ↔ Web

| Composant Android     | Équivalent Web                      |
| --------------------- | ----------------------------------- |
| `SupportMapFragment`  | `<iframe>` Google Maps / Leaflet.js |
| `GoogleMap`           | Objet `map` JavaScript              |
| `MarkerOptions`       | `L.marker()` dans Leaflet           |
| `Volley`              | `fetch()` / Axios                   |
| `JSONArray`           | Tableau JSON JavaScript             |
| `JSONObject`          | Objet JSON JS                       |
| `LatLng`              | `{lat, lng}` JavaScript             |
| `CameraUpdateFactory` | `map.setView()`                     |

---

## 📱 Interface

* **Écran principal** :

  * Carte Google Maps interactive
  * Affichage des positions GPS sous forme de marqueurs
  * Zoom automatique sur les positions récupérées
  * Messages Toast en cas d’erreur réseau

---

## 🔧 Configuration Google Maps

### 1️⃣ Générer une clé API Google Maps

Créer une clé API depuis :

```text
Google Cloud Console → APIs & Services → Credentials
```

Activer :

```text
Maps SDK for Android
```

---

### 2️⃣ Ajouter la clé dans `AndroidManifest.xml`

```xml
<meta-data
    android:name="com.google.android.geo.API_KEY"
    android:value="VOTRE_CLE_API"/>
```

---

## 🔧 Configuration requise

> Le serveur PHP/MySQL doit être exécuté sur la machine hôte.

Depuis l’émulateur Android :

```text
10.0.2.2 = localhost du PC hôte
```

Exemple d’API :

```text
http://10.0.2.2/localisation/showPosition.php
```

Réponse JSON attendue :

```json
[
  {
    "latitude": "31.6295",
    "longitude": "-7.9811",
    "date_position": "2025-05-13 10:30:00"
  }
]
```

---

## 📱 Demo

https://github.com/user-attachments/assets/c7fce3d0-a3d4-4523-a947-ec7ff2d7e85f

---

## 🎯 Objectif pédagogique

Ce laboratoire permet de comprendre :

* L’intégration de **Google Maps SDK** dans une application Android
* La communication entre Android et un serveur **PHP/MySQL**
* Le chargement et le parsing de données JSON
* L’utilisation de **Volley** pour les requêtes réseau
* L’affichage dynamique de positions GPS sur une carte interactive
* La relation entre données géographiques et visualisation cartographique

---

## 👨‍💻 Auteur

**Mourad EL OUATIK** | Réalisé dans le cadre du **Lab 13 Android** | Programmation & Sécurité des Applications Mobile
