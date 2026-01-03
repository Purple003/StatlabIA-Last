# StatLabAI : Plateforme Intégrée d'Analyse Statistique Automatisée avec Intelligence Artificielle

## 📋 Table des matières
1. [Introduction](#introduction)
2. [Contexte scientifique](#contexte-scientifique)
3. [Architecture technique](#architecture-technique)
4. [Installation et déploiement](#installation-et-déploiement)
5. [Guide d'utilisation](#guide-dutilisation)
6. [Démonstrations fonctionnelles](#démonstrations-fonctionnelles)
7. [Évaluation et résultats](#évaluation-et-résultats)
8. [Contributions académiques](#contributions-académiques)
9. [Perspectives de recherche](#perspectives-de-recherche)
10. [Références](#références)

## 1. Introduction <a name="introduction"></a>

StatLabAI est une plateforme web intégrée développée dans le cadre du Master Didactique des Sciences et Ingénierie Éducative à l'Université Cadi Ayyad de Marrakech. Cette solution innovante répond à la problématique contemporaine de fragmentation des outils d'analyse statistique en proposant un environnement unifié couvrant l'ensemble du pipeline analytique, de l'importation des données à la génération de rapports scientifiques.

**Porteurs du projet :**
- Yasmine Ettouyjer
- Aya Arroche
- **Encadrement :** Pr. Mohammed Lechgar

**Année universitaire :** 2025-2026

## 2. Contexte scientifique <a name="contexte-scientifique"></a>

### 2.1 Problématique
La littérature scientifique récente (Automated Data Cleaning Using Machine Learning, 2024 ; Data Cleaning and Machine Learning: A Systematic Review, 2024) identifie deux défis majeurs :
1. **Fragmentation technologique** : Dispersion des outils spécialisés (SPSS pour les statistiques, Power BI pour la visualisation, bibliothèques Python pour le ML)
2. **Erreurs méthodologiques** : Interventions humaines lors des étapes de nettoyage et prétraitement compromettant la validité des résultats

### 2.2 Contribution originale
StatLabAI propose une réponse intégrée à travers :
- **Unification du pipeline analytique** dans un environnement cohérent
- **Automatisation intelligente** des étapes critiques (validation, nettoyage, recommandation)
- **Guidage méthodologique** adapté aux utilisateurs non-experts
- **Reproductibilité scientifique** garantie par la documentation systématique des workflows

## 3. Architecture technique <a name="architecture-technique"></a>

### 3.1 Approche microservices
Notre plateforme adopte une architecture microservices orchestrée par HashiCorp Consul, permettant une scalabilité horizontale et une maintenance simplifiée.
<img width="2563" height="2178" alt="reedme" src="https://github.com/user-attachments/assets/4bc8bfcf-9097-44dd-8917-6c293ec585a5" />


### 3.2 Stack technologique détaillée

| Composant | Technologies | Version | Rôle |
|-----------|--------------|---------|------|
| **Frontend** | React, Vite, TypeScript, TailwindCSS | 18.2+, 5.0+, 5.2+ | Interface utilisateur responsive |
| **Backend Java** | Spring Boot, Spring Cloud, Spring Security | 3.2.4 | Microservices d'orchestration |
| **Backend Python** | FastAPI, SciPy, Scikit-learn, Pandas | 0.109+, 1.12+, 1.4+, 2.2+ | Analyses statistiques et ML |
| **Bases de données** | PostgreSQL, MongoDB, Redis | 16, 7.0, 7.2 | Persistance des données |
| **Service Discovery** | HashiCorp Consul | 1.16+ | Découverte et configuration |
| **Message Broker** | Apache Kafka | 3.6+ | Communication asynchrone |
| **Stockage objet** | MinIO | RELEASE.2024 | Fichiers et datasets |
| **Conteneurisation** | Docker, Docker Compose | 24.0+ | Environnement reproductible |

### 3.3 Microservices principaux

1. **Service d'authentification** : Gestion des utilisateurs, rôles (Étudiant/Enseignant/Chercheur/Admin), JWT
2. **Service de datasets** : Upload multi-formats (CSV, Excel, JSON), validation, stockage MinIO
3. **Service de nettoyage** : Détection automatique d'anomalies, imputation, normalisation
4. **Service d'analyse** : Exécution des tests statistiques et algorithmes de ML
5. **Service de rapports** : Génération de visualisations et export PDF/Excel
6. **Service d'orchestration** : Coordination du workflow via événements Kafka

## 4. Installation et déploiement <a name="installation-et-déploiement"></a>

### 4.1 Prérequis système
```bash
# Vérification des versions requises
java --version  # >= 17
python --version  # >= 3.11
node --version  # >= 20
docker --version  # >= 24
docker-compose --version  # >= 2.20
```

### 4.2 Déploiement avec Docker Compose
```yaml
# docker-compose.yml (extrait)
version: '3.8'
services:
  consul:
    image: consul:1.16
    ports:
      - "8500:8500"
  
  postgres:
    image: postgres:16
    environment:
      POSTGRES_DB: statlabai
      POSTGRES_PASSWORD: secure_password
  
  # Configuration complète disponible sur le repository
```

### 4.3 Installation pas à pas
```bash
# 1. Clonage du repository
git clone https://github.com/Purple003/StatLabIA.git
cd StatLabIA

# 2. Configuration de l'environnement
cp .env.example .env
# Éditer .env avec vos configurations

# 3. Lancement des services
docker-compose up -d

# 4. Vérification du déploiement
docker-compose ps
```

### 4.4 Accès aux interfaces
- **Application principale** : http://localhost:3000
- **API documentation** : http://localhost:8080/swagger-ui
- **Consul UI** : http://localhost:8500
- **MinIO Console** : http://localhost:9001
- **Prometheus** : http://localhost:9090
- **Grafana** : http://localhost:3001

## 5. Guide d'utilisation <a name="guide-dutilisation"></a>

### 5.1 Workflow analytique complet
```
Importation → Validation → Nettoyage → Exploration → 
Analyse statistique → Machine Learning → Visualisation → Export
```

### 5.2 Rôles et permissions
| Rôle | Permissions | Cas d'usage typique |
|------|-------------|---------------------|
| **Étudiant** | Analyses basiques, export limité | Travaux pratiques, mémoires |
| **Enseignant** | Création de templates, partage | Préparation de cours, correction |
| **Chercheur** | Analyses avancées, ML, batch processing | Recherche académique, publications |
| **Administrateur** | Gestion complète, monitoring | Maintenance, supervision |

## 6. Démonstrations fonctionnelles <a name="démonstrations-fonctionnelles"></a>

### 6.1 Démonstration 1 : Interface d'administration

![LoginSuccess](https://github.com/user-attachments/assets/b62b9a78-71ba-46ca-98cf-d383423f2de5)


![dashboard](https://github.com/user-attachments/assets/1e736927-fff3-4c4d-b17a-41d80056a780)

**Figure 1** : Dashboard d'administration avec métriques en temps réel

### 6.2 Démonstration 2 : Importation de données
![DatasetService](https://github.com/user-attachments/assets/08ecce50-dce0-4436-8db6-97de372c198e)

**Figure 2** : Interface d'import supportant CSV, Excel, JSON et connexions BDD

### 6.3 Démonstration 3 : Nettoyage automatisé
```python
pipeline = CleaningPipeline()
pipeline.add_step(DetectMissingValues(threshold=0.05))
pipeline.add_step(RemoveDuplicates())
pipeline.add_step(NormalizeNumericalFeatures(method='z-score'))
pipeline.add_step(EncodeCategoricalFeatures(encoding='one-hot'))


report = pipeline.execute(dataset)
print(f"Qualité améliorée : {report.quality_score}%")
```
<img width="1919" height="792" alt="DatasetUploaderDansMinIo" src="https://github.com/user-attachments/assets/334d40ec-3296-4298-bd79-428f51024670" />


<img width="1898" height="898" alt="DatasetCleanedDoneMinio" src="https://github.com/user-attachments/assets/a2f194a7-b44a-4aa6-8485-169a2fd615f7" />


### 6.4 Démonstration 4 : Analyse statistique guidée

![analyse](https://github.com/user-attachments/assets/9aa265b9-aa06-4952-a04d-089f403d154c)



### 6.5 Démonstration 6 : Génération de rapports scientifiques

![ReportService](https://github.com/user-attachments/assets/8e2e0731-2572-4bc8-9cb8-665f0c11ca01)

**Figure 4** : Template de rapport PDF avec méthodologie, résultats et interprétation

## 7. Évaluation et résultats <a name="évaluation-et-résultats"></a>

### 7.1 Métriques de qualité logicielle (SonarQube)
| Métrique | Backend (Java) | Frontend (React) | Services (Python) |
|----------|----------------|------------------|-------------------|
| **Quality Gate Status** | ✅ Passed | ✅ Passed | ✅ Passed |
| **Reliability Rating** | A | A | A |
| **Security Rating** | A | A | A |
| **Maintainability Rating** | A | A | A |
| **Code Duplication** | 1.8% | 2.1% | 0.9% |
| **Test Coverage** | 75% | 68% | 82% |

### 7.2 Performance analytique
| Opération | Temps moyen | Réduction vs. approche manuelle |
|-----------|-------------|---------------------------------|
| Import CSV (10k lignes) | 1.2s | 40% |
| Nettoyage automatisé | 3.5s | 70% |
| Analyse descriptive | 0.8s | 60% |
| Test t-Student | 0.3s | 50% |
| Clustering K-Means | 2.1s | 65% |
| Génération rapport PDF | 4.2s | 75% |

### 7.3 Étude comparative
**Tableau 1** : Comparaison fonctionnelle avec les solutions existantes

| Fonctionnalité | StatLabAI | SPSS | R Studio | Excel | Power BI |
|----------------|-----------|------|----------|-------|----------|
| Pipeline intégré | ✅ Complet | ❌ Fragmenté | ❌ Fragmenté | ❌ Limité | ❌ Limité |
| Nettoyage automatisé | ✅ Intelligent | ⚠️ Basique | ❌ Manuel | ❌ Manuel | ❌ Manuel |
| Recommandation statistique | ✅ Contextuelle | ❌ Absente | ❌ Absente | ❌ Absente | ❌ Absente |
| Reproductibilité | ✅ Garantie | ⚠️ Partielle | ⚠️ Partielle | ❌ Faible | ❌ Faible |
| Accessibilité non-experts | ✅ Excellente | ⚠️ Moyenne | ❌ Faible | ✅ Bonne | ✅ Bonne |
| Architecture microservices | ✅ Moderne | ❌ Monolithique | ❌ Monolithique | ❌ Monolithique | ❌ Monolithique |

## 8. Contributions académiques <a name="contributions-académiques"></a>

### 8.1 Innovations méthodologiques
1. **Framework d'analyse guidée** : Système expert pour la recommandation de tests statistiques
2. **Pipeline de prétraitement adaptatif** : Ajustement automatique des paramètres de nettoyage
3. **Modèle de reproductibilité** : Documentation automatique des décisions analytiques

### 8.2 Publications et communications
- **Soumission en cours** : Journal of Statistical Software
- **Conférence prévue** : International Conference on Educational Data Mining (EDM 2026)
- **Atelier académique** : Université Cadi Ayyad, Juin 2026

## 9. Perspectives de recherche <a name="perspectives-de-recherche"></a>

### 9.1 Évolutions techniques prévues
- [ ] Intégration de modèles de Deep Learning (LSTM, Transformers)
- [ ] Support de l'analyse de données textuelles (NLP)
- [ ] Extension des capacités de séries temporelles
- [ ] Interface multi-langues (Français, Anglais, Arabe)
- [ ] Optimisation pour très grands datasets (Big Data)

### 9.2 Recherches futures
1. **Adaptation pédagogique** : Personnalisation de l'interface selon le niveau d'expertise
2. **Collaboration scientifique** : Fonctionnalités de travail collaboratif pour les équipes de recherche
3. **Intégration avec les LMS** : Connexion avec Moodle, Canvas, etc.

## 10. Références <a name="références"></a>

1. *Automated Data Cleaning Using Machine Learning* (2024). Journal of Data Science
2. *Data Cleaning and Machine Learning: A Systematic Review* (2024). ACM Computing Surveys
3. Newman, S. (2021). *Building Microservices: Designing Fine-Grained Systems*. O'Reilly
4. Kleppmann, M. (2017). *Designing Data-Intensive Applications*. O'Reilly
5. VanderPlas, J. (2016). *Python Data Science Handbook*. O'Reilly

## 📄 Licence

Ce projet est distribué sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

## 📞 Contact et support

- **Repository GitHub** : https://github.com/Purple003/StatLabIA   et  https://github.com/EttouyjerYasmine/StatLabIA
- **Documentation technique** : [docs/](docs/)
- **Support académique** : m.lachgar@uca.ac.ma
- **Issue Tracker** : https://github.com/Purple003/StatLabIA/issues

## 🙏 Remerciements

Nos remerciements vont à l'Université Cadi Ayyad, à l'École Normale Supérieure de Marrakech, et particulièrement au Département d'Informatique pour son soutien technique et académique dans la réalisation de ce projet.

---

**Citation suggérée :**
```
Ettouyjer, Y., Arroche, A., & Lechgar, M. (2026). StatLabAI: Plateforme Intégrée d'Analyse 
Statistique Automatisée avec Intelligence Artificielle. Université Cadi Ayyad, Marrakech.
```

*Dernière mise à jour : Avril 2026*
