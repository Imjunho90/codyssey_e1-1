내 컴퓨터에 개발자용 '작업실' 꾸미기



# 1.터미널 조작 로그 기록

## 현재 위치 확인, 목록 확인(숨김 파일 포함)
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % pwd
/Users/junhojeon/codyssey/codyssey-1-1

(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % ls -la
total 0
drwxr-xr-x  2 junhojeon  staff   64  8  1 16:50 .
drwxr-xr-x  6 junhojeon  staff  192  8  1 16:50 ..
~~~

## 이동, 생성, 복사
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % mkdir codyssey
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % touch test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd codyssey

(base) junhojeon@Junhoui-MacBookAir-2 codyssey % cp ~/codyssey/codyssey-1-1/test.txt ~/codyssey/codyssey-1-1/codyssey
~~~

## 이동/이름변경, 삭제
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % cd codyssey-1-1
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % mv test.txt codyssey/test_1.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd codyssey
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % ls
test.txt	test_1.txt

(base) junhojeon@Junhoui-MacBookAir-2 codyssey % rm test.txt test_1.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % ls
(base) junhojeon@Junhoui-MacBookAir-2 codyssey % 
~~~

# 2. 권한 실습

## 파일 권한 확인 및 변경
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % touch test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % echo 'hello codyssey' > test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cat test.txt
hello codyssey
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % chmod 000 test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % ls -l test.txt
----------  1 junhojeon  staff  15  8  1 17:19 test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cat test.txt
cat: test.txt: Permission denied

(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % chmod 700 test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % ls -l test.txt
-rwx------  1 junhojeon  staff  15  8  1 17:19 test.txt
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cat test.txt
hello codyssey
~~~

~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % mkdir test
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % ls -ld test
drwxr-xr-x  2 junhojeon  staff  64  8  1 17:24 test
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd test
(base) junhojeon@Junhoui-MacBookAir-2 test % cd -
~/codyssey/codyssey-1-1
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % chmod 000 test
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd test
cd: permission denied: test

(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % chmod 100 test
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % cd test
(base) junhojeon@Junhoui-MacBookAir-2 test % cd -
~/codyssey/codyssey-1-1
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % ls -ld test
d--x------  2 junhojeon  staff  64  8  1 17:24 test
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % 
~~~



# 3.Docker 설치 및 기본점검

## 버전 및 동작여부 확인 결과
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker --version
Docker version 29.4.0, build 9d7ad9f


(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker info
Client:
 Version:    29.4.0
 Context:    orbstack
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.79.0
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-agent
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.25.0
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-ai
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.33.0
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v5.1.2
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-compose
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.0.47
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-debug
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  v0.4.1
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-desktop
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.4
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-dhi
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.31
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-extension
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.0
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-init
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.42.2
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-mcp
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.1
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-model
  offload: Docker Offload (Docker Inc.)
    Version:  v0.6.4
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-offload
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.1.5
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-pass
  sandbox: Docker Sandbox (Docker Inc.)
    Version:  v0.12.0
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-sandbox
  scout: Docker Scout (Docker Inc.)
    Version:  v1.22.0
    Path:     /Users/junhojeon/.docker/cli-plugins/docker-scout

Server:
 Containers: 12
  Running: 6
  Paused: 0
  Stopped: 6
 Images: 4
 Server Version: 29.4.0
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: 301b2dac98f15c27117da5c8af12118a041a31d9
 runc version: c241c0bb5e60a8e8c1b2e53d4eca8d0068d8d57e
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 7.0.11-orbstack-00360-gc9bc4d96ac70
 Operating System: OrbStack
 OSType: linux
 Architecture: aarch64
 CPUs: 8
 Total Memory: 7.818GiB
 Name: orbstack
 ID: 70d4aba1-aabe-4e7d-b2c0-90d4cd07b79c
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http://proxy.orb.internal:8305
 HTTPS Proxy: http://proxy.orb.internal:8305
 No Proxy: localhost,127.0.0.1,127.0.0.0/8,::1,10.0.0.0/8,172.16.0.0/12,192.168.0.0/16,0.250.250.0/24,*.orb.internal,*.local,gateway.docker.internal,host.internal,host.docker.internal,host.lima.internal,docker.for.mac.localhost,docker.for.mac.host.internal
 Experimental: true
 Insecure Registries:
  ::1/128
  127.0.0.0/8
 Live Restore Enabled: false
 Product License: Community Engine
 Default Address Pools:
   Base: 192.168.97.0/24, Size: 24
   Base: 192.168.107.0/24, Size: 24
   Base: 192.168.117.0/24, Size: 24
   Base: 192.168.147.0/24, Size: 24
   Base: 192.168.148.0/24, Size: 24
   Base: 192.168.155.0/24, Size: 24
   Base: 192.168.156.0/24, Size: 24
   Base: 192.168.158.0/24, Size: 24
   Base: 192.168.163.0/24, Size: 24
   Base: 192.168.164.0/24, Size: 24
   Base: 192.168.165.0/24, Size: 24
   Base: 192.168.166.0/24, Size: 24
   Base: 192.168.167.0/24, Size: 24
   Base: 192.168.171.0/24, Size: 24
   Base: 192.168.172.0/24, Size: 24
   Base: 192.168.181.0/24, Size: 24
   Base: 192.168.183.0/24, Size: 24
   Base: 192.168.186.0/24, Size: 24
   Base: 192.168.207.0/24, Size: 24
   Base: 192.168.214.0/24, Size: 24
   Base: 192.168.215.0/24, Size: 24
   Base: 192.168.216.0/24, Size: 24
   Base: 192.168.223.0/24, Size: 24
   Base: 192.168.227.0/24, Size: 24
   Base: 192.168.228.0/24, Size: 24
   Base: 192.168.229.0/24, Size: 24
   Base: 192.168.237.0/24, Size: 24
   Base: 192.168.239.0/24, Size: 24
   Base: 192.168.242.0/24, Size: 24
   Base: 192.168.247.0/24, Size: 24
   Base: fd07:b51a:cc66:d000::/56, Size: 64
 Firewall Backend: iptables

WARNING: DOCKER_INSECURE_NO_IPTABLES_RAW is set
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % 

~~~


# 4.Docker 기본 운영 명령 수행

## Docker 이미지 다운로드/목록 확인 

~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker pull hello-world
Using default tag: latest
latest: Pulling from library/hello-world
58dee6a49ef1: Pull complete 
c3bdf82c34d1: Download complete 
Digest: sha256:c3cbe1cc1aa588a64951ac6286e0df7b27fe2e6324b1001c619bb358770c0178
Status: Downloaded newer image for hello-world:latest
docker.io/library/hello-world:latest

What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview hello-world

(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker images
                                                           i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   c3cbe1cc1aa5       18.5kB         10.3kB  
~~~

## 컨테이너: 실행/중지/목록 확인


##컨테이너 실행
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker run -d nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
9f270a0f328f: Pull complete 
59f54fbcd984: Pull complete 
54c3b3bebc0a: Pull complete 
9b1a2f3b8553: Pull complete 
627a5a63361a: Pull complete 
4cca0d328dc5: Pull complete 
94f27359a4c8: Pull complete 
d07ed3315b0d: Download complete 
52efd73ccaa6: Download complete 
Digest: sha256:5a88c9c45479443d7be2eadc894b4ed0a9801bae03d97a5760ae13b5c2005942
Status: Downloaded newer image for nginx:latest
34060bc4edb73c1e0d0def88e3b042f22fbeaf92c1bd9650b7c66c049d29c942
~~~
## 컨테이너 중지 및 목록확인
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker stop inspiring_sanderson
inspiring_sanderson
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker ps -a
CONTAINER ID   IMAGE     COMMAND                   CREATED         STATUS                      PORTS     NAMES
34060bc4edb7   nginx     "/docker-entrypoint.…"   2 minutes ago   Exited (0) 27 seconds ago             inspiring_sanderson

~~~

## 로그 및 리소스 확인
~~~bash
(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker logs inspiring_sanderson
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/08/01 08:41:29 [notice] 1#1: using the "epoll" event method
2026/08/01 08:41:29 [notice] 1#1: nginx/1.31.3
2026/08/01 08:41:29 [notice] 1#1: built by gcc 14.2.0 (Debian 14.2.0-19) 
2026/08/01 08:41:29 [notice] 1#1: OS: Linux 7.0.11-orbstack-00360-gc9bc4d96ac70
2026/08/01 08:41:29 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 20480:1048576
2026/08/01 08:41:29 [notice] 1#1: start worker processes
2026/08/01 08:41:29 [notice] 1#1: start worker process 29
2026/08/01 08:41:29 [notice] 1#1: start worker process 30
2026/08/01 08:41:29 [notice] 1#1: start worker process 31
2026/08/01 08:41:29 [notice] 1#1: start worker process 32
2026/08/01 08:41:29 [notice] 1#1: start worker process 33
2026/08/01 08:41:29 [notice] 1#1: start worker process 34
2026/08/01 08:41:29 [notice] 1#1: start worker process 35
2026/08/01 08:41:29 [notice] 1#1: start worker process 36
2026/08/01 08:43:53 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2026/08/01 08:43:53 [notice] 29#29: gracefully shutting down
2026/08/01 08:43:53 [notice] 29#29: exiting
2026/08/01 08:43:53 [notice] 30#30: gracefully shutting down
2026/08/01 08:43:53 [notice] 30#30: exiting
2026/08/01 08:43:53 [notice] 33#33: gracefully shutting down
2026/08/01 08:43:53 [notice] 34#34: gracefully shutting down
2026/08/01 08:43:53 [notice] 36#36: gracefully shutting down
2026/08/01 08:43:53 [notice] 33#33: exiting
2026/08/01 08:43:53 [notice] 29#29: exit
2026/08/01 08:43:53 [notice] 34#34: exiting
2026/08/01 08:43:53 [notice] 33#33: exit
2026/08/01 08:43:53 [notice] 36#36: exiting
2026/08/01 08:43:53 [notice] 34#34: exit
2026/08/01 08:43:53 [notice] 35#35: gracefully shutting down
2026/08/01 08:43:53 [notice] 36#36: exit
2026/08/01 08:43:53 [notice] 35#35: exiting
2026/08/01 08:43:53 [notice] 30#30: exit
2026/08/01 08:43:53 [notice] 35#35: exit
2026/08/01 08:43:53 [notice] 31#31: gracefully shutting down
2026/08/01 08:43:53 [notice] 32#32: gracefully shutting down
2026/08/01 08:43:53 [notice] 31#31: exiting
2026/08/01 08:43:53 [notice] 31#31: exit
2026/08/01 08:43:53 [notice] 32#32: exiting
2026/08/01 08:43:53 [notice] 32#32: exit

(base) junhojeon@Junhoui-MacBookAir-2 codyssey-1-1 % docker stats inspiring_sanderson
CONTAINER ID   NAME                  CPU %     MEM USAGE / LIMIT   MEM %     NET I/O   BLOCK I/O   PIDS
34060bc4edb7   inspiring_sanderson   0.00%     0B / 0B             0.00%     0B / 0B   0B / 0B     0
~~~





