# Container_Infrastructure_flipped_learning
CI/CD 관련 이론을 위한 공간입니다. (쿠버네티스, 도커, 젠킨스, 프로메테우스, 그라파나 등)

---
# 목차
- 1. 컨테이너 인프라 환경
- 2. 테스트 환경
- 3. 쿠버네티스
- 4. 도커
- 5. 젠킨스
- 6. 프로메테우스 및 그라파나
---
# 내용

※주로 참고 도서 : 컨테이너 인프라 환경 구축을 위한 쿠버네티스/도커

### 1. 컨테이너 인프라 환경

- 엔지니어가 개발 환경을 구축하면 사용자(개발자)는 그에 맞는 Tool을 모두 설치해야 했던 On-premises 환경은 이제 구 시대 환경

- 이미 구성된 환경을 사용자(개발자)가 필요에 따라 선택 및 조합하여 사용할 수 있는 IaaS 환경이 대두되고 있음

- 기존 계획 단계에서 설계 및 환경을 완전히 구비한 후 예정된 목표를 달성하는 폭포수 방법론

- 애자일(Agile) 방법론은 일정 주기를 정한 다음 해당 주기에 맞춰 요구 사항을 충족시키는 Proto 타입을 만들고 개선하여 최종 목표에 점진적으로 접근

- 이를 위해 인프라는 다음과 같이 변화하고 있음

  - 사용자(개발자)가 요구하는 인프라를 즉시 제공하는 기능 유지
  
  - 사용자(개발자)마다 독립적인 환경에서 개발해도 모두 동일한 결과를 도출 가능
  
  - 개발된 SW의 성능 보장 및 인프라 가용 리소스를 최대한 확보 가능

- 컨테이너는 하나의 운영 체제 커널에서 다른 프로세스에 영향을 받지 않고 독립적으로 실행되는 프로세스 상태

- 컨테이너는 가상화 상태에서 동작하는 프로세스보다 가볍고 빠르게 동작

#### <모놀리식 아키텍처와 마이크로 서비스 아키텍처>

