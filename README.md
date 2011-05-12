Локално .mk огледало за Fedora/Centos/Rhel/Debian
=================================================

За огледалото
-------------

[mirror.cabletel.com.mk][1] е локално огледало за Fedora/Centos/Rhel/Debian. 

Серверот и интернет сообраќајот несебично го донира CableTEL Македонија. Човечките ресурси потребни за одржување на огледалото несебично ги донираат [CableTEL][2] и [Слободен софтвер Македонија][3]. Доколку имаш прашања околу огледалото може да прашаш на јавната [поштенска листа][4].

Доколку сакаш локално огледало за Ubuntu погледни [тука][5].

HW info:
    Локација:   Скопје, Македонија
    CPU:        XEON Dual-Core TODO: точен модел на процесорот
    RAM:        3GB
    HDD:        1TB
    LINK:       1Gbps

* TODO: Точен опис на сетапот со два сервери ова она.
* TODO: Некоја статистика тука може да дојде.


Убави сликички
--------------

* ![CableTEL](http://cabletel.com.mk/img/logo_cabletel.jpg)
* ![Слободен софтвер Македонија](http://slobodensoftver.org.mk/files/garland_2s.mk_logo_0.png)
* ![Debian](http://www.debian.org/Pics/openlogo-50.png)
* ![Centos](https://www.centos.org/themes/centos/images/centos_logo_45.png)
* ![Fedora](http://fedoraproject.org/static/images/fedora-logo.png)


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

Centos mirror
------------
Centos огледалото е достапно на [mirror.cabletel.com.mk/centos/][6] за i386 и x86_64 архитектура.

Пример yum.repo датотека за Centos 5.x кој го користи ова локално македонско огледало:

    [base]
    name=CentOS-$releasever - Base
    baseurl=http://mirror.cabletel.com.mk/centos/$releasever/os/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

    #released updates 
    [updates]
    name=CentOS-$releasever - Updates
    baseurl=http://mirror.cabletel.com.mk/centos/$releasever/updates/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

    #additional packages that may be useful
    [extras]
    name=CentOS-$releasever - Extras
    baseurl=http://mirror.cabletel.com.mk/centos/$releasever/extras/$basearch/
    gpgcheck=1
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

    #additional packages that extend functionality of existing packages
    [centosplus]
    name=CentOS-$releasever - Plus
    baseurl=http://mirror.cabletel.com.mk/centos/$releasever/centosplus/$basearch/
    gpgcheck=1
    enabled=0
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
    
    #contrib - packages by Centos Users
    [contrib]
    name=CentOS-$releasever - Contrib
    baseurl=http://mirror.cabletel.com.mk/centos/$releasever/contrib/$basearch/
    gpgcheck=1
    enabled=0
    gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5


Fedora mirror
------------
TODO


Debian mirror
-------------
TODO


[1]: http://mirror.cabletel.com.mk
[2]: http://www.cabletel.com.mk
[3]: http://www.slobodensoftver.org.mk
[4]: http://lists.softver.org.mk/mailman/listinfo/ossm-members
[5]: http://mirror.on.net.mk/ubuntu/
