# Poverty App — Project Structure

This file contains the Mermaid source for the project structure diagram.

```mermaid
flowchart TB
  Root["app/"]

  subgraph Application[Application Files]
    app_py["app.py"]
    app_modern["app_modern.py"]
    recommender["recommendation_system.py<br/>recommendation_engine.py<br/>recommendation_function.py"]
  end

  subgraph ConfigAndData[Config & Data Files]
    appcfg["app_config.json"]
    feature_files["feature_list.json<br/>feature_schema.json<br/>feature_target_config.json"]
    encoding_files["feature_encoder.json<br/>target_encoding_config.json"]
    schemas["api_prediction_schema.json<br/>inference_feature_schema.json<br/>model_feature_schema.json"]
    mapping["dropdown_mapping.json"]
    performance["model_performance.json<br/>shap_feature_impact.json"]
  end

  subgraph Models[Model Artifacts]
    model_files["app_model.pkl<br/>champion_model.pkl<br/>champion_model_package.pkl<br/>data_scaler.pkl"]
  end

  subgraph Storage[Runtime Storage]
    db_files["Poverty_app.db<br/>poverty7_app.db"]
    uploads["uploads/"]
    outputs["outputs/"]
  end

  subgraph Documentation[Documentation]
    dfd["docs/dfd.*"]
    erd["docs/erd.*"]
    structure["docs/project_structure.*"]
    docs_readme["docs/README.md"]
    puppeteer["docs/puppeteer-config.json"]
  end

  subgraph Packages[Dependencies]
    node_modules["node_modules/"]
    package_files["package.json<br/>package-lock.json<br/>requirements.txt"]
  end

  Root --> Application
  Root --> ConfigAndData
  Root --> Models
  Root --> Storage
  Root --> Documentation
  Root --> Packages
```

Notes:
- The diagram reflects the current repository organization under `e:\final year project\app`.
- `node_modules/` is included as the local dependency folder installed by npm.
- `outputs/` and `uploads/` are runtime storage folders for export artifacts and uploaded files.
