- ### Access logs
`docker logs -f --tail 1200 <container_name>`

- ### list all containers 
`docker ps -all`

- ### run container
`docker run -d -p 8000:8000 <image_name>`

- ### list all images
`docker images`

- ### build an image
`docker image build <path to dockerfile> -t <image_name>`

- ### remove image
`docker image rm <image_name>`

- ### rename container
`docker rename <old_name> <new_name>`

- ### remove container even if its exited
`docker rm <container_ID>`

- ### rename image
`docker image tag server:latest myname/server:latest`


- ## Push to docker hub
	- create docker image
	- `docker tag <image_id> yourhubusername/verse_gapminder:firsttry`
	- `docker push yourhubusername/verse_gapminder:firsttry`