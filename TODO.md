# TODO – ModBotAI Week 1 Development Sprint

## Day 1 – Design & Setup
- [X] Finalize system architecture diagram (add to docs/)
- [X] Initialize GitHub repository & enable Issues/PRs
- [X] Create Python virtual environments for all components
- [ ] Scaffold directory structure as per project layout
- [ ] Set up local PostgreSQL instance (ensure pgvector extension)
- [ ] Write initial Pydantic schemas: `data_pipeline/schemas.py`
- [ ] Create basic Django models: `django_app/content_review/models.py`
- [ ] Add a starter GitHub Actions workflow: `.github/workflows/ci-cd.yml`
- [ ] Initial CI config: install dependencies, lint, check black/mypy
- [ ] Commit .env.example for required secrets/config
- [ ] Document setup in README

---

## Day 2 – Data Ingestion & Storage
- [ ] Implement Reddit ingestion: `data_pipeline/praw_ingest.py` (PRAW, env-based config)
- [ ] Validate/clean comments with Pydantic; insert into Postgres
- [ ] Define DB schema in Django, run initial migrations
- [ ] Store both raw and cleaned text fields in DB
- [ ] Set up `langgraph_flow.py` stub—clean comment, print output
- [ ] Write tests to confirm data insertion (`tests/test_django.py`)
- [ ] Document ingestion process in README

---

## Day 3 – Model Training & Integration
- [ ] Fine-tune RoBERTa on toxic comment data: `models/fine_tune_roberta.ipynb`
- [ ] Save model checkpoint (`models/toxic_classifier.pt`)
- [ ] Write inference script: `models/classifier.py` (load model, predict on sample)
- [ ] Integrate classifier code so FastAPI can call it
- [ ] Update `langgraph_flow.py` to add classify step (output label)
- [ ] Verify end-to-end: ingest, clean, classify, print result
- [ ] Add unit test for classifier script

---

## Day 4 – FastAPI Endpoints
- [ ] Define request/response models: `fastapi_app/schemas.py`
- [ ] Implement `/moderate` endpoint in `fastapi_app/endpoints.py` (classifies comment)
- [ ] Implement `/search` endpoint (embedding + pgvector similarity query)
- [ ] Set up OAuth2 security: `fastapi_app/auth.py`
- [ ] Write pytest API tests (`tests/test_fastapi.py`): POST /moderate, GET /search
- [ ] Ensure endpoints return correct responses, validate JWT
- [ ] Document API endpoints in README

---

## Day 5 – Django Admin Integration
- [ ] Register Comment model in `django_app/content_review/admin.py`
- [ ] Add list filters (e.g., is_toxic), approve/delete actions
- [ ] Customize admin display and (optionally) add stats views
- [ ] Test full pipeline: moderate via API, check admin dashboard
- [ ] Ensure Django connects to shared Postgres (test DB_URL config)
- [ ] Document admin usage/workflow in README

---

## Day 6 – Containerization & Orchestration
- [ ] Write Dockerfiles: `docker/Dockerfile.fastapi`, `docker/Dockerfile.django`
- [ ] Configure Postgres image/init script for pgvector (`docker/Dockerfile.postgres` or `k8s/pgvector-initdb.sql`)
- [ ] Build/tag images, add to local registry
- [ ] Write Kubernetes manifests: `k8s/fastapi-deploy.yaml`, `k8s/django-deploy.yaml`, `k8s/postgres-statefulset.yaml`
- [ ] Define Services (ClusterIP/LoadBalancer) for each microservice
- [ ] Deploy locally (minikube/kind); verify all services connect/persist data
- [ ] Update README with Docker/K8s run instructions

---

## Day 7 – CI/CD, Testing & Final Touches
- [ ] Complete CI pipeline: auto-test, lint, build, and push Docker images
- [ ] Add workflow step to deploy to K8s via kubectl (for staging)
- [ ] Run full suite of tests—add/expand tests for edge cases
- [ ] Finalize documentation (README: architecture, API, admin, workflow)
- [ ] Record demo video/gif: API → admin → search (optional, docs/)
- [ ] Code cleanup: refactor, docstrings, format, update .envs
- [ ] Review all modules for integration; ensure smooth E2E flow

---

## Bonus/Stretch (Optional)
- [ ] Add Prometheus exporters for service monitoring
- [ ] Draft Grafana dashboard config for ops
- [ ] Add caching (Redis/LRU) for high-frequency queries
- [ ] Document further scalability or monitoring strategies

---
