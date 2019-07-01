require 'erb'

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/bionic64'
  config.vm.network 'forwarded_port', guest: 5432, host: 25432 # PostgreSQL
  config.vm.network 'forwarded_port', guest: 8000, host: 28000 # ORCA / ORCA API
  config.vm.provider 'virtualbox' do |vb|
    vb.cpus = 4
    vb.memory = 4094
  end
  config.vbguest.auto_update = true
  config.vm.synced_folder ".", "/home/vagrant/panda-sample2"
  config.vm.provision :shell, inline: ERB.new(<<~SHELL).result
    echo 'curl'
    curl -o /etc/apt/sources.list.d/jma-receipt-bionic51.list https://ftp.orca.med.or.jp/pub/ubuntu/jma-receipt-bionic51.list
    curl https://ftp.orca.med.or.jp/pub/ubuntu/archive.key | apt-key add -
    echo 'apt-get'
    apt-get update
    apt-get dist-upgrade -y
    apt-get install -y jma-receipt
    update-locale LANG=ja_JP.UTF-8
    echo 'tz'
    timedatectl set-timezone Asia/Tokyo
    cd /tmp
    echo 'special'
    wget http://ftp.orca.med.or.jp/pub/etc/install_modules_for_ftp.tgz
    tar xvzf install_modules_for_ftp.tgz
    cd install_modules_for_ftp
    sudo -u orca ./install_modules.sh
    echo "listen_addresses = '*'" >> /etc/postgresql/10/main/postgresql.conf
    echo 'host all all 0.0.0.0/0 trust' >> /etc/postgresql/10/main/pg_hba.conf
    service postgresql restart
    echo 'jma setup'
    jma-setup
    service jma-receipt start
    service jma-receipt stop
    service jma-receipt start
    echo 'jma passwd'
    if [ ! -f /etc/jma-receipt/passwd ]; then
      echo "ororor:$(md5pass ororor):" > /etc/jma-receipt/passwd
      chown orca:orca /etc/jma-receipt/passwd
      chmod 644 /etc/jma-receipt/passwd
      su orca - -c '/usr/lib/jma-receipt/bin/passwd_store.sh | nkf -w'
      service jma-receipt restart
      sleep 3
    fi
    su orca -c "/usr/lib/jma-receipt/scripts/tools/run_master_upgrade.sh | nkf -w" || true
    su orca -c "/usr/lib/jma-receipt/bin/jma-receipt-program-upgrade.sh | nkf -w" || true
  SHELL
end
