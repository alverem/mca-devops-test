deploy_db:
	kubectl apply -f db/pg-ns.yaml && \
	kubectl apply -f db/
delete_db:
	kubectl delete -f db/


deploy_backend:
	kubectl apply -f backend/backend-ns.yaml && \
	kubectl apply -f backend/
	


delete_backend:
	kubectl delete -f backend/

build_backend:
	cd .. && docker build -t backend:1.0.1 -f infrastructure/docker/Dockerfile-backend .

run_backend:
	docker run --rm backend:1.0.1 

docker_clean:
	docker system prune
#-e SPRING_PROFILES_ACTIVE=prod \
#	-e SPRING_POSTGRES_URL=jdbc:postgresql://localhost:5432/postgres \
#	-e SPRING_POSTGRES_USERNAME=myapplication \
#	-e SPRING_POSTGRES_PASSWORD=M3P@ssw0rd! \	