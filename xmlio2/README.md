# XMLIO2�ƥ��ȥץ����

POST�᥽�åɤ����Ϥ��줿xml�򤽤Τޤ��֤�API

## ����

���쥻���
  $ sudo service jma-receipt stop

�ӥ��
  $ make

PostgreSQL�桼������(identǧ�ڤ��뤿�������桼����Ʊ̾)
  $ sudo -u postgres createuser -d $USER

DB����(panda�ѥ����������꤬���줿DB��������ϰʹߥ����åײ�ǽ)
  $ createdb pandatest

panda�ѥ�����������
  $ /usr/lib/panda/bin/monsetup -dir directory

## �����е�ư

$ ./init start

## POST

http://localhost:8000/test1/test1

�ʲ��Υ��ޥ�ɤǥꥯ�����Ȥ�ȯ�ԤǤ��롣

% ruby post_xml.rb
% ruby post_json.rb


## �����н�λ

$ ./init stop
$ ./init clean
$ make clean

