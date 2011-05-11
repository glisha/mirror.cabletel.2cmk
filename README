2cmk & Cabletel mirror
======================

EPEL за centos/rhel
-------------------

За синхронизација на EPEL (екстра пакети за Centos/Redhat дистрибуции).

    rsync -vaH --include-from=include_epel.txt --numeric-ids --delete --delete-after --delay-updates rsync://ftp.sh.cvut.cz/epel/

Кои работи од upstream репозиториумот да ги синхронизира. Debug пакетите додаваат +30% на големина.

    # cat > include_epel.txt <<KRAJ
    - **/debug/*
    + /6/
    + /6/i386/
    /6/i386/** #~5GB
    /6/x86_64/ 
    /6/x86_64/** #~5GB
    /5/
    /5/i386/ 
    /5/i386/** #~5GB
    /5/x86_64/
    /5/x86_64/** #~5GB
    /RPM-GPG-KEY-EPEL
    /RPM-GPG-KEY-EPEL-6
    /testing/ 
    /testing/6/
    /testing/6/i386/
    /testing/6/i386/** #~1GB
    /testing/5/
    /testing/5/x86_64/
    /testing/5/x86_64/** #~600MB
    - *
    KRAJ

Пример yum.repo датотека за Centos5/Rhel5

    #cat > /etc/yum.repos.d/epelmk.repo <<KRAJ
    [epel]
    name=Extra Packages for Enterprise Linux 5 - $basearch 
    baseurl=http://mirror.cabletel.com.mk/epel/$releasever/$basearch
    enabled=1
    gpgcheck=1
    gpgkey=http://mirror.cabletel.com.mk/epel/RPM-GPG-KEY-EPEL

    [epel-testing]
    name=Extra Packages for Enterprise Linux 5 - Testing - $basearch 
    baseurl=http://mirror.cabletel.com.mk/epel/testing/$releasever/$basearch
    enabled=0
    gpgcheck=1
    gpgkey=http://mirror.cabletel.com.mk/epel/RPM-GPG-KEY-EPEL

или за RHEL6
    #cat > /etc/yum.repos.d/epel6mk.repo <<KRAJ
    [epel]
    name=Extra Packages for Enterprise Linux 6 - $basearch           
    baseurl=http://mirror.cabletel.com.mk/epel/$releasever/$basearch
    enabled=1
    gpgcheck=1
    gpgkey=http://mirror.cabletel.com.mk/epel/RPM-GPG-KEY-EPEL-6

    [epel-testing]
    name=Extra Packages for Enterprise Linux 6 - Testing - $basearch    
    baseurl=http://mirror.cabletel.com.mk/epel/testing/$releasever/$basearch
    enabled=0
    gpgcheck=1
    gpgkey=http://mirror.cabletel.com.mk/epel/RPM-GPG-KEY-EPEL-6

Fedora mirror
------------
TODO


