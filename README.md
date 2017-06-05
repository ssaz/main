```
yum -y install git

# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# interactive mode !!!
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# add ssh public key to github user profile
# then
git config --global user.name "mailaz"
git config --global user.email "mailaz"
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# ----------------------------------------------------------------------------------------------

# centos_for_cloud

docker pull centos:7.3.1611

cd /var/lib/docker/src/
mkdir centos_for_cloud
cd centos_for_cloud/
vi README.md
vi LICENSE.md
vi .gitignore
vi Dockerfile
vi entrypoint.sh
vi chpwd.sh

docker build --rm -t centos_for_cloud .
docker run -d -p 2222:22 centos_for_cloud | cut -c 1-12 | xargs docker logs -f
ctrl+c

# test
# ignore

docker ps -a|awk '{print $1}'|grep -v 'CONTAINER'|xargs docker rm -f

# push to docker hub
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# interactive mode !!!
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# create user, organization and repository in docker hub
# then
docker login
# input username password email
# then
docker tag centos_for_cloud ssorg/centos_for_cloud
docker push ssorg/centos_for_cloud
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# push to github
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# interactive mode !!!
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
git init
git add *
git add .gitignore
git commit -m "init"
git remote add origin git@github.com:ssaz/centos_for_cloud.git
git push origin master
# then backup in project
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# ----------------------------------------------------------------------------------------------

# shadowsocks_for_docker

# shadowsocks-libev_for_docker

# shadowsocksr_for_docker

# ----------------------------------------------------------------------------------------------
```
