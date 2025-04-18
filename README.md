## Nettoyage des data

Pandas uniquement

## Normalisation du jeu de donnée

## Jeu de Données contenant uniquement les 3 caractéristique

## Utiliser matpotlib pour afficher les étoiles

## Choix de l'estimateur sckit-learn le plus adapté

## Entrainement du modèle

## affichage des différent groupes dans le graphiques avec matplotlib




Voici précisément les détails sur le modèle utilisé et comment il est entraîné dans ton cas :

## 📌 Modèle choisi :

### **KMeans**
- **Type de modèle :** Algorithme de clustering (apprentissage non supervisé)
- **Bibliothèque :** `scikit-learn`

## 📌 Paramètres utilisés :
```python
KMeans(n_clusters=4, random_state=42)
```

- **n_clusters=4 :** Le nombre de groupes souhaité est fixé à **4**.
- **random_state=42 :** Pour assurer la reproductibilité des résultats.

## 📌 Comment le modèle est entraîné :

1. **Préparation des données :**
   - Chargement et nettoyage des données.
   - Sélection des colonnes utiles (`Mass`, `Distance`, `Radius`).
   - Nettoyage des valeurs non-numériques et suppression des lignes avec des valeurs manquantes.

2. **Normalisation des données :**
   - Utilisation de `MinMaxScaler` pour normaliser toutes les valeurs entre 0 et 1 :
   ```python
   scaler = MinMaxScaler()
   df_normalized = scaler.fit_transform(df_clean)
   ```

3. **Entraînement du modèle KMeans :**
   - Entraînement sur les données normalisées :
   ```python
   kmeans = KMeans(n_clusters=4, random_state=42)
   kmeans.fit(df_normalized)
   ```

   - Le modèle recherche automatiquement 4 centres de gravité (centroïdes) dans les données pour former 4 groupes distincts.

4. **Attribution des clusters :**
   - Affectation des clusters aux données d'origine :
   ```python
   df_clean['Cluster'] = kmeans.predict(df_normalized)
   ```

## 📌 Pourquoi ce modèle ?
- **KMeans** est efficace pour regrouper des données lorsqu'on ne dispose pas d’étiquettes préalables.
- Il est particulièrement adapté ici, car l'objectif était précisément de découvrir des groupes sans connaître préalablement les caractéristiques de regroupement.

---

**Souhaites-tu des précisions complémentaires sur le modèle ou les étapes d'entraînement ?**