- Example `/tmp/var.yml`
```yml
docker_composes:
  portainer:
    git_repo_url: https://github.com/jeo1/docker-portainer.git
    docker_dir: /home/docker/portainer
    env_files:
      - env_src: /tmp/portainer.env
        env_dst: /home/docker/portainer/.env
  readarr:
    git_repo_url: https://github.com/jeo1/docker-readarr.git
    docker_dir: /home/docker/readarr
    config_dir:
      - config_path: /home/jeo/a1
        file_mode: "0777"
        state: directory
      - config_path: /home/jeo/a2
        file_mode: "0777"
        state: directory
    env_files:
      - env_src: /tmp/readarr.env
        env_dst: /home/docker/readarr/.env
    config_repo_url: http://192.168.1.108:3000/jeo/test.git
    config_repo_dir: /home/config/readarr
```



`ansible-pull -U https://github.com/jeo1/ansible-docker-deploy.git -i '<user>' -e '@/tmp/var.yml'`


```yml
docker_composes:
  readarr:
    git_repo_url: https://github.com/jeo1/docker-readarr.git
    docker_dir: /home/docker/readarr
    env_files:
      - env_src: /home/jeo/readarr.env
        env_dst: /home/docker/readarr/.env    
    config_repo_url: http://192.168.1.150:3000/jeo/config-readarr.git
    config_repo_dir: /home/config/readarr
```