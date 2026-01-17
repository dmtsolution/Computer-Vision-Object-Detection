
DÉTECTEUR DE CHATS - EXPORT COMPLET
Généré le : 04/01/2026 à 20:58

CONTENU :
- best_model.pth          : Meilleur modèle (plus basse val_loss)
- final_model.pth         : Modèle final (si présent)
- training_curves.png     : Courbes d'entraînement
- resultats_seuils.png    : Résultats par seuil de confiance
- predictions_test.png    : Exemples de prédictions
- resultats_evaluation.json : Métriques détaillées
- training_history.json   : Historique complet

PERFORMANCES (seuil recommandé : 0.8) :
- Précision   : 98.3 %
- Rappel      : 97.7 %
- F1-score     : 0.980
- IoU moyen    : 0.922

UTILISATION (inférence simple) :
import torch
from torchvision.models.detection import fasterrcnn_resnet50_fpn_v2
from torchvision.models.detection.faster_rcnn import FastRCNNPredictor

model = fasterrcnn_resnet50_fpn_v2(weights=None)
in_features = model.roi_heads.box_predictor.cls_score.in_features
model.roi_heads.box_predictor = FastRCNNPredictor(in_features, 2)
model.load_state_dict(torch.load('best_model.pth', map_location='cpu'))
model.eval()