<img src="https://user-images.githubusercontent.com/101415950/196708479-94084c8b-e211-41ac-9583-0c56c9c744fb.png" width="80%" height="80%">
(출처 : https://blog.lgcns.com/1278)

- 모놀리식 아키텍처
	
	- 하나의 큰 목적이 있는 서비스 또는 애플리케이션에 여러 기능이 통합된 구조
	
	- 하나의 결합된 코드로 구성되므로 초기 단계에서 설계하기 용이
	
	- 개발이 좀 더 단순하고 코드 관리가 간편
	
	- 운영하는 과정에서 수정이 많을 경우, 결합도가 높아 하나의 서비스 수정이 다른 서비스에 영향끼칠 수 있음

	- 소규모 프로젝트에 적합

- 마이크로 서비스 아키텍처

	- 개별 기능을 하는 작은 서비스를 각각 개발하여 연결하는 방식으로 각 서비스가 독립적으로 동작할 수 있음

	- 개발한 서비스 재활용 용이
	
	- 서비스 수정 시 다른 서비스에 영향을 끼칠 가능성이 적어 사용량 변환에 따라 특정 서비스 확장 가능

	- 사용자의 요구 사항에 따라 가용성을 즉각적으로 확보해야 하는 IaaS 환경에 적합

	- 모놀리식 아키텍처에 비해 복잡도가 높고 각 서비스가 서로 유기적으로 통신하는 구조이므로 네트워크를 통한 호출 횟수가 증가   
	  => 성능에 영향

	- 대규모 프로젝트에 적합

#### <컨테이너 인프라 환경 지원 도구>

- 컨테이너 인프라 환경은 컨테이너, 컨테이너 관리, 개발 환경 구성 및 배포 자동화, 모니터링으로 구성

- 도커

	- 컨테이너 환경에서 독립적으로 애플리케이션을 실행할 수 있도록 컨테이너를 만들고 관리하는 것을 지원

	- 운영체제 환경 관계없이 독립적인 환경에서 일관적인 결과 보장

- 쿠버네티스

	- 다수의 컨테이너 관리에 사용

	- 컨테이너 자동 배포, 배포된 컨테이너에 대한 동작 보증, 부하에 따른 동적 확장 등 기능 제공
	
	- 컨테이너 인프라에 필요한 기능을 통합하고 관리하는 솔루션

	- 컨테이너 인프라를 기반으로 다양한 서비스를 효율적으로 관리하는 환경 제공
	
	- 내외부와 유연하게 연결하는 역할

- 젠킨스

	- 빌드, 테스트, 패키지화, 배포 단계 모두 자동화하여 계발 단계를 표준화하는 CI/CD 제공
	
	- 개발된 코드의 빠른 적용과 효과적인 관리를 통해 개발 생산성을 높이는 데 초점이 맞춰져 있음

	- 단일 기능을 빠르게 개발해 적용해야 하는 환경에 적합(=컨테이너 인프라 환경)

- 프로메테우스 및 그라파나

	- 모니터링을 위한 도구

	- 프로메테우스는 상태 데이터를 수집

	- 그라파나는 프로메테우스로 수집한 데이터를 시각화

	- 컨테이너 인프라 환경에서 많은 종류의 소규모 기능이 각각 나누어 개발되기 때문에 중앙 모니터링이 필요

	- 프로메테우스 및 그라파나는 컨테이너로 패키징이 되어 동작하며 최소환의 자원으로 쿠버네티스 클러스터 상태를 시작적으로 표현

---
### 2. 테스트 환경 구성

- 코드형 인프라

	- 코드로 하드웨어를 설정 후 운영체제 설치 및 네트워크 구성하여 개발환경 구층

	- 코드로 인프라를 소프트웨어처럼 다룸

- 버추얼 박스

	- 가상화 소프트웨어

	- 다운로드 링크 : https://www.virtualbox.org/wiki/Download_Old_Builds_6_1 (6.1.12버전)

	- 모두 기본상태로 next 클릭 후 설치 완료

- 베이그런트

	- 프로비저닝(provisioning) 기능 수행
	
		- 사용자의 요구에 맞게 시스템 자원을 할당, 배치, 배포

		- 필요할 때 시스템을 사용할 수 있는 상태로 변경

	- 다운로드 링크 : https://www.vagrantup.com/downloads (2.2.9버전)

	- 모두 기본상태로 next 클릭 후 설치 완료

	- vagrant init : 프로비저닝을 위한 기초 파일 생성

	- vagrant up : Vagrantfile을 읽어 프로비저닝 진행
	
	- vagrant halt : 베이그런트에서 다루는 가상 머신 종료
	
	- vagrant destroy : 베이그런트에서 관리하는 가상 머신 삭제
	
	- vagrant ssh : 베이그런트에서 관리하는 가상 머신에 ssh로 접속

	- vagrant provision : 베이그런트에서 관리하는 가상 머신에 변경된 설정 적용

#### <Tool 정상 동작 확인>

- 먼저 프로비저닝을 위한 코드 작성 후 베이그런트에서 호출한 뒤 버추얼 박스에 운영 체제 설치

- 베이그런트 설치 디렉터리(c:\HashiCorp)에 프로비저닝을 위한 코드 작성 권장

- vagrant init으로 생성 후 바로 vagrant up 실행하면 Vagrantfile이 config.vm.box = "base"로 설정되어 있어 base이미지를 찾지 못하여 에러 발생

- config.vm.box = "base"를 config.vm.box = "sysnet4admin/CentOS-k8s"으로 변경 후 저장하여 이미지 설정 필요

#### <베어그런트로 테스트 환경 구축>

Vagrantfile을 수정하여 원하는 구성이 자동으로 CentOS에 입력되도록 수행

[Vagrantfile 예시 코드]
```
#do |이름|으로 시작한 작업은 end로 종료
#Providier는 베이그런트를 통해 제공되는 코드가 실제로 가상 머신으로 배포되게 하는 소프트웨어
#auto_correct:true는 포트가 중복되면 포트가 자동으로 변경

# -*- mode: ruby -*-				 	#루비(ruby) 언어임을 인식하는 호환 코드
# vi: set ft=ruby :				 	#ft는 파일 종류(file type)의 약자

Vagrant.configure("2") do |config|		 	#"2"는 API 버전, do |config|는 베이그런드 설정의 시작
  N = 3 # max number of worker nodes			#쿠버네티스에서 작업을 수행할 worker node 수 설정(args: N을 통해 넘길 수 있음)
  Ver = '1.18.4' # Kubernetes Version to install	#쿠버네키스 버전을 변수로 설정

  #=============#
  # Master Node #
  #=============#

    config.vm.define "m-k8s" do |cfg|			#가상머신을 "m-k8s"로 정의, do |cfg|를 추가해 원하는 설정으로 변경
      cfg.vm.box = "sysnet4admin/CentOS-k8s"		#do |cfg|에서 적용한 내용을 받아 cfg.vm.box로 변경
      cfg.vm.provider "virtualbox" do |vb|		#Provider를 버추얼박스로 정의, 버추얼 박스에 필요한 설정을 정의하기 위해 do |vb| 추가
        vb.name = "m-k8s(github_SysNet4Admin)"		#가상머신 이름
        vb.cpus = 2					#CPU 수
        vb.memory = 3072				#메모리 크기
        vb.customize ["modifyvm", :id, "--groups", "/k8s-SgMST-1.13.1(github_SysNet4Admin)"]	#소속된 그룹 명시
      end						#들여쓰기 위치 정확하게
      cfg.vm.host_name = "m-k8s"			#가상머신 자체 설정으로 호스트이름 설정
      cfg.vm.network "private_network", ip: "192.168.1.10"	#호스트 전용 네트워크를 private_network로 설정, eth1 인터페이스를 Host-Only로 구성하고 IP 지정
      cfg.vm.network "forwarded_port", guest: 22, host: 60010, auto_correct: true, id: "ssh"	#ssh통신은 호스트 60010번을 게스트 22번으로 전달되도록 구성
      cfg.vm.synced_folder "../data", "/vagrant", disabled: true	#호스트(PC)와 게스트(가상 머신) 사이에 디렉터리 동기화가 이루어지지 않게 disabled:true 설정
      cfg.vm.provision "shell", path: "config.sh", args: N	#vm.provision "shell" 구문으로 경로에 있는 파일("config.sh")을 게스트(CentOS) 내부에서 호출하여 실행
      cfg.vm.provision "shell", path: "install_pkg.sh", args: [ Ver, "Main" ]	#변수 Ver, 문자 "Main"을 install_pkg.sh로 넘김
      cfg.vm.provision "shell", path: "master_node.sh"	#쿠버네티스 Master Node를 위한 "master_node.sh" 코드 추가
    end

  #==============#
  # Worker Nodes #
  #==============#

  (1..N).each do |i|					#1에서 3까지 반복하는 반복문으로 (1..N).each로 이루어짐
    config.vm.define "w#{i}-k8s" do |cfg|		#해당 값은 |i|를 통해 #{i}로 치환하여 사용
      cfg.vm.box = "sysnet4admin/CentOS-k8s"
      cfg.vm.provider "virtualbox" do |vb|
        vb.name = "w#{i}-k8s(github_SysNet4Admin)"
        vb.cpus = 1
        vb.memory = 2560
        vb.customize ["modifyvm", :id, "--groups", "/k8s-SgMST-1.13.1(github_SysNet4Admin)"]
      end
      cfg.vm.host_name = "w#{i}-k8s"
      cfg.vm.network "private_network", ip: "192.168.1.10#{i}"
      cfg.vm.network "forwarded_port", guest: 22, host: "6010#{i}", auto_correct: true, id: "ssh"
      cfg.vm.synced_folder "../data", "/vagrant", disabled: true
      cfg.vm.provision "shell", path: "config.sh", args: N
      cfg.vm.provision "shell", path: "install_pkg.sh", args: Ver
      cfg.vm.provision "shell", path: "work_nodes.sh"	#쿠버네티스 Worker Node를 위한 "work_node.sh" 코드 추가
    end
  end
end
```

[config.sh 예시 코드]
```
#!/usr/bin/env bash

# vim configuration 
echo 'alias vi=vim' >> /etc/profile			#vi를 호출하면 vim을 호출(코드에  하이라이트를 넣어 코드를 쉽게 구분하기 위함)

# swapoff -a to disable swapping
swapoff -a						#스왑되지 않도록 설정(쿠버네티스 설치 요구 조건을 충족하기 위해)
# sed to comment the swap partition in /etc/fstab
sed -i.bak -r 's/(.+ swap .+)/#\1/' /etc/fstab		#시스템이 다시 시작되더라도 스왑되지 않도록 설정

# kubernetes repo
gg_pkg="packages.cloud.google.com/yum/doc" # Due to shorten addr for key #리포지터리를 설정하기 위한 경로를 변수로 처리(간략화)
cat <<EOF > /etc/yum.repos.d/kubernetes.repo 		#쿠버네티스를 내려받을 리포티터리 설정 시작
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=0
repo_gpgcheck=0
gpgkey=https://${gg_pkg}/yum-key.gpg https://${gg_pkg}/rpm-package-key.gpg
EOF							#쿠버네티스를 내려받을 리포티터리 설정 끝

# Set SELinux in permissive mode (effectively disabling it)
setenforce 0						#selinux가 제한적으로 사용되지 않도록 permissive 모드로 변경
sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

# RHEL/CentOS 7 have reported traffic issues being routed incorrectly due to iptables bypassed
cat <<EOF >  /etc/sysctl.d/k8s.conf			#브리지 네트워크를 통과하는 IPv4와 IPv6의 패킷을 iptables가 관리하게 설정
net.bridge.bridge-nf-call-ip6tables = 1			#Pod(쿠버네티스에서 실행되는 객체의 최소 단위)의 통신을 iptables로 제어
net.bridge.bridge-nf-call-iptables = 1			#필요에 따라 IPVS 같은 방식으로 구성
EOF
modprobe br_netfilter					#br_netfilter 커널 모듈을 사용하여 브리지로 네트워크를 구성
							#IP 마스커레이드를 사용하여 내부 네트워크랑 외부 네트워크를 분리
							#IP 마스커레이드는 커널에서 제공하는 NAT 기능을 의미
							#br_netfilter 적용함으로써 iptables이 활성화

# local small dns & vagrant cannot parse and delivery shell code.
echo "192.168.1.10 m-k8s" >> /etc/hosts			#쿠버네티스 안에서 노드 간 통신을 이름으로 할 수 있게 하기 위한 구문
for (( i=1; i<=$1; i++  )); do echo "192.168.1.10$i w$i-k8s" >> /etc/hosts; done	#각 노드의 호스트 이름과 IP를 /etc/hosts에 설정
							#이때 Worker Node는 넘겨받은 N변수에 맞게 동적으로 생성됨
# config DNS  
cat <<EOF > /etc/resolv.conf				#외부와 통신할 수 있는 DNS 서버 지정
nameserver 1.1.1.1 #cloudflare DNS
nameserver 8.8.8.8 #Google DNS
EOF
```

[install_pkg.sh 예시 코드]

```
#!/usr/bin/env bash

# install packages 
yum install epel-release -y
yum install vim-enhanced -y
yum install git -y					#깃허브에서 코드를 내려받을 수 있게 Git을 설치

# install docker 
yum install docker -y && systemctl enable --now docker	#쿠버네티스를 관리하는 컨테이너를 설치하기 위해 도커를 설치하고 구동

# install kubernetes cluster 
yum install kubectl-$1 kubelet-$1 kubeadm-$1 -y		#넘겨받은 버전의 kubectl, kubelet, kubeadm 설치
systemctl enable --now kubelet				#kubelet 시작

# git clone _Book_k8sInfra.git 
if [ $2 = 'Main' ]; then				#전체 실행 코드를 Master Node에만 내려받도록 설정($2는 두번 째로 넘겨받은 값)
  git clone https://github.com/sysnet4admin/_Book_k8sInfra.git	#Git에서 코드를 내려받음
  mv /home/vagrant/_Book_k8sInfra $HOME			#내려받은 코드를 홈디렉터리(/root)로 옮김
  find $HOME/_Book_k8sInfra/ -regex ".*\.\(sh\)" -exec chmod 700 {} \;	#배시 스크립트(.sh)를 find로 찾아 바로 실행가능한 상태가 되도록 chmod 700 설정
fi
```

[master_node.sh 예시 코드]
```
#!/usr/bin/env bash

# init kubernetes 					#kubeadm을 통해 쿠버네티스 worker node를 받아들일 준비를 함
kubeadm init --token 123456.1234567890123456 --token-ttl 0 \	#토큰을 123456.1234567890123456로 지정하고 유지되는 시간(time to live)을 0으로 설정(기본 값인 24시간 후에 토큰이 계속 유지)
--pod-network-cidr=172.16.0.0/16 --apiserver-advertise-address=192.168.1.10	#Worker Node가 정해진 토큰에 들어오게 함
							#쿠버네티스가 자동으로 컨테이너에 부여하는 네트워크를 172.16.0.0/16(176.16.0.1 ~ 172.16.255.254)으로 제공
							#Worker Node에 접속하는 API 서버의 IP를 192.168.1.10으로 지정(Worker Node들이 자동으로 API 서버에 연결)
# config for master node only 
mkdir -p $HOME/.kube					#Master Node에서 현재 사용자가 쿠버네티스를 정상적으로 구동할 수 있게 하는 구문
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config	#설정 파일을 루트의 홈디렉터리(/root)에 복사
chown $(id -u):$(id -g) $HOME/.kube/config		#쿠버네티스를 이용할 사용자에게 권한 부여

# config for kubernetes's network 
kubectl apply -f \					#CNI(컨테이너 네트워크 인터페이스)인 Calico의 설정을 적용해 쿠버네티스의 네트워크를 구성
https://raw.githubusercontent.com/sysnet4admin/IaC/master/manifests/172.16_net_calico.yaml
```

[work_nodes.sh 예시 코드]
```
#kubeadm을 이용하여 Master Node에 접속
#접속 시 연결에 필요한 토큰은 기존 Master Node에서 생성한 123456.1234567890123456 사용
#간단히 구성하기 위해 --discovery-token-unsafe-skip-ca-verification으로 인증 무시
#API 서버 주소인 192.168.1.10으로 기본 포트 번호인 6443 포트에 접속하도록 설정

#!/usr/bin/env bash

# config for work_nodes only 
kubeadm join --token 123456.1234567890123456 \
             --discovery-token-unsafe-skip-ca-verification 192.168.1.10:6443
```

#### <id: "ssh"로 설정하는 이유>

- ssh 서비스의 기본 포트 번호인 22번을 id: "ssh"로 설정하지 않으면 중복된 두개의 포트로 설정

- 자기 자신(127.0.0.1/localhost)의 2222번 포트로 오는 내용과 모든 IP(0.0.0.0)의 60010 포트에서 오는 내용을 게스트의 22번으로 포워딩

```
vagrant port
	22(guest) => 2222(host)
	22(guest) => 60010(host)

netstat -an | findstr 2222
netstat -an | findstr 60010
```

- 명시적으로 좋지 않고 설정의 낭비를 줄이기 위해 왠만하면 id: "ssh"를 사용하는 것이 나음

#### <호스트 전용 네트워크가 정상적으로 동작하지 않는 경우>

- 최대 절전 모드나 여러 차례 가상 머신을 다시 시작하는 경우에 호스트 전용 네트워크가 정상적으로 동작하지 않을 수 있음

- 버추얼박스에서 파일>호스트 네트워크 관리자 선택

- 속성 클릭 후 DHCP 서버를 사용하지 않도록 체크를 해제, IPv4 주소에 198.168.1.1 입력

#### <vi(visual editor)와 Vim(visual editor improved)>

- vi는 유닉스 환경에서 사용되는 텍스트 편집기(editor)

- vi와 Vim의 가장 큰 차이점은 Vim은 화살표로 커서가 이동하지만, vi는 H, J, K, L로 커서를 이동

#### <PuTTY와 SuperPuTTY>

- 명령 프롬프트(Command Prompt, cmd.exe)로 가상 머신에 접근할 수 있지만 가상머신마다 각각 명령어를 통해 접근해야 하므로 불편함

- PuTTY는 터미널 접속 프로그램으로 가볍고 다양한 플러그인을 통해 여러 대의 가상 머신에 접근할 수 있음

- 접속 정보를 저장하고 바로 불러와 실행할 수 있는 기능

- 한 번에 한 대씩만 접근 가능

- https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html 링크의 Alternative binary files 항목에서 다운로드

- SuperPuTTY는 한 번에 여러 대의 가상 머신에 접근하여 분할된 창을 통해 관리

- https://github.com/jimradford/superputty/releases 에서 다운로드

- SuperPuTTY 사용 시 putty.exe 위치를 지정하여 사용

#### <127.0.0.1로 접속하는 이유>

- 192.168.1.0/24 영역대로 가상 머신의 IP를 설정하는 경우

- 현업에서는 데이터 통신과 관리 네트워크를 분리해 사용하는 데 이와 비슷하게 관리 네트워크를 분리

- 192.168.1.0/24에서 문제가 발생해도 접속하는 데 문제가 없음

- 각 가상 머신은 베이그런트에서 NAT로 사용하는 eth0에 고유 포트 포워딩 규칙이 적용 ("forwarded_port", guest: 22, host: 60010)

---
### 3. 쿠버네티스

#### <컨테이너 인프라 환경>

<img src="https://user-images.githubusercontent.com/101415950/197549006-3059f673-f0a2-40b0-8f5b-2f48abeda60f.png" width="80%" height="80%">

- 리눅스 운영 체제의 커널 하나에서 여러 개의 컨테이너가 격리된 상태로 실행되는 인프라 환경

- 컨테이너는 하나 이상의 목적을 위해 독립적으로 작동하는 프로세스

- 개인 환경에서는 1명의 관리자(사용자)가 다양한 응용프로그램을 사용하므로 각각의 프로그램을 컨테이너로 구현할 필요 없음

- 기업 환경에서는 다수의 관리자가 수천 대의 서버를 함께 관리하므로 일관성 유지를 위해 컨테이너 필요

- 여러 사람이 조작하여 설정의 일관성이 떨어진 눈송이 서버를 방지하는 효과

- 가상화 환경에서 각각의 가상 머신이 모두 독립적인 운영체제 커널을 가지고 있어야 하므로 자원을 더 소모하고 성능이 떨어짐

- 컨테이너 인프라 환경은 커널 하나에 컨테이너 여러 개가 격리된 형태로 실행되므로 자원을 효율적으로 사용하고   
  수행해야 하는 단계도 적어 속도 빠름

<img src="https://user-images.githubusercontent.com/101415950/197551826-c1ad029c-920d-4d69-bc39-79f307d38411.png" width="80%" height="80%">
(출처 : https://www.alibabacloud.com/ko/knowledge/difference-between-container-and-virtual-machine)

#### <쿠버네티스(k8s) 정의>

- 쿠버네티스는 컨테이너 오케스트레이션(Orchestration)을 위한 솔루션

- 오케스트레이션은 복잡한 단계를 관리하고 요소들의 유기적인 관계를 미리 정의하여 손쉽게 사용하도록 서비스를 제공하는 것

- 즉 다수의 컨테이너를 유기적으로 연결, 실행, 종료 그리고 상태 추적 및 보존 등 컨테이너를 안정적으로 사용할 수 있게 만들어주는 솔루션

- 이와 비슷한 솔루션은 도커 스웜(소규모 환경에 유용), 메소스(분산 관리 시스템과 연동 필요), 노매드(Consul, Vault 연동)가 있음

#### <쿠버네티스(k8s) 구성 방법>

- 관리형 쿠버네티스
	
	- Public Cloud 업체에서 제공
	
	- EKS(Amazon Elastic Kubernetes Service), AKS(Azure Kubernetes Service), GKE(Google Kubernetes Engine)이 속함
	
	- 구성이 이미 다 갖춰져 있고 Master Node를 클라우드 업체에서 관리

- 설치형 쿠버네티스

	- Suse의 Rancher, RedHat의 Openshift와 같은 플랫폼에서 제공
	
	- 유료

- 구성형 쿠버네티스

	- 사용하는 시스템에 쿠버네티스 클러스터를 자동으로 구성해주는 솔루션
	
	- Kubeadm, kops(kubernetes Operations), KRIB(Kubernetes Rebar Integrated Bootstrap), kubespray가 있음
	
	- Kubeadm은 사용자가 변경하기 수월하고 온프레미스(On-premises)와 클라우드 모두 지원

	- kubespray는 실제 업무 환경에서도 매우 편리하게 쿠버네티스 클러스터를 자동으로 배포할 수 있는 도구

#### <쿠버네티스(k8s) 구성 요소>

- kubectl, kubelet, API 서버, 캘리코, etcd, 컨트롤러 매니저, 스케줄러, kube-proxy, 컨테이너 런타임, 파드 등

- 쿠버네티스 구성 요소는 동시에 여러 개가 존재하는 경우 Hash 코드를 삽입하여 중복된 이름 회피(예시 : calico-node-bf486의 bf486)

- 구성 요소의 이름을 직접 정할 수 있음

- 구성 요소에 문제 발견 시 다시 생성되는 특성을 가지는 파드로 이루어져 있어서 자동으로 이름을 지정하는 것이 관리 수월

- 아래 예시에서 coredns-5644d7b6d9-b4dz9의 5644d7b6d9은 레플리카셋(ReplicaSet)을 무작위 문자열로 변형하여 추가한 것

```
# --all-namespaces는 default(기본 namespaces) 외 모든 것을 표시
# kubectl get pods는 파드를 수집하여 출력

[root@m-k8s ~]#  kubectl get pods --all-namespaces
NAMESPACE     NAME                                       READY   STATUS    RESTARTS   AGE
kube-system   calico-kube-controllers-6bbf58546b-pmk78   1/1     Running   0          36m
kube-system   calico-node-bf486                          1/1     Running   0          31m
kube-system   calico-node-j9plc                          1/1     Running   0          22m
kube-system   calico-node-mnkgd                          1/1     Running   0          27m
kube-system   calico-node-xwxtc                          1/1     Running   0          36m
kube-system   coredns-5644d7b6d9-b4dz9                   1/1     Running   0          36m
kube-system   coredns-5644d7b6d9-jmsxh                   1/1     Running   0          36m
kube-system   etcd-m-k8s                                 1/1     Running   0          35m
kube-system   kube-apiserver-m-k8s                       1/1     Running   0          35m
kube-system   kube-controller-manager-m-k8s              1/1     Running   0          35m
kube-system   kube-proxy-5ltsx                           1/1     Running   0          22m
kube-system   kube-proxy-fzvsx                           1/1     Running   0          36m
kube-system   kube-proxy-gfsc8                           1/1     Running   0          31m
kube-system   kube-proxy-v8lxz                           1/1     Running   0          27m
kube-system   kube-scheduler-m-k8s                       1/1     Running   0          35m 
```

#### <쿠버네티스(k8s) 구성 요소간 통신 : 관리자나 개발자가 파드를 배포할 때>

- 관리자 or 개발자가 파드 배포 명령을 수행했을 때 실행되는 순서는 하기 그림과 같음

- 0 ~ 7번 : 기본 설정으로 배포된 쿠버네티스에서 이루어지는 통신 단계를 구분

- 10번대 : 선택적으로 배포하는 것들로 순서와 상관이 없음

<img src="https://user-images.githubusercontent.com/101415950/197653986-0e0c9c1f-f55d-4071-b344-d753e54be574.png" width="80%" height="80%">

- 0 : kubectl

	- 쿠버네티스 클러스터에 명령을 내리는 역할
	
	- 바로 실행되는 명령 형태인 binary로 배포되므로 Master Node에 있을 필요 없음
	  (kubectl이 어디에 있더라도 API 서버의 접속 정보만 있으면 어느 곳에서든 쿠버네티스 클러스터에 명령 가능)
	
	- 통상적으로 API 서버와 주로 통신하므로 API 서버가 위치한 Master Node에 구성할 수 있음

	- Worker Node에서 kubectl를 실행하기 위해 마스터 노드의 scp 명령으로 쿠버네티스 클러스터의 정보를 Worker Node로 받아와야 함
	  (쿠버네티스 클러스터의 정보를 kubectl이 알게 하기 위해)

- 1 : API 서버

	- 쿠버네티스 클러스터의 중심 역할을 하는 통로
	
	- 상태 값을 저장하는 etcd 등 여러 요소들이 API 서버를 중심으로 두고 통신
	
	- 회사에서 모든 직원과 상황을 관리하고 목표를 설정하는 관리자 역할

- 2 : etcd

	- etc 디렉터리(리눅스의 구성 정보를 가지고 있는 디렉터리)와 distributed(퍼트리다)의 합성어

	- 구성 요소들의 상태 값이 모두 저장되는 장소(etcd 외 다른 구성 요소는 상태 값을 관리하지 않음)
	
	- 회사의 관리자가 모든 보고 내용을 기록하는 노트
	
	- etcd의 정보만 백업되어있으면 긴급한 장애 상황에서도 쿠버네티스 클러스터 복구 가능
	
	- 분산 저장이 가능한 key-value 저장소이므로 복제하여 여러 곳에 저장해 두면 하나의 etcd에 장애가 발생해도 시스템 가용성 확보 가능

	- 멀티 마스터 노드 형태

- 3 : Controller Manager

	- 쿠버네티스 클러스터의 Object 상태 관리
	
	- Worker Node에서 통신 불량인 경우 상태 체크 및 복구는 Controller Manager에 속한 Node Controller에서 이루어짐

	- ReplicaSet Controller는 ReplicaSet에 요청받은 파드 갯수대로 파드 생성

	- EndPoint Controller는 서비스와 파드를 연결하는 역할

	-  Controller Manager에 소속된 다양한 상태 값을 관리하는 주체들이 각자의 역할 수행

- 4 : Scheduler

	- Node의 상태, 자원, 레이블, 요구 조건 등 고려하여 파드를 어떤 Worker Node에 생성할지 결정하고 할당하는 역할

	- 파드를 조건에 맞는 Worker Node에 지정하고, 파드가 Worker Node에 할당된 일정을 관리하는 역할

- 5 : kubelet

	- 파드의 구성 내용(PodSpec)을 받아 컨테이너 런타임으로 전달

	- 파드 내 컨테니어들이 정상적으로 동작하는지 모니터링

	- 파드의 생성과 상태 관리 및 복구 등 담당

	- kubelet에 문제 발생 시 파드가 정상적으로 관리되지 않음

- 6 : 컨테이너 런타임(CRI, Container Runtime Interface)

	- 파드를 이루는 컨테이너의 실행을 담당

	- 파드 내 다양한 종류의 컨테이너가 문제 없이 동작하게 하는 표준 인터페이스

- 7 : 파드(Pod)

	- 한 개 이상의 컨테이너로 단일 목적의 일을 수행하는 쿠버네티스 애플리케이션의 최소 단위

	- 웹 서버 역할을 할 수 있고 로그나 데이터를 분석하는 역할도 할 수 있음

	- 파드는 가상 머신과 달리 언제라도 죽을 수 있는 존재로 가정하고 설계되었기 때문에 여러 대안으로 디자인됨

	[컨테이너와 파드의 관계]   
	<img src="https://user-images.githubusercontent.com/101415950/197660830-bb278a36-0e2e-41dd-8f80-cb7cb04b1915.png" width="30%" height="30%">

- 11 : 네트워크 플러그인

	- 쿠버네티스 클러스터의 통신을 위해 구성해야 하는 요소

	- 일반적으로 CNI로 구성

	- CNI는 클라우드 네이티브 컴퓨팅 재단의 프로젝트로 컨테이너의 네트워크 안정성과 확장성을 보장하기 위해 개발

	- CNI에 사용할 네트워크 플로그인을 선택 시 구성 방식과 지원하는 기능, 성능이 각기 다르므로 사용 목적에 맞게 선택

	- CNI는 캘리코(Calico), 플래널(Flannel), 실리움(Cilium), 큐브 라우터(Kube-router), 로마나(Romana), 위브넷(WeaveNet), Canal이 있음

	- 캘리코(Calico)는 L3로 컨테이너 네트워크를 구성 / 플래널(Flannel)은 L2로 컨테이너 네트워크를 구성

	- 네트워크 프로토콜인 BGP와 VXLAN의 지원, ACL(Access Control List) 지원, 보안 기능 제공 등을 살펴보고 
	  필요한 조건을 가지고 있는 네트워크 플러그인을 선택할 수 있어서 설계 유연성이 높음

- 12 : CoreDNS

	- 클라우드 네이티브 컴퓨팅 재단에서 보증하는 프로젝트

	- 빠르고 유연한 DNS 서버

	- 쿠버네티스 클러스터에서 도메인 이름을 이용하여 통신하는 데 사용

	- 실무에서 쿠버네티스 클러스터를 구성하여 사용할 때, IP보다 DNS Name을 편리하게 관리해 주는 CoreDNS를 사용하는 것이 일반적임

#### <쿠버네티스(k8s) 구성 요소간 통신 : 사용자가 배포된 파드에 접속할 때>

- 1 : kube-proxy

	- 쿠버네티스 클러스터는 파드가 위치한 노드에 kube-proxy를 통해 파드가 통신할 수 있는 네트워크 설정
	
	- 실제 통신은 br_netfilter와 iptables로 관리   
	  (config.sh 파일에서 br_netfilter 커널 모듈을 적재하고 iptables를 거쳐 통신)

- 2 : 파드(Pod)

	- 이미 배포된 파드에 접속하고 필요한 내용을 전달받음

	- 대부분 사용자는 파드가 어떤 Worker Node에 위치하는지 신경쓰지 않아도 됨

#### <쿠버네티스(k8s) 구성 요소간 통신 : 파드 생명주기>

- 쿠버네티스의 가장 큰 장점은 쿠버네티스 구성 요소마다 하는 일이 명확하게 구분됨 => 마이크로서비스 아키텍처(MSA)와 연관

- 각자의 역할을 충실하게 수행하면 클러스터 시스템이 안정적으로 운영됨

- 역할이 나누어져 있어 문제 발생 시 어느 부분에서 문제가 발생했는지 디버깅하기 수월함

<img src="https://user-images.githubusercontent.com/101415950/197666301-6be225cc-8d55-46d8-801e-29d05d6206e2.png" width="80%" height="80%">


1. kubectl을 통해 API 서버에 파드 생성을 요청

2. API 서버에 전달된 내용이 있으면 API 서버는 etcd에 전달된 내용을 모두 기록하여 클러스터 상태 값을 최신으로 유지   
   => 각 요소가 상태를 업데이트할 때마다 모두 API 서버를 통해 etcd에 기록

3. API 서버에 파드 생성이 요청된 것을 Controller Manager가 인식하면 Controller Manager는 파드를 생성 후 API 서버에 전달   
   (아직 어떤 Worker Node에 파드를 적용할 지는 결정되지 않은 상태로 파드만 생성)

4. API 서버에 파드가 생성되었다는 정보를 Scheduler가 인식   
   Scheduler는 생성된 파드를 어떤 Worker Node에 적용할지 조건을 고려하여 결정 후 해당 Worker Node에 파드를 띄우도록 요청

5. API 서버에 전달된 정보대로 지정한 Worker Node에 파드가 속해 있는지 Scheduler가 kubelet으로 확인

6. kubelet에서 컨테이너 런타임으로 파드 생성을 요청

7. 파드 생성

8. 파드는 사용 가능한 상태가 됨

#### <쿠버네티스(k8s) 상태유지 방법>

- 쿠버네티스는 작업을 순서대로 진행하는 Workflow 구조가 아닌 선언적인(declarative) 시스템 구조를 가짐

- 각 요소가 추구하는 상태(desired status)를 선언하면 현재 상태(current status)와 비교 점검 후 추구하는 상태에 맞출려고 하는 구조

- 추구하는 상태를 API 서버에 선언하면 다른 요소들이 API 서버에서 확인하여 현재 상태와 비교하고 그에 맞게 상태를 변경

- API는 현재 상태 값을 가지고 있고 이것을 보존하므로 etcd가 필요, API서버와 etcd는 거의 한몸처럼 동작하도록 설계

- Work Node는 Workflow 구조에 따라 설계됨   
	
	- 쿠버네티스가 kubelet과 컨테이너 런타임을 통해 파드를 생성하고 제거 구조이므로 선언적인 방식으로 구조화 하기에 어렵기 때문
 	
	- 명령이 절차적으로 전달되는 방식이 시스템 성능을 높이는 데 효율적이기 때문
 
 - Master Node는 이미 생성된 파드들을 유기적으로 연결하므로 쿠버네티스 클러스터를 안정적으로 유지하기 위해 선언적인 시스템이 편리

<img src="https://user-images.githubusercontent.com/101415950/197680984-d017ee86-a748-4b9d-8371-579dc703b7b1.png" width="80%" height="80%">


#### <파드 생성 방법>

- 쿠버네티스를 사용한다는 것 = 사용자에게 효과적으로 파드를 제공한다는 뜻

- kubectl run 파드이름 : 파드생성

- kubectl create deployment 파드이름 : 파드생성(파드이름을 제외한 나머지 부분 해시코드로 무작위 생성)

- kubectl get pod : 파드 확인 (kubectl get pods -o wide : 파드에 대한 더 많은 정보 확인)

- curl ip주소 : ip주소의 웹 페이지 정보를 받아오는지 확인

```
[root@m-k8s ~]# kubectl run nginx-pod --image=nginx		#--image=(생성할 이미지 이름 or 이미지 경로)
pod/nginx-pod created						
[root@m-k8s ~]# kubectl create deployment dpy-nginx --image=nginx
deployment.apps/dpy-nginx created
```

- run으로 파드 생성 시 단일 파드 1개만 생성 (초코파이 1개)

- create deployment로 파드 생성 시 Deployment라는 관리 그룹 내 파드 생성 (초코파이 박스 내 초코파이 1개)

```
[root@m-k8s ~]# kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
dpy-nginx-7cd4d79cc9-xmv28  1/1     Running   0          50s
nginx-pod                    1/1     Running   0          87s 
```

<img src="https://user-images.githubusercontent.com/101415950/197715292-485c95d7-c8d6-4eef-89cd-d00318723b7a.png" width="40%" height="40%">

#### <오브젝트>

- 쿠버네티스를 사용하는 관점에서 파드(Pod)와 Deployment는 Spec과 상태 등의 값을 가지고 있음

- 오브젝트는 Spec과 상태 등 값을 갖는 파드(Pod)와 Deployment를 개별 속성을 포함해 부르는 단위

- 기본 오브젝트

	- 파드(Pod)
	
		- 쿠버네티스에서 실행되는 최소 단위(웹 서비스를 구동하는 데 필요한 최소 단위)
		
		- 독립적인 공간과 사용 가능한 IP를 가지고 있음
		
		- 하나의 파드는 1개 이상의 컨테이너를 갖고 있으므로 여러 기능을 묶어 하나의 목적으로 사용 가능
		
		- 범용으로 사용할 시 대부분 1개의 파드에 1개의 컨테이너를 적용

	- 네임스페이스(Namespace)
		
		- 쿠버네티스 클러스터에서 사용되는 리소스들을 구분해 관리하는 그룹

		- ex) default : 특별히 지정하지 않으면 기본으로 할당됨
		
		- ex) kube-system : 쿠버네티스 시스템에 사용됨
		
		- ex) metallb-system : 온프레미스에서 쿠버네티스 사용 시 외부에서 클러스터 내부로 접속하게 도와주는 컨테이너들이 속함

	- 볼륨(Volume)
		
		- 파드가 생성될 때 파드에서 사용할 수 있는 디렉터리 제공

		- 파드는 영속되는 개념이 아니고 제공되는 디렉터리를 임시로 사용
	
		- 파드가 사라지더라도 저장과 보존이 가능한 디렉터리를 볼륨(Volume)을 통해 생성 및 사용 가능
	
	- 서비스(Service)

		- 파드는 클러스터 내 유동적이므로 접속 정보가 고정적이지 않음

		- 파드 접속을 안정적으로 유지하도록 서비스를 통해 내/외부로 연결

		- 서비스는 파드가 생성될 때 부여되는 새로운 IP를 기존에 제공하던 기능과 연결해줌

		- 서비스는 쿠버네티스 외부에서 내부로 접속 시 내부 구조, 파드의 생존 여부를 신경쓰지 않아도 이를 논리적으로 연결하는 것
		
		- 기존 인프라에서 로드밸런서, 게이트웨이와 비슷한 역할

	<img src="https://user-images.githubusercontent.com/101415950/197724789-20739f8c-d7fd-4e6d-afa1-b76e2012d164.png" width="80%" height="80%">

