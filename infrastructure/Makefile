build_all: build_backend build_fe deploy_db deploy_backend deploy_fe

destroy_all: delete_db delete_backend delete_fe docker_clean

# DB
deploy_db:
	kubectl apply -f db/pg-ns.yaml && \
	kubectl apply -f db/
delete_db:
	kubectl delete -f db/

# Backend
deploy_backend:
	kubectl apply -f backend/backend-ns.yaml && \
	kubectl apply -f backend/
	
delete_backend:
	kubectl delete -f backend/

build_backend:
	cd .. && docker build --no-cache -t  my-backend:1.0.0 -f infrastructure/docker/Dockerfile-backend .

# Frontend
rebuild_fe: scale_down_fe docker_clean build_fe scale_up_fe

scale_up_fe:
	kubectl scale deployment frontend -n frontend --replicas=1

scale_down_fe:
	kubectl scale deployment frontend --replicas=0 -n frontend && sleep 3
	
build_fe:
	cd .. && docker build --no-cache -t frontend:1.0.0 -f infrastructure/docker/Dockerfile-frontend .

deploy_fe:
	kubectl apply -f frontend/fe-ns.yaml && \
	kubectl apply -f frontend/

delete_fe:
	kubectl delete -f frontend/

# Clean
docker_clean:
	docker system prune -f && docker image prune -a -f


