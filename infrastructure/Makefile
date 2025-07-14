deploy_db:
	kubectl apply -f db/
build_backend:
	cd .. && docker build -t backend:1.0.0 -f infrastructure/docker/Dockerfile-backend .
deploy_backend:
	kubectl apply -f backend/