#### <디플로이먼트(Deployment)>

- 기본 오브젝트만으로 쿠버네티스 사용 가능, 그러나 한계가 있어 이를 극복하기 위해 기능을 조합하고 추가한 것이 Deployment

- Deployment 이외에 데몬셋(DaemonSet), 컨피그맵(ConfigMap), 레플리카셋(ReplicaSet), PV(PersistentVolume), PVC(PersistentVolumeClaim),    
  스테이트풀셋(StatefulSet) 등이 있으며 목적에 맞는 오브젝트들을 추가하여 사용

- Deployment는 파드를 기반하며 ReplicaSet 오브젝트를 합친 형태

- 아래 그림은 Deployment 오브젝트 계층 구조를 나타냄

<img src="https://user-images.githubusercontent.com/101415950/197727218-4d9c3a04-5fd0-481f-b6f2-e15abfb22876.png" width="40%" height="40%">

- API 서버와 Controller Manager는 파드를 생성되는 것을 감시할 뿐만 아니라 Deployment와 같이 ReplicaSet을 포함하는 오브젝트 생성 감시

- 아래 그림은 API 서버와 Controller Manager의 통신을 나타냄

<img src="https://user-images.githubusercontent.com/101415950/197727795-eac86dd4-56e6-4e7d-860e-53175d77545d.png" width="40%" height="40%">


