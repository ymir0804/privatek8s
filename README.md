# Private k8s Cluster 구축하기(With Virtual Box)

## AliExpress에서 산 서버 사용
- ubuntu 22.04    

### spec
- JINGSHA X99 D8
    - 14 core 28 Thread / 64 GB
    - 750TI
    - 1TB SSD


### 구성 정보 및 프로세스
- OS
    - ubuntu 22.04 Server
- Master
    - 10.0.2.15
    - 4Core 16GB
- Worker
    - 10.0.2.10, 11
    - 6Core 22GB


- 구성 프로세스
    - VirtualBox CLI 설치
    ```bash
    # Virtual Box 공식홈페이지를 통해 repository 구성
    sudo apt-get update
    sudo apt-get install -y virtualbox
    ```
    - VirtualBox Extension Pack 설치
    ```Bash
    wget https://download.virtualbox.org/virtualbox/6.1.50/Oracle_VM_VirtualBox_Extension_Pack-6.1.50.vbox-extpack
    VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-6.1.50.vbox-extpack
    ```
    - phpvirtualbox 설치
    ```bash
    adduser vbox
    usermod -aG vboxusers vbox
    apt install apache2 php libapache2-mod-php php-soap php-xml
    cd /var/www/html/
    git clone https://github.com/phpvirtualbox/phpvirtualbox.git -b vbox6.1-php8.0
    chown -R vbox:vbox ./phpvirtualbox/
    chmod -R 777 ./phpvirtualbox/
    ```
   - phpVirtualBox 사용 시 설정 부분
   ```php
   # config.php 파일
   /* var $username = vbox;
      var $password = vbox
      var $location = 'http://127.0.0.1:18083/';
    */
    #  endpoint/jqueryFileTree.php 파일
    /*
    *  Replace all occurrences of "count()" under the "if" statement by the "is_countable()".
    https://github.com/phpvirtualbox/phpvirtualbox/issues/330
    */
   ```


