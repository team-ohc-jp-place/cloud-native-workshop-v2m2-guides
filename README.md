The CCN Roadshow(Dev Track) Module 2 Guide 2019
===
このモジュールでは、OpenShift上でRed Hat Application Rumties(Quarkus, Spring Boot)を用いたクラウドネイティブアプリのCI/CDパイプラインを作成することができます。
また、開発者は Web IDE(CodeReady Workspace)を介してクラウドネイティブアプリをモニタリングし、デバッグする方法を学びます。

Agenda
===
* Advanced Cloud-Native Services
* Implementing Continuous Delivery
* Debugging Applications
* Application Monitoring

Lab Instructions on OpenShift
===

APB経由で lab infra をインストールした場合、 lab instructions はすでにデプロイされていることに注意してください。

ここでは、 lab instructions を OpenShift クラスタに手動でデプロイするための Ansible プレイブックの例を示します。


```
- name: Create Guides Module 2
  hosts: localhost
  tasks:
  - import_role:
      name: siamaksade.openshift_workshopper
    vars:
      project_name: "guide-m2"
      workshopper_name: "Cloud-Native Workshop V2 Module-2"
      project_suffix: "-XX"
      workshopper_content_url_prefix: https://raw.githubusercontent.com/RedHat-Middleware-Workshops/cloud-native-workshop-v2m2-guides/master
      workshopper_workshop_urls: https://raw.githubusercontent.com/RedHat-Middleware-Workshops/cloud-native-workshop-v2m2-guides/master/_cloud-native-workshop-module2.yml
      workshopper_env_vars:
        PROJECT_SUFFIX: "-XX"
        COOLSTORE_PROJECT: coolstore{{ project_suffix }}
        OPENSHIFT_CONSOLE_URL: "https://YOUR_OCP_MASTER_URL"
        ECLIPSE_CHE_URL: "http://che-labs-infra.YOUR_OCP_ROUTE_SUBFFIX"
        GIT_URL: "http://gogs-labs-infra.YOUR_OCP_ROUTE_SUBFFIX"
        NEXUS_URL: "http://nexus-labs-infra.YOUR_OCP_ROUTE_SUBFFIX"
        LABS_DOWNLOAD_URL: "http://gogs-labs-infra.YOUR_OCP_ROUTE_SUBFFIX"
         
      openshift_cli: "oc --server https://YOUR_OCP_MASTER_URL"
```
