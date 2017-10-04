# 社内勉強会資料

## はじめに

ドキュメントビルダーのSphinx,mkdocsを知ってもらうための資料

## 使い方

以下のコマンドで、Vagrantの起動とログインをする

```shell
vagrant up
vagrant ssh
```

## python2.7

```
sudo yum update -y
sudo yum install -y wget
mkdir -p /vagrant-data/tool/pip
cd $_
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
sudo pip install virtualenvwrapper
```

```
vi ~/.bash_profile

### add s
### Virtualenvwrapper
if [ -f /usr/bin/virtualenvwrapper.sh ]; then
    export WORKON_HOME=$HOME/.virtualenvs
    source /usr/bin/virtualenvwrapper.sh
fi
### add e
```

```
source ~/.bash_profile
```

## Sphinxの入れ方

```
mkvirtualenv --python=/usr/bin/python2.7 sphinx
pip install sphinx
```

## mkdocsの入れ方

```
mkvirtualenv --python=/usr/bin/python2.7 mkdocs
pip install mkdocs
```
