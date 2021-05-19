create-network:
	@docker network create sandy || true > /dev/null

build:
	docker run -v ~/.m2:/root/.m2 -v ${PWD}:/usr/src  -w /usr/src  maven:3-jdk-8 mvn clean package -DskipTests
	docker build -t sandy .
	docker build -t db -f Dockerfile.mysql .

run:
	docker rm -f db-dev-dev || true
	docker rm -f db || true
	docker run -it --rm -d --name db-dev-dev --net sandy db
	docker rm -f sandy || true
	docker run -it --rm -p 8080:8080 --name  sandy -d --net sandy sandy

run-external:
	docker rm -f db || true
	docker rm -f db-dev-dev || true
	docker run -it --rm -d --name db --net sandy db
	docker rm -f sandy || true
	docker run -it -d --rm -p 8080:8080 --name sandy -e SPRING_CONFIG_LOCATION=/etc/app/config/ -v ${PWD}/config:/etc/app/config/ --net sandy sandy

