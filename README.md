# ViewModelLiveDataDemoEnrichi – Compteur avec ViewModel + LiveData

Application de démonstration des **Android Jetpack Components** (ViewModel et LiveData) pour résoudre le problème classique de la perte de données lors d’une rotation d’écran.

## Fonctionnalités

- Compteur simple (incrémenter, décrémenter, remettre à zéro)
- **Avec ViewModel** : les données survivent à la rotation sans code supplémentaire
- **LiveData** : mise à jour automatique de l’interface, lifecycle‑aware (pas de crash si l’activité est détruite)
- Comparaison avec l’approche classique (sans ViewModel) expliquée dans le README

## Prérequis

- Android Studio
- SDK minimum API 24

## Installation

1. Clonez le dépôt
2. Ouvrez le projet dans Android Studio
3. Laissez Gradle synchroniser les dépendances
4. Lancez l’application sur un émulateur ou un téléphone

## Test du comportement

- Incrémentez le compteur plusieurs fois
- **Tournez l’écran** (Ctrl+F11 sur émulateur) : le compteur reste à sa valeur
- Redémarrez l’application (en la tuant depuis le gestionnaire de tâches) : le compteur est remis à zéro (comportement normal)

## Ce que vous apprendrez

- Pourquoi une variable simple est perdue lors d’une rotation
- Pourquoi `onSaveInstanceState()` est limité (types primitifs, pas d’objets lourds)
- Comment `ViewModel` survit aux changements de configuration
- Comment `LiveData` observe le cycle de vie et évite les fuites mémoire
- La séparation des responsabilités (MVVM)

## Structure du projet

- `CounterViewModel` : logique métier, expose `LiveData<Integer>`
- `MainActivity` : observe le `LiveData` et délègue les actions utilisateur
- `activity_main.xml` : interface minimale

## Points clés (à retenir)

| Concept | Rôle |
|---------|------|
| `ViewModel` | Stocke des données persistantes liées à un cycle de vie (Activity/Fragment) |
| `LiveData` | Observable lifecycle‑aware : notifie les observateurs actifs |
| `MutableLiveData` | Version modifiable de LiveData (privée dans le ViewModel) |
| `ViewModelProvider` | Récupère ou crée le ViewModel associé au LifecycleOwner |
| `setValue()` | Depuis le thread principal |
| `postValue()` | Depuis un thread background (sécurisé) |

