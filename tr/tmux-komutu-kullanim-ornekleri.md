---
title: "Tmux Komutu Kullanımı"
description: "Tmux komutu örnekleri. En sık kullanılan tmux komutları. Tmux kısa referans sayfası"
date: "2021-12-25"
cover: "/images/tmux-short-tutorial/cover.jpg"
language: "tr"
categories: 
    - Linux Komut Satırı Araçları
slug: "tmux-komutu-kullanim-ornekleri"
tags:
    - Linux
    - Quick
metaTags: Reçete, Kısa, Hızlı    
metaPhrases:
    - Tmux Kullanım Örnekleri
    - Tmux Kısa Örnekler
---

# Tmux Nedir?
**tmux** terminal multiplexer ifadesinin kısaltmasıdır. Bir komut satırı penceresi içinde birden fazla pencereyi veya tabı iç içe çalıştırmak için kullanılır.  

**tmux**'ın bir diğer kullanımı ise **ssh** uzerinden bağlanılan uzak bilgisayarlarda, çalıştırılması uzun süren komutları çalıştırmaktır. Unix tabanlı(Linux, Mac OSX, vb.) işletim sistemleri için tasarlanmıştır. **ssh** ile bağlandığınız bir makinede uzun bir komut çalıştırdıktan sonra sonucunu beklerken **ssh** bağlantınız kopabilir, bağlantınız koptuğu için çalıştırdığınız komut da işletim sistemi tarafından öldürülür. **tmux** bu gibi problemleri bertaraf etmenizi sağlayan çok faydalı bir araçtır.

**Tmux**, **ssh** bağlantısı yaptıgınız uzak bilgisayarda bir çeşit sunucu çalıştırır. Komutlarınız aslında bu sunucu tarafından sağlanan oturumlarda(session) yönetilir. Komutunuz calışmaya başlarken ssh bağlantınız kopsa bile bu oturumlar uzak bilgisayarda saklandığı için tekrar ssh bağlantısı kurup komutunuzun çalıştığı oturuma bağlanabilirsiniz.

## En sık kullanılan Tmux komut parametreleri:

- ### Açık tmux oturumlarını listele:
    ``` bash
    tmux ls
    ```

    Örnek Çıktı: 
    ``` bash
    ❯ tmux ls
    build_job: 1 windows (created Sat Dec 25 15:47:12 2021)
    copy_files: 1 windows (created Sat Dec 25 15:46:56 2021)
    ```


- ### **copy-files** isimli yeni bir oturum oluştur ve bu oturuma bağlan(attach):
    ``` bash
    tmux new -s copy_files
    ```

- ### Bağlı oldugun herhangi oturumla bağlantıyı kes(Oturum arka tarafta calışmaya devam eder. Tekrar bağlanabilirsiniz): 
    <kbd>Ctrl</kbd> + <kbd>b</kbd> + <kbd>d</kbd>

- ### Daha önce açılmış bir **build-job** isimli bir oturuma bağlan:
    ``` bash
    tmux a -t build_job
    ```

- ### Varolan bir oturumu öldür:
    Bunu yapmak için iki yöntem vardır:
    1) Eger oturumun içinde iseniz **exit** yazarak oturumu kapatabilirsiniz. 
    2) Eger oturumun dışında iseniz aşağıdaki komut ile oturumun ismini yazarak oturumu sonlandırabilirsiniz.
        ``` bash
        tmux kill-session -t oturum_adi        
        ```
 
 - ### Var olan tüm oturumları öldür:
    ``` bash
    tmux kill-session -a
    ```
    Bu komuttan sonra **tmux ls** komutunu çalıştırdığınızda boş liste döner.
    
