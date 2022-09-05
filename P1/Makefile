all:
	docker build --tag badas .
	docker run --privileged -it --name test badas
start:
	docker start -i test
clean:
	docker rm $$(docker ps -aq)
	docker rmi -f $$(docker images -qa)
