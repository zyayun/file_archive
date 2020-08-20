jenkins

- Plugin
  - Generic Webhook Trigger Plugin (Webhook插件)
  - Deploy to container Plugin (部署容器插件)
  - Credentials Binding (凭证管理插件)
  - role-strategy （授权插件）
  - publish-over-ssh (ssh远程插件)

- 加速jenkins

  ```shell
  首先找到 default.json文件，然后替换该文件中的内容
  find / -name 'default.json
  sed -i 's/http:\/\/updates.jenkins-ci.org\/download/https:\/\/mirrors.tuna.tsinghua.edu.cn\/jenkins/g' /var/lib/jenkins/updates/default.json && sed -i 's/http:\/\/www.google.com/https:\/\/www.baidu.com/g' /var/lib/jenkins/updates/default.json
  ```


