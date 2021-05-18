create-network:
	@docker network create sandy || true > /dev/null

build:
	docker run -v ~/.m2:/root/.m2 -v ${PWD}:/usr/src  -w /usr/src  maven:3-jdk-8 mvn clean package -DskipTests
	docker build -t sandy .

run:
	docker run -it --rm --name db -e MYSQL_USER=sandy -e MYSQL_PASSWORD=sandy123 -e MYSQL_DATABASE=springbootdb --net sandy centos/mysql-57-centos7
	docker run -it --rm --net sandy sandy

