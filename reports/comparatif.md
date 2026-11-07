# Comparatif des approches - projet fraude (TP04)

Mesures locales : poste Windows, Python 3.10, FLAML 2.8.0, scikit-learn 1.7.2 (7 novembre 2026).
Documentation cloud : pages officielles listees dans le sujet, consultation du 7 novembre 2026.
Les tarifs cloud sont des ordres de grandeur : verifiez-les sur la page de tarification le jour du rendu.

| Approche | F1 test | Temps humain | Temps machine | Cout estime (source, date) | Explicabilite | Export / reversibilite |
|---|---|---|---|---|---|---|
| Logistique (ref.) | 0.7407 | ~2 min | 0.05 s | 0 (poste local) | Maximale (coefficients) | Total |
| Manuel (TP2) | 0.8669 | ~30-60 min (essais du TP2) | 1.9 s (entrainement final) | 0 (poste local) | Moyenne/Bonne (importances, arbres) | Total |
| FLAML 60 s | 0.8582 (xgboost) | ~2 min | 60.6 s | 0 (poste local) | Moyenne/Basse (journal des 154 essais) | Total (lgbm/xgboost exportable) |
| Vertex AI AutoML | non mesure | ~15-30 min (console) | >= 1 h (budget minimal 1 heure de noeud) | facture par heure de noeud (ordre de grandeur ~20 $/h, Vertex AI pricing, 07/11/2026) | Bonne (importances, evaluation) | Faible / Verrouillage (Vendor Lock-in) |
| SageMaker Autopilot | non mesure | ~15-30 min (Canvas) | dizaines de minutes | facture a l'usage des instances d'entrainement et d'inference (SageMaker pricing, 07/11/2026) | Bonne (rapport d'explicabilite, notebooks generes) | Faible / Verrouillage (Vendor Lock-in) |
| Azure Automated ML | non mesure | ~15-30 min (studio) | dizaines de minutes | pas de surcout AutoML, on paie le cluster de calcul a l'heure (Azure ML pricing, 07/11/2026) | Bonne (explications du modele) | Faible / Verrouillage (Vendor Lock-in) |

## Commentaire (5 lignes)

1. **Logistique** : baseline obligatoire, quasi instantanee et interpretable ; tout modele plus complexe doit la battre nettement (+0.12 de F1 ici).
2. **Reglage manuel** : meilleur F1 (0.8669), mais il a demande du temps humain et de l'expertise ; adapte quand on connait bien le probleme.
3. **FLAML local** : en 60 s et deux minutes de travail, un F1 a 0.009 du manuel, gratuit et exportable : ideal pour une premiere baseline solide.
4. **Plateformes cloud** : justifiees pour une equipe sans infrastructure, de gros volumes ou un besoin de deploiement/monitoring integre, au prix du cout horaire et de la dependance au fournisseur.
5. Dans tous les cas, le budget au-dela de 60 s n'a rien rapporte (120 s = meme modele) : le rendement du calcul plafonne vite.