#### <NGINX 이미지>

- 컨테이너로 도커를 사용하므로 도커의 기본 저장소인 도커 허브에서 이미지를 가지고 옴 (https://hub.docker.com/_/nginx)

- 클라우드 서비스를 이용하고 있으면 기본 저장소 외 클라우드 서비스 업체에서 제공하는 저장소를 사용

- ex) 구글의 GCR(Google Container Registry), 아마존의 ECR(Elastic Container Registry), 마이크로소프트의 ACR(Azure Container Registry)

#### <ReplicaSet으로 파드 수 관리>

- 다수의 파드를 하나씩 생성한다면 비효율적이므로 쿠버네티스에서는 다수의 파드를 만드는 ReplicaSet 오브젝트를 제공

- 파드 3개 생성하겠다고 ReplicaSet에 선언하면 Controller Manager와 Scheduler가 Worker Node에 파드 3개를 만들도록 선언 

- ReplicaSet은 파드 수를 보장하는 기능만 제공

- 그러므로 Rolling 업데이트 기능 등이 추가된 Deployment를 사용하여 파드 수를 관리하기를 권장

- 아래 그림은 ReplicaSet으로 파드 수를 관리하는 과정(총 3개의 파드 상태로 변경됨)
<img src="https://user-images.githubusercontent.com/101415950/197747014-7e3c2f22-e486-4200-bca6-eedf34577057.png" width="60%" height="60%">

## 마크다운 언어 참조
https://gist.github.com/ihoneymon/652be052a0727ad59601
