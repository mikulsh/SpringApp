create-network:
	@docker network create sandy || true > /dev/null

build:
	docker run -v ~/.m2:/root/.m2 -v ${PWD}:/usr/src  -w /usr/src  maven:3-jdk-8 mvn clean package -DskipTests
	docker build -t sandy .
	docker build -t db -f Dockerfile.mysql .

run:
	docker run -it --rm -d --name db --net sandy db
	docker run -it --rm -p 8080:8080 -d --net sandy sandy

