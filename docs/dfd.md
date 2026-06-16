# Poverty App — Data Flow Diagram

```mermaid
flowchart LR
  %% External actor
  User([User])

  %% Frontend / App
  WebApp[[Web App\n(app.py)]]
  Uploads[(Uploads\nuploads/)]

  %% Core services
  RecSystem[[Recommendation System\n(recommendation_system.py)]]
  RecEngine[[Recommendation Engine\n(recommendation_engine.py)]]

  %% ML pipeline
  FeatureList[(Feature List\nfeature_list.json, feature_schema.json)]
  FeatureEncoder[[Feature Builder / Encoder\n(build_features(), feature_encoder.json)]]
  Scaler[(Scaler\ndata_scaler.pkl)]
  Model[(Trained Model\napp_model.pkl / champion_model.pkl)]

  %% Data stores & configs
  DB[(SQLite DB\nPoverty_app.db)]
  RecDB[(Recommendations DB\nrecommendations.json / RECOMMENDATION_DB)]
  Configs[(Config Files\ninference_config.json, app_config.json)]
  Outputs[(Outputs\nrecommendations.json, outputs/, pdfs/)]

  %% Flows
  User -->|submit profile / upload| WebApp
  User -->|download report / view results| Outputs
  Uploads -->|profile images / CSV| WebApp

  WebApp -->|reads/writes users & preds| DB
  WebApp -->|loads ML pipeline| Model
  WebApp -->|loads scaler & features| Scaler
  WebApp -->|reads feature list| FeatureList
  WebApp -->|requests recommendations| RecSystem

  WebApp -->|build_features(...)| FeatureEncoder
  FeatureList --> FeatureEncoder
  FeatureEncoder -->|feature vector| Scaler
  Scaler -->|scaled X| Model
  Model -->|predict & probabilities| WebApp

  WebApp -->|save prediction| DB
  WebApp -->|generate PDF / charts| Outputs

  RecSystem -->|query class -> formatted recs| RecDB
  RecSystem -->|return formatted recommendations| WebApp
  RecEngine -->|(alternative engine)| RecDB

  Configs -->|settings| WebApp
  Configs -->|settings| RecSystem

  %% Notes
  subgraph "" [ ]
    style "" fill:none,stroke:none
  end
```
