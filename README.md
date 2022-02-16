Filebeat
=========

Эта роль устанавливает Filebeat  на указанные в Inventory хосты.

Зависимости
------------

Перед установкой Filebeat требуется установить Elasticsearch и Kibana, т.к. в шаблоне настройки сервиса прописывается IP хостов где установлены Elasticsearch и Kibana.

Настройка значений переменных
--------------
В файле default/main.yml указывается версия Kibana (filebeat_version) а также прописывается тип установки filebeat_install_type. Этой переменной регулируется нужно ли скачивать дистрибутив. Если да, то нужно указать remote, если нет, то другое значение, но при этом нужно будет скачать файл в каталог /files.

В основном плейбуке хосты Elasticserach должны быть в группе с названием el-instance, а хосты Kibana в kib-instance, иначе нужно будет изменить шаблон в /templates/filebeat.yml.j2


Пример Playbook
----------------

    - name: Install Filebeat
      hosts: filebeat
        roles:
        - filebeat_role

License
-------

BSD