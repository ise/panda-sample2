# BLOB�Υ��åץ��ɤȥ�������ɤ��ץ����

���ɽ���� cobol/demo.png ��BLOBIMPORT���Ʋ��̤�ɽ�����롣
���θ�ϲ��̤��饢�åץ��ɤ��줿�ե������cobol/uploaded.png��BLOBEXPORT����(�ե�����˽񤭽Ф�)��

DB��monblob�ơ��֥��BLOBIMPORT��BLOBEXPORT���줿�ե����뤬��Ǽ����Ƥ��롣

* BLOBIMPORT
    * �ե������monblob�ơ��֥����Ͽ����
* BLOBEXPORT
    * monblob�ơ��֥�Υ쥳���ɤ�ե�����ؽ񤭽Ф�

## ����

```
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
```

## ���饤����ȵ�ư

```
$ glclient2
```

������: http://localhost:8000/rpc/
�桼��: sample
�ѥ����: sample
SSL����: �ʤ�

## �����н�λ

```
$ ./init stop
$ ./init clean
$ make clean
```
