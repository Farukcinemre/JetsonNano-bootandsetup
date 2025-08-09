# JetsonNano-bootandsetup
## JETSON NANO SIFIRLAMA

Jetson Nano ‘ya sıfırlama yapılması için bilgisayara sanal bilgisayar kuruyoruz ve bu sanal bilgisayara Ubuntu Linux işletim sistemi kuruyoruz(Şekil 1). 


**Not:** Ubuntu 18.04 versiyonu olan işletim sistemi indirilmelidir. Aksi halde başka versiyonlarda çalışmaz. 

Sanal bilgisayar indirme linki :  [1] https://releases.ubuntu.com/18.04/

![Ubuntu İSO dosyası ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ubuntu%20versiyon%2018.04%20indirme.png)

                                                              Şekil 1

Ubuntu indirildikten sonra sanal makineye Nvidia SDK Manager indirilmesi gerekir(şekil 2). Aşağıdaki linkten indirin. İndirme yaparken aşağıdaki resimde de görüldüğü gibi “.deb Ubuntu “yazan kısma tıklayıp indirmelisiniz. İndirirken sizden üyelik istiyor üye olun ya da hali hazırda bir üyeliğiniz varsa giriş yapmanız yeterlidir. Eğer üye olmazsanız ya da giriş yapmazsanız uygulamayı yükleyemezsiniz. 

  Link:  [2] https://developer.nvidia.com/drive/sdk-manager
  
  ![Nvidia SDK Manager indirme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20jetson%20nano%20indirme.png)
  
                                                              Şekil 2
  
Daha sonra Ubuntu Linux’ta yükleme yapabilmek için dosyanın indirildiği yere gelip terminal açıyoruz.

     $sudo dpkg -i nvidiasdkmanager.deb 
     
Bu kodu çalıştırıyoruz. Eğer yüklemede hata veriyorsa 

     $sudo apt  --fix-broken install 
          
Bu kodu çalıştırıyoruz. Bunu yaptıktan sonra tekrar “$ sudo dpkg -i nvidiasdkmanager.deb “kodunu tekrar denediğinizde çalışacaktır.

Daha sonra Nvidia SDK Manager uygulamasını açıyoruz Aşağıdaki resimdeki gibi bir ekran geliyor. “ logging in “ kısmından tekrar giriş yaptıktan sonra (Şekil 3)uygulama arayüzü açılıyor. 

![Nvidia SDK Manager login ekranı](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20log%20in%20ekran%C4%B1.png)

                                                               Şekil 3

Aşağıdaki ekrandaki gibi arayüz ekranı geliyor. Burada “Target Hardware” başlıklı kısımı seçip oradan elimizdeki Jetson Nano modeli ne ise onu seçmek gerekir(Şekil 4).

![Jetson Nano Model seçim ekranı](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri%20se%C3%A7im%20ekran%C4%B1%20.png)

                                                               Şekil 4

Jetson Nanoyu seçtiğimizde “ADDITIONAL SDKS” kısmında sadece DeepStream deki tik işaretine basıp işaretliyoruz ve 2.adıma geçiyoruz.

![Nvidia SDK 2.adım ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/download%20ve%20install%20ekran%C4%B1.png)

                                                               Şekil 5

2.Adıma geçtiğimizde ise yükleme yapmadan önce bizden privacy policy kabul etmemizi söylüyor. Ve onun yanındaki “Download now. İnstall later“ Seçeneğine tıklarsanız Nvidia Jetson Nano için gerekli olan dosyaları indirir yüklemeyi kendiniz indirdikten sonra yaparsınız eğer o seçeneği işaretlemeden ilerlerseniz direkt download ve install’u yapar(Bu işlem uzun sürebilir)(Şekil 5). Download ve install devam ederken  aşağıdaki karşımıza resimdeki ekran geliyor. Oradaki “ Automatic Setup -Jetson nano” seçeneği işaretli olacak ekranda görüldüğü üzere “Manual Setup” seçeneğini seçmelisiniz(Şekil 6).	 

![Manuel Setup Ekrani](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/manuel%20setup%20jetson%20nano.png)

                                                                Şekil 6

Bunu seçtiğiniz zaman sizden Jetson Nano’nun yeni kullanıcı adı ve şifresini girmenizi isteyecektir. Bunları girdikten sonra finish e tıklayın. Download ve install işlemi devam edecektir.

Yüklemeye devam ederken karşınıza aşağıdaki gibi bir ekran çıkacak (SDK components yükleme ekranı)(Şekil 7). Bu ekran Jetson Nano’da görüntü işleme, derin öğrenme ile ilgili çalışma yapmak istiyorsanız o çalışmalar için gerekli olan yazılımları  (CUDA, CUDA X-AI, OPENCV vb.) Jetson Nano’ya yüklemenizi sağlıyor. Burada yazılımları Jetson Nano’ya yüklemeniz için iki seçeneğiniz var

![Jetson Nano SDK components yükleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20paketleri%20y%C3%BCkleme%20.png)

                                                                 Şekil 7

**1.Seçenek:** İsterseniz resimde de gördüğünüz gibi connection olarak USB’den yükleme yapabilirsiniz. Yani sanal bilgisayar Jetson Nano ile USB üzerinden köprü bağlantı kurup kendi içindeki interneti Jetson Nano’nun da kullanmasını sağlayacak. Eğer USB’den bağlantı yapıp install edecekseniz IP kısmını değiştirmemeniz gerekir.

**2.seçenek:** İsterseniz connection olarak ethernet seçebilirsiniz ve Jetson Nano’ya bir USB wifi adapter bağlayıp onun IP’sini yazıp install'a tıklayıp yüklemesini beklemelisiniz.

Bu yükleme bittiğinde Jetson Nano’ya derin öğrenme için gerekli olan bazı dosyalar yüklenmiş olacak.

Bu işlem bittikten sonra Jetson Nano kendiliğinden açılacaktır. Jetson Nano ‘nun ekranını görebilmek için bir monitör kullanmanız gerekir. Monitöre bağladığınızda giriş ekranı önünüze çıkacak. Kullanıcı adı ve şifrenizi girerek giriş yapabilirsiniz.

Siz bu işleme install yapmadan skip düğmesine basıp geçerseniz yukarıda bahsettiğim yazılımları manuel olarak yani Jetson Nano’nun terminalinden tek tek yüklemeniz gerekecektir.

Tek tek yüklemek için gereken kodlar: [3] https://github.com/55selcukozdemir/web_self-car/blob/main/README.md

Linkte derin öğrenme için gerekli kütüphaneleri adım adım nasıl yüklemeniz gerektiği anlatılıyor. Adım adım işlemleri takip ettiğinizde kütüphaneleri yüklemiş olacaksınız.

![Jetson Nano Modelleri](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri.png)

                                                                   Şekil 8 

Yukarıdaki resimde de görüldüğü gibi(Şekil 8) Jetson Nano’nun 3 modeli vardır ve bu modeller Jetson Nano, Jetson Nano (developer kit), Jetson Nano (2 gb developer kit version) 

Jetson Nano’nun sdcard destekli modeline sahipseniz 64GB hafızaya sahip bir sdcard bağlarsanız derin öğrenme için gerekli kütüphaneleri yüklemek için yeterli alanınız olmuş olur.

Eğer Jetson Nano’nun sdcard desteği olmayan 4GB ram 16GB dahili hafızası olan modeline sahipseniz bu depolama alanı sizin için yeterli olmayacaktır. Bu nedenle harici başka bir depolama cihazıyla (harddisk, SSD, flash bellek) Jetson Nano’yu çalıştırmanız gerekecektir. Eğer flash bellek ile boot etmeyi denerseniz flash bellek ne kadar hızlı olursa olsun okuma yazma oranı düşük kalacağı için işlemler çok yavaş gerçekleşecektir. Harddiskte kullanırsanız aynı şekilde hızı sizi tatmin etmeyecektir. Burada en mantıklı tercih SSD olacaktır.   

# SSD'den Boot Etme
Yararlandığım video linki: [4]https://youtu.be/53rRMr1IpWs

SSD den boot edebilmemiz için github linkini kopyalıyoruz.

     $ git clone https://github.com/JetsonHacksNano/bootFromUSB.git
     
Daha sonra yüklediğimiz github klasörüne giriş yapıyoruz

     $ cd bootFromUSB
     
![Jetson Nano diskler](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/diskler.png)

                                                                       Şekil 9

Jetson Nano’yu boot edileceğinden SSD ‘nin formatlanması gerekir(Şekil 9). Resimde gördüğünüz gibi arama kısmına “disks” yazıp ilk çıkana tıklıyoruz(Şekil 10).

![Jetson Nano SSD ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ssd.png)

                                                                       Şekil 10

esimdeki gibi SSD’yi seçip sağ üstteki 3 çizgi olan kutucuğu seçiyoruz. Format disk’e tıklıyoruz (Şekil 11) ve Partitioning kısmını GPT olan kısım ile değiştiriyoruz (Şekil 12). Daha sonra format a tıklıyoruz ve tekrar formata tıklıyoruz(Şekil 13).

![Jetson Nano format disk](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/format.png)

                                                                       Şekil 11

![Jetson Nano format GPT](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/GPT.png)

                                                                       Şekil 12

![Jetson Nano format onay](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/areyousure.png)

                                                                       Şekil 13

Bu işlemleri yaptıktan sonra SSD formatlanmış oluyor. İşlem bittikten sonra resimdeki gibi “+” kısmına basıp disk bölümü yapıyoruz(Şekil 14).

![SSD disk bölme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/%2Bssd.jpg)

                                                                       Şekil 14

"+" kısmına tıkladıktan sonra SSD yi bölüyoruz(Şekil 15).Daha sonra SSD diskine isim veriyoruz. Burada “Type” kısmında “Internal disk for use with Linux systems only (Ext4)” bu seçeneği işaretliyoruz. Sonra “Create” e tıklayarak ilerliyoruz ve SSD diskin bölümlenmesini yapılmış oluyor(Şekil 16).

![SSD bölümleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/disk%20b%C3%B6lme.png)

                                                                       Şekil 15

![SSD disk format](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ext4.png)

                                                                       Şekil 16

aşağıdaki Komutu kullanarak SSD diski kontrol edebiliyoruz.

     $ ls /dev/sda* 

SSD diski boot edebilmemiz için diske sistem dosyalarının yüklenmesi gerekir.Bilgisayarda  flash ile boot etmek gibi düşünebilirsiniz. 

     $ ./copyRootToUSB.sh -p /dev/sda1 
                
Bu komutu kullanarak SSD’ye sistem dosyalarını kopyalıyoruz. Daha sonra SSD’ye girip boot/extlinux klasörünün giriyoruz. Klasör içerisinde terminal açıyoruz.

     $ sudo cp extlinux.conf extlinux.conf.original

Burada extlinux dosyalarını kopyalıyoruz.

     $ sudo gedit extlinux.conf 
     
bu komutla birlikte extlinux dosyasının içine giriyoruz(Şekil 17).

![Extlinux config dosyası](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/extlinuxconfig.png)

                                                                       Şekil 17

Resimdeki işaretlenen bölgeyi kopyalayıp altına yapıştırıyoruz ve yapıştırılan kısımdaki “primary” kısmına sdcard yazıyoruz(Şekil 18).

![Extlinux sdcard](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sdcard.png)

                                                                       Şekil 18

SSD’den boot etmek istiyorsak root kısmını değiştirmemiz gerekir.Root kısmına SSD’nin sistem dosyalarının olduğu adresi yazmamız gerekir.

     $ ./partUUID.sh 
     
Bu komutu kullanarak SSD’deki sistem dosyalarının adresini bulabiliyoruz(Şekil 19).

![Jetson SSD adres](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/partuuid.png)

                                                                      Şekil 19 

Buradaki “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1” kısmını kopyalıyoruz ve extlinux içerisindeki primary kısmında bulunan root kısmına yapıştırıyoruz(Şekil 20).

![SSD root](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/root.png)

                                                                      Şekil 20

**Not:** Tırnak içinde belirtilen ifade “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1” kısmı özel bir kısımdır bu kısım sizde farklı olacaktır. Buna dikkat etmek gerekir. Yapılacak işlemlerde değişiklik yoktur.

Daha sonra extlinux dosyasını ctrl+s ile kaydedip dosyayı kapatıyoruz.

Buradan sonraki kısımda gidişat değişiyor bu nedenle bu kısmı ikiye ayırarak anlatmanın daha sağlıklı olduğunu düşünüyorum.

**1.Jetson Nano sdcard destekli ise**
Eğer sizde bulunan Jetson Nano sdcard destekliyse Jetson Nano’yu kapatıyoruz ve açmadan önce sdcard’ın takılmadığından emin olup Jetson Nano’yu açıyoruz.

     $lsblk
     
![Boot kontrol etme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/lsblk.png)

                                                                      Şekil 21

Terminali açıp yukardaki kodu yazıyoruz ve Eğer sda1 kısmında part’ın yanındaki kısımda sadece “/” varsa başarıyla boot edilmiş demektir(Şekil 21).

 **2.Jetson Nano sdcard destekli değilse**
 
Eğer sizde bulunan Jetson Nano sdcard destekli değilse Jetson Nano kendi dahili hafızası üzerinden sistemi boot ettiğinden dolayı Jetson Nano’nun bütün sistem dosyalarını siliyoruz. Bir süre sonra Jetson yanıt vermeyecek ve kapanacak daha sonra SSD takılı bir şekilde çalıştırdığımızda SSD’den boot etmiş olacaktır. yine aynı şekilde kontrol etmek için “$lsblk” ya girip sda1 kısmının  “/” bu şekilde olup olmadığını kontrol etmeniz gerekir.

# JETSON NANO YOLOV5 KURULUMU

Yararlandığım youtube linki: https://youtu.be/oKaLyow7hWU

Yolov5 github dosyalarını kopyalıyoruz.

     $ git clone https://github.com/ultralytics/yolov5.git
    
İndirdiğimiz yolov5 dosyasının içine giriyoruz ve requirements.txt 
dosyasına girdiğimizde yolov5’i çalıştırmak için hangi kütüphanelerin kurulması gerektiğini görüyoruz.

İhtiyacımız olan kütüphaneler yukarıdaki resimden de görüyorsunuz. Buradaki kütüphaneleri bir bir indireceğiz ancak burada opencv versiyonu 4.1.2 olarak gösteriyor ama biz 4.1.1 indireceğiz ve pip kullanmadan indireceğiz. Jetson Nano da gpu (ekran kartı) opencv’yi CUDA ile çalıştırdığımızda performansı en üst düzeye çıkarmış olacağız.
Normalde SDK Manager’dan SDK Components bölümünü install ettiyseniz opencv yüklemenize gerek yoktur ancak yüklemediyseniz bu durumda internetten yüklemeniz gerekir.

**1.Adım: OPENCV yükleme**

**Not:** Eğer opencv’yi nvidia SDK Manager’dan Jetson Nano’ya yükleme yapmışsanız bu adımı atlayabilirsiniz.

Opencv dosyalarını kopyalıyoruz

     $git clone https://github.com/JetsonHacksNano/buildOpenCV.git
     
Dosya yüklendikten sonra “buildopencv” dosyasının içine giriyoruz. Orada bulunan  “$NUM_JOBS” kısmını 1 yaparak değiştiriyoruz(eğer Jetson Nano modeliniz sd card destekliyse değiştirme yapmayın)(Şekil 22)

![OPENCV num jobs](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_jobs.png)

                                                                      Şekil 22

Bu işlemleri yaptıktan sonra dosyayı kaydedip çıkıyoruz.

Terminal açıp buildOPENCV dosyasına giriyoruz.

     $ cd buildOPENCV

Sonra aşağıdaki komutu çalıştırarak opencv’yi yüklüyoruz. 

     $ ./buildOPENCV 

**2.Adım:Diğer kütüphaneleri yükleme**

masaüstüne terminal açıp python3-pip dosyasını yüklüyoruz.

     $ sudo apt install python3-pip
     
PyYAML==5.3.1’i kuruyoruz

     $ pip3 install -U PyYAML==5.3.1
     
Tqdm kuruyoruz   

     $ pip3 install tqdm 
     
Cython kuruyoruz.

     $ pip3 install cython 
     
Numpy kuruyoruz.

     $ pip3 install -U numpy==1.18.5
     
Ptyhon APİ dosyalarını kuruyoruz.

     $ sudo apt install build-essential libssl-dev python3-dev
     
Cycler kuruyoruz.

     $ pip3 install cycler==0.10
     
Kiwisolver kuruyoruz.

     $pip3 install kiwisolver==1.3.1
     
Pyparsing kuruyoruz.
    
    $ pip3 install pyparsing==2.4.7
     
Python-dateutil kuruyoruz.

    $pip3 install Python-dateutil==2.8.2
    
Matplotlib kuruyoruz.

     $pip3 install  --no-deps matplotlib==3.2.2
     
 Gfortran kuruyoruz.
 
      $sudo apt install gfortran 
      
Libopenplas kuruyoruz.   

     $sudo apt install libopenblas-dev 
     
Liblapack-dev kuruyoruz.
 
     $sudo apt install liblapack-dev 
     
Scipy kuruyoruz.

     $pip3 install scipy==1.4.1
     
Libjpeg-dev kuruyoruz.

     $sudo apt install libjpeg-dev 
     
Pillow kuruyoruz.

     $pip3 install pillow==8.3.2
     
Typing-extensions kuruyoruz.

     $pip3 install typing-extensions==3.10.0.2
     
**3.Adım: Torch kütüphanesini yükleme**

Jetson Nano’nun ARM tabanlı işlemci mimarisinden olduğundan dolayı windowstaki gibi torch’un sitesine girip yükleme söz konusu değildir. Daha farklıdır. Torch yüklerken bir de Torchvision yüklememiz gerekir(Şekil 23).

Nvidia’nın forum sitesinde Torch kütüphanesini nasıl yükleyeceğinize dair 
Sitenin linki:
[6]https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

![Torch setup](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/torchvision.png)

                                                                       Şekil 23

Resimde de gördüğünüz gibi Torch’un versiyonları mevcut. Burada  installation kısmına tıkladığınız zaman hangi Torch’un komutlarla adım adım yüklendiğini göstermektedir. Vertification kısmı ise yüklediğimiz Torch ve Torchvision dosyalarını kontrol etmek için kullanılır(Şekil 24).

![Python3.6 ve torchvision](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/python%20torchvision.png)

                                                                      Şekil 24

Burada installation’a girdiğimizde Torch’u indirmek için kodlar bulunuyor. Biz Python 3.6 için oluşturulan kod dizinini kullanacağız ve  Torch’un 1.10 sürümünü kuracağız.

![Torch .whl dosyası](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/whl%20dosyas%C4%B1.png)

                                                                      Şekil 25

Resimde de görüldüğü üzere pyhon3.6 için Torch 1.10’u indirmek için “torch-1.10.0-cp36-cp36m-linux_aarch64.whl” dosyasını kullanmamız  gerekir(Şekil 25).

Terminale girip aşağıdaki kodu çalıştırıyoruz.

     $wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O  torch-1.10.0-cp36-cp36m-linux_aarch64.whl 
     
 python3-pip paket dosyalarını yüklüyoruz.
 
      $sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev
      
Pip komutunu kullanarak “.whl” uzantılı dosyayı yüklüyoruz.

     $ pip3 install  --no-deps torch-1.10.0-cp36-cp36m-linux_aarch64.whl
     
Torch’un yüklenmesi için Torchvision’ın da yüklenmesi gerekir.Torchvision yüklemek için yukarıdaki resimdeki kodları kullanıyoruz.

İlk önce gerekli kütüphaneleri yüklüyoruz.

     $sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
     
     $ git clone --branch v0.11.1 https://github.com/pytorch/vision torchvision       
     
Burada Torch’un hangi sürümünü yüklüyorsanız karşısında Torchvision’ın hangi versiyonu yüklenmesi gerektiği yazılıdır.

Biz Torch'un 1.10 versiyonunu yükleyeceğimizden kodda  <version> yerine v0.11.1 yazılması gerekir.

Kodu bu şekilde düzenledikten sonra çalıştırıyoruz.

     $ git clone --branch v0.11.1 https://github.com/pytorch/vision Torchvision  
     
Yükleme işlemi bittikten sonra Torchvision klasörünün içine giriyoruz

     $ cd torchvision
     
Build edeceğimiz 0.9.0 versiyonu seçiyoruz.

    $ export BUILD_VERSION=0.9.0
    
Pyhon3 ile setup dosyasını yüklüyoruz.

    $ python3 setup.py install  --user

Seaborn’u yüklüyoruz.

     $pip3 install  --no-deps seaborn==0.11.0
     
Yolov5 klasörün içine giriyoruz 

     $cd yolov5
     
Python kodu ile detect.py dosyasını çalıştırarak /data/images klasöründeki resimleri yolov5 ile test ediyoruz.

     $python3 detect.py --source  data/images --weights yolov5s.pt 
     
![Resim test sonucu](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sonu.png)     
  
                                                                       Şekil 26

Yolov5 başarılı bir şekilde resimdeki sonuçları vermeyi başardı.Hazır olarak eğitilen yolov5s.pt modeli insanları ve otobüsü doğru bir şekilde tanımladı(Şekil 26).

Jetson Nano’da gerçek zamanlı görüntü işleme yapmak için realsense kütüphanesini yüklememiz gerekir.

İlk olarak githubdaki dosyaları kopyalıyoruz.

     $ git clone https://github.com/jetsonhacks/installRealSenseSDK.git
     
Sonra klasörün içine giriyoruz   

     $cd installRealSenseSDK
     
“buildLibrealsense” dosyasını texteditor ile açıyoruz 

![Num proc dosyası](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_proc.png)

                                                                       Şekil 27  
  
Resimde de görülen “$NUM_PROCS” yazısını silip yerine 1 yazıyoruz(Şekil 27).

Daha sonra buildLibRealsense dosyasını çalıştırıyoruz

     $./buildLibRealsense.sh
     
Yükleme bittikten sonra kütüphanenin yüklenip yüklenmediğini kontrol etmemiz gerekir.

Python’u açıyoruz
 
     $python3  
     
Kütüphaneyi import ediyoruz

     $import pyrealsense2
     
Eğer hata vermeyip bir alt satıra geçmişse yüklenmiş demektir.

![Pyrealsense Hata](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense.png)

                                                                       Şekil 28
  
Eğer resimdeki gibi hata vermişsse(Şekil 28) python’un path’ini değiştirmek gerekir.Python’un realsense kütüphanesinin path’ini bulmak gerekiyor.

Pyrealsense2 kütüphanesi /usr/local/lib/python3.6/pyrealsense2 klasöründe bulunuyor.

Home klasörüne gelip üç çizgiye tıklayıp “show hidden files” seçeneğini işaretliyoruz ve .bashrc klasörüne tıklayıp texteditor ile giriş yapıyoruz.

![Pyrealsense PATH](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pythonpath.png)

                                                                      Şekil 29
  
Resimde de görüldüğü gibi /usr/local/lib olan yeri /usr/local/lib/python3.6/pyrealsense2 olarak değiştirip kaydediyoruz(Şekil 29).

Aşağıdaki komutu kullanıyoruz.

     $source ~/.bashrc
     
Python3’ü çalıştırıp kütüphaneyi kontrol ediyoruz.

     $python3 
     
     $ import pyrealsense2 as rs

![Pyrealsense Python](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense2.png)

                                                                     Şekil 30  
        
Eğer bu şekilde alt satıra geçiyorsa işlemi başarıyla tamamlamışsınız demektir(Şekil 30).

Sonra libcanberra-gtk dosyasını kuruyoruz

     $sudo apt install libcanberra-gtk*
     
Ve yolov5 için kurulacak olan kütüphaneleri tamamlıyoruz.

**Kamera ile Test**

Yolov5 dosyasının içine giriyoruz.

Terminal açıp gerçek zamanlı test için gereken komutu yazıyoruz ve çalıştırıyoruz.

     $ python detect.py --weights yolov5s.pt --source 0    
     
".pt" uzantılı dosyada eğitilen model bulunur. Eğer yolov5'in hazır olarak sunduğu "yolov5s.pt" dosyasını çalıştırırsanız varsayılan olarak eğitilmiş modelleri (insan,bilgisayar,telefon vb.)   test etmiş olursunuz.

Biz Teknofest Tarımsal İnsansız Aracı CORE takımı olarak yarışma gereği olarak yabancı bitki tanıması yapmamız gerekiyor.Bu nedenle ".pt" dosyasında değişiklik yapıp sadece yabancı bitkiyi görmesi ve ilaçlaması gerektiğinden dolayı yabancı bitkiyi eğiterek bitkinin tanımlanmasını sağladık(Şekil 31).

![Yabancı Bitki test sonucu](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/yabanci-bitki.jpg)
  
                                                                     Şekil 31


# Kaynakça

[1]https://releases.ubuntu.com/18.04/

[2] https://developer.nvidia.com/drive/sdk-manager
https://youtu.be/0nplGFQ07po

[3]https://github.com/55selcukozdemir/web_self-car/blob/main/README.md

[4] https://youtu.be/53rRMr1IpWs 

[5] https://youtu.be/oKaLyow7hWU

[6]https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048



🚀 Jetson Nano Boot and Setup Guide 🌟
Welcome to the ultimate guide for resetting, configuring, and optimizing your Jetson Nano for deep learning tasks! This comprehensive tutorial walks you through the process of setting up your Jetson Nano, booting from an SSD, and installing YOLOv5 for real-time image processing. Whether you're a beginner or an experienced developer, this guide is designed to make your Jetson Nano journey smooth and successful. Let's dive in! 🎉

🔄 JETSON NANO RESET
To reset your Jetson Nano and prepare it for deep learning, we’ll set up a virtual machine on a computer and install Ubuntu Linux (Figure 1). This is the foundation for a clean and efficient setup.

⚠️ Important Note: You must download Ubuntu 18.04, as other versions are not compatible with the Jetson Nano.

Download Link: [1] https://releases.ubuntu.com/18.04/

![Figure 1: Downloading Ubuntu 18.04 ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ubuntu%20versiyon%2018.04%20indirme.png)

Once Ubuntu is installed, download the Nvidia SDK Manager on the virtual machine (Figure 2). Visit the link below and select the “.deb Ubuntu” option as shown in the image. You’ll need to sign up or log in to Nvidia’s website to proceed—without an account, the installation won’t work.
Link: [2] https://developer.nvidia.com/drive/sdk-manager

![Figure 2: Nvidia SDK Manager Download](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20jetson%20nano%20indirme.png)
Navigate to the download directory in Ubuntu, open a terminal, and run:
$ sudo dpkg -i nvidiasdkmanager.deb

If you encounter an error, fix it with:
$ sudo apt --fix-broken install

Then retry the dpkg command—it should work seamlessly now.
Launch the Nvidia SDK Manager. You’ll see a login screen (Figure 3). After logging in, the intuitive interface will appear.

![Figure 3: Nvidia SDK Manager Login](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20log%20in%20ekran%C4%B1.png)
In the interface, select your Jetson Nano model under the “Target Hardware” section (Figure 4). Choosing the correct model is crucial for compatibility.

![Figure 4: Selecting Your Jetson Nano Model](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri%20se%C3%A7im%20ekran%C4%B1%20.png)

After selecting your model, check the box for DeepStream under “ADDITIONAL SDKS” and proceed to Step 2 (Figure 5).

![Figure 5: DeepStream Selection ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/download%20ve%20install%20ekran%C4%B1.png)
In Step 2, accept the privacy policy. You have two options:

Download now. Install later: Downloads the files for manual installation later.
Direct Download and Install: Installs immediately (this may take some time).

During installation, choose Manual Setup instead of “Automatic Setup - Jetson Nano” (Figure 6).

![Figure 6: Manual Setup Selection](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/manuel%20setup%20jetson%20nano.png)
You’ll be prompted to enter a new username and password for the Jetson Nano. After entering these, click Finish to continue the installation.
The SDK Components screen will appear (Figure 7), allowing you to install essential software like CUDA, CUDA X-AI, and OpenCV for deep learning and image processing.

![Figure 7: SDK Components Installation](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20paketleri%20y%C3%BCkleme%20.png)
You have two connection options for installation:

USB Connection: The virtual machine shares its internet with the Jetson Nano via USB. Keep the IP address unchanged.
Ethernet Connection: Connect a USB Wi-Fi adapter to the Jetson Nano, enter its IP address, and proceed with the installation.

Once complete, the Jetson Nano will have the necessary deep learning libraries installed and will boot automatically. Connect it to a monitor to access the login screen, where you can enter your credentials.

Tip: If you skip the installation, you’ll need to manually install the libraries via the Jetson Nano’s terminal. Detailed instructions are available here: [3] https://github.com/55selcukozdemir/web_self-car/blob/main/README.md


![Figure 8: Jetson Nano Models](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri.png)
As shown in Figure 8, there are three Jetson Nano models: Jetson Nano, Jetson Nano (Developer Kit), and Jetson Nano (2GB Developer Kit).

SD Card Models: A 64GB SD card provides ample storage for deep learning libraries.
Non-SD Card Models (4GB RAM, 16GB Internal Storage): The internal storage is insufficient, so use an external storage device (e.g., hard disk, SSD, or flash drive). An SSD is recommended for optimal performance, as flash drives and hard disks are slower.


💾 Booting from SSD
Reference Video: [4] https://youtu.be/53rRMr1IpWs
To boot from an SSD, clone the necessary repository:
$ git clone https://github.com/JetsonHacksNano/bootFromUSB.git

Navigate to the repository:
$ cd bootFromUSB


![Figure 9: Disks Application](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/diskler.png)
Format the SSD (Figure 9). Search for “disks” in the search bar and open the Disks application (Figure 10).

![Figure 10: Selecting the SSD ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ssd.png)
Select the SSD, click the three-line menu, and choose Format Disk (Figure 11). Change the partitioning to GPT (Figure 12), then confirm the format (Figure 13).

![Figure 11: Format Disk Option](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/format.png)


![Figure 12: GPT Partitioning](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/GPT.png)


![Figure 13: Format Confirmation](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/areyousure.png)
After formatting, create a new partition by clicking the + button (Figure 14).

![Figure 14: Creating a New Partition](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/%2Bssd.jpg)
Partition the SSD (Figure 15), name it, and select Internal disk for use with Linux systems only (Ext4) under “Type.” Click Create to complete partitioning (Figure 16).

![Figure 15: Partitioning the SSD](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/disk%20b%C3%B6lme.png)

![Figure 16: Ext4 Partition Type](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ext4.png)
Verify the SSD:
$ ls /dev/sda*

Copy system files to the SSD:
$ ./copyRootToUSB.sh -p /dev/sda1

Navigate to the SSD’s boot/extlinux directory and open a terminal:
$ sudo cp extlinux.conf extlinux.conf.original

Edit the extlinux.conf file:
$ sudo gedit extlinux.conf


![Figure 17: Editing extlinux.conf](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/extlinuxconfig.png)
Copy the marked section, paste it below, and replace “primary” with “sdcard” (Figure 18).

![Figure 18: Modifying extlinux.conf](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sdcard.png)
To boot from the SSD, update the root partition:
$ ./partUUID.sh


![Figure 19: Finding the SSD PARTUUID](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/partuuid.png)

Copy the “root=PARTUUID=...” string and paste it into the “root” section of the primary entry in extlinux.conf (Figure 20).

![Figure 20: Updating the Root Partition](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/root.png)

⚠️ Note: The PARTUUID (e.g., “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1”) is unique to your SSD. Use the correct value for your setup.

Save and close the extlinux.conf file with Ctrl+S.
🌟 SD Card Supported Jetson Nano
If your Jetson Nano supports an SD card, shut it down, ensure no SD card is inserted, and power it on. Check the boot status:
$ lsblk


![Figure 21: Verifying SSD Boot](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/lsblk.png)
If “/” appears next to sda1, the SSD boot was successful.
🌟 Non-SD Card Supported Jetson Nano
For Jetson Nanos without SD card support, delete all system files from the internal storage. The device will shut down after a while. Restart it with the SSD connected, and it will boot from the SSD. Verify with:
$ lsblk

Ensure “/” appears next to sda1.

🖼️ JETSON NANO YOLOv5 INSTALLATION
Reference Video: [5] https://youtu.be/oKaLyow7hWU
Let’s install YOLOv5 for real-time object detection! Start by cloning the YOLOv5 repository:
$ git clone https://github.com/ultralytics/yolov5.git

Navigate to the yolov5 directory and open the requirements.txt file to view the required libraries. We’ll install OpenCV 4.1.1 (not 4.1.2 as listed) without pip to maximize GPU performance with CUDA.
🎯 Step 1: Install OpenCV

Note: Skip this step if OpenCV was installed via Nvidia SDK Manager.

Clone the OpenCV repository:
$ git clone https://github.com/JetsonHacksNano/buildOpenCV.git

Navigate to the buildOpenCV directory and set “NUM_JOBS” to 1 if your Jetson Nano does not support an SD card (Figure 22).

![Figure 22: Modifying NUM_JOBS](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_jobs.png)
Save the file, then run:
$ cd buildOpenCV
$ ./buildOpenCV

🎯 Step 2: Install Other Libraries
Install python3-pip:
$ sudo apt install python3-pip

Install the required libraries:
$ pip3 install -U PyYAML==5.3.1
$ pip3 install tqdm
$ pip3 install cython
$ pip3 install -U numpy==1.18.5
$ sudo apt install build-essential libssl-dev python3-dev
$ pip3 install cycler==0.10
$ pip3 install kiwisolver==1.3.1
$ pip3 install pyparsing==2.4.7
$ pip3 install python-dateutil==2.8.2
$ pip3 install --no-deps matplotlib==3.2.2
$ sudo apt install gfortran
$ sudo apt install libopenblas-dev
$ sudo apt install liblapack-dev
$ pip3 install scipy==1.4.1
$ sudo apt install libjpeg-dev
$ pip3 install pillow==8.3.2
$ pip3 install typing-extensions==3.10.0.2

🎯 Step 3: Install PyTorch and Torchvision
Due to the Jetson Nano’s ARM architecture, PyTorch installation requires a specific approach. Follow the instructions from Nvidia’s forum: [6] https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

![Figure 23: PyTorch Versions](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/torchvision.png)
Select PyTorch 1.10 for Python 3.6 (Figure 24).

![Figure 24: PyTorch and Torchvision Compatibility](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/python%20torchvision.png)

![Figure 25: Download the PyTorch wheel file](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/whl%20dosyas%C4%B1.png)

$ wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O torch-1.10.0-cp36-cp36m-linux_aarch64.whl

Install dependencies:
$ sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev

Install the PyTorch wheel file:
$ pip3 install --no-deps torch-1.10.0-cp36-cp36m-linux_aarch64.whl

Install Torchvision:
$ sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
$ git clone --branch v0.11.1 https://github.com/pytorch/vision torchvision
$ cd torchvision
$ export BUILD_VERSION=0.9.0
$ python3 setup.py install --user

Install Seaborn:
$ pip3 install --no-deps seaborn==0.11.0

Navigate to the yolov5 directory and test YOLOv5:
$ cd yolov5
$ python3 detect.py --source data/images --weights yolov5s.pt


![Figure 26: YOLOv5 Test Results](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sonu.png)     
The pretrained yolov5s.pt model successfully detects objects like people and buses (Figure 26).
📷 RealSense Library for Real-Time Image Processing
For real-time image processing, install the RealSense SDK:
$ git clone https://github.com/jetsonhacks/installRealSenseSDK.git
$ cd installRealSenseSDK

Edit the buildLibrealsense file, replacing “NUM_PROCS” with 1 (Figure 27).

![Figure 27: Modifying NUM_PROCS](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_proc.png)

Run the build script:
$ ./buildLibrealsense.sh

Verify the installation:
$ python3
$ import pyrealsense2

If an error occurs (Figure 28), update the Python path.

![Figure 28: Pyrealsense Error](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense.png)
Edit the .bashrc file, changing /usr/local/lib to /usr/local/lib/python3.6/pyrealsense2 (Figure 29).

![Figure 29: Updating Python Path](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pythonpath.png)
Apply the changes:
$ source ~/.bashrc

Verify again:
$ python3
$ import pyrealsense2 as rs

If it moves to the next line, the installation is successful (Figure 30).

![Figure 30: Successful Pyrealsense Import](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense2.png)
Install libcanberra-gtk:
$ sudo apt install libcanberra-gtk*

🎥 Camera Testing with YOLOv5
Navigate to the yolov5 directory and run real-time detection:
$ python detect.py --weights yolov5s.pt --source 0

The .pt file contains the trained model. Using yolov5s.pt tests pretrained models for objects like people and computers. For our Teknofest Agricultural Unmanned Vehicle CORE Team, we trained a custom .pt file to detect and spray foreign plants (Figure 31).

![Figure 31: Custom YOLOv5 Detection](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/yabanci-bitki.jpg)

📚 References

https://releases.ubuntu.com/18.04/
https://developer.nvidia.com/drive/sdk-managerhttps://youtu.be/0nplGFQ07po
https://github.com/55selcukozdemir/web_self-car/blob/main/README.md
https://youtu.be/53rRMr1IpWs
https://youtu.be/oKaLyow7hWU
https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048


🌟 JetsonNano-bootandsetup
🔄 JETSON NANO SIFIRLAMA
Jetson Nano’yu sıfırlamak ve derin öğrenme projeleri için hazırlamak için bir bilgisayara sanal makine kuruyoruz ve bu makineye Ubuntu Linux işletim sistemi yüklüyoruz (Şekil 1). Bu, temiz ve verimli bir kurulum için temel oluşturur.

⚠️ Önemli Not: Ubuntu 18.04 sürümünü indirmelisiniz, çünkü diğer sürümler Jetson Nano ile uyumlu değildir.

İndirme Linki: [1] https://releases.ubuntu.com/18.04/

Şekil 1: Ubuntu 18.04 İndirme
Ubuntu yüklendikten sonra, sanal makineye Nvidia SDK Manager’ı indirin (Şekil 2). Aşağıdaki linkten “.deb Ubuntu” seçeneğini seçerek indirin. İndirme için Nvidia hesabına kaydolmanız veya giriş yapmanız gerekir; aksi takdirde kurulum çalışmaz.
Link: [2] https://developer.nvidia.com/drive/sdk-manager

Şekil 2: Nvidia SDK Manager İndirme
Ubuntu’da, indirilen dosyanın bulunduğu dizine gidin, bir terminal açın ve şu komutu çalıştırın:
$ sudo dpkg -i nvidiasdkmanager.deb

Hata alırsanız şu komutu çalıştırın:
$ sudo apt --fix-broken install

Ardından dpkg komutunu tekrar deneyin; artık sorunsuz çalışacaktır.
Nvidia SDK Manager’ı başlatın. Karşınıza bir giriş ekranı çıkacak (Şekil 3). Giriş yaptıktan sonra kullanıcı dostu arayüz açılır.

Şekil 3: Nvidia SDK Manager Giriş
Arayüzde, “Target Hardware” bölümünden elinizdeki Jetson Nano modelini seçin (Şekil 4). Doğru modeli seçmek uyumluluk için kritik öneme sahiptir.

Şekil 4: Jetson Nano Model Seçimi
Modeli seçtikten sonra, “ADDITIONAL SDKS” bölümünde yalnızca DeepStream kutusunu işaretleyin ve 2. Adım’a geçin (Şekil 5).

Şekil 5: DeepStream Seçimi
2. Adım’da, gizlilik politikasını kabul edin. İki seçeneğiniz var:

Download now. Install later: Dosyaları indirir ve manuel kurulum için saklar.
Doğrudan İndir ve Kur: Hemen kurulum yapar (bu işlem uzun sürebilir).

Kurulum sırasında Manual Setup’ı seçin, “Automatic Setup - Jetson Nano” yerine (Şekil 6).

Şekil 6: Manuel Kurulum Seçimi
Jetson Nano için yeni bir kullanıcı adı ve şifre girmeniz istenecek. Bunları girdikten sonra Finish’e tıklayın. Kurulum devam edecektir.
Kurulum sırasında SDK Components ekranı görünecek (Şekil 7). Bu ekran, derin öğrenme ve görüntü işleme için gerekli yazılımları (CUDA, CUDA X-AI, OpenCV vb.) yüklemenizi sağlar.

Şekil 7: SDK Components Yükleme
Kurulum için iki bağlantı seçeneği mevcut:

USB Bağlantısı: Sanal makine, internetini USB üzerinden Jetson Nano ile paylaşır. IP adresini değiştirmeyin.
Ethernet Bağlantısı: Jetson Nano’ya bir USB Wi-Fi adaptörü bağlayın, IP adresini girin ve kuruluma devam edin.

Kurulum tamamlandığında, Jetson Nano derin öğrenme için gerekli dosyaları yüklemiş olacak ve otomatik olarak açılacaktır. Giriş ekranını görmek için bir monitöre bağlayın ve kimlik bilgilerinizi girin.

İpucu: Kurulumu atlamak isterseniz, yazılımları Jetson Nano’nun terminalinden manuel olarak yüklemeniz gerekir. Ayrıntılı talimatlar burada: [3] https://github.com/55selcukozdemir/web_self-car/blob/main/README.md


Şekil 8: Jetson Nano Modelleri
Şekil 8’de görüldüğü gibi, Jetson Nano’nun üç modeli vardır: Jetson Nano, Jetson Nano (Developer Kit) ve Jetson Nano (2GB Developer Kit).

SD Kart Destekli Modeller: 64GB SD kart, derin öğrenme kütüphaneleri için yeterli depolama sağlar.
SD Kart Desteksiz Modeller (4GB RAM, 16GB Dahili Depolama): Dahili depolama yetersizdir, bu nedenle harici bir depolama cihazı (ör. sabit disk, SSD veya flash bellek) kullanmalısınız. En iyi performans için SSD önerilir, çünkü flash bellekler ve sabit diskler daha yavaştır.

💾 SSD'den Boot Etme
Yararlanılan Video: [4] https://youtu.be/53rRMr1IpWs
SSD’den önyükleme yapmak için gerekli depoyu kopyalayın:
$ git clone https://github.com/JetsonHacksNano/bootFromUSB.git

Depoya gidin:
$ cd bootFromUSB


Şekil 9: Diskler Uygulaması
SSD’yi formatlayın (Şekil 9). Arama çubuğuna “disks” yazın ve Diskler uygulamasını açın (Şekil 10).

Şekil 10: SSD Seçimi
SSD’yi seçin, sağ üstteki üç çizgili menüye tıklayın ve Format Disk’i seçin (Şekil 11). Bölümlemeyi GPT olarak değiştirin (Şekil 12), ardından formatı onaylayın (Şekil 13).

Şekil 11: Disk Formatlama Seçeneği

Şekil 12: GPT Bölümleme

Şekil 13: Format Onayı
Formatlama完成后，点击 + 按钮创建新分区 (Şekil 14).

Şekil 14: Yeni Bölüm Oluşturma
SSD’yi bölün (Şekil 15), bir isim verin ve “Type” kısmında Internal disk for use with Linux systems only (Ext4) seçeneğini işaretleyin. Create’e tıklayarak bölümlemeyi tamamlayın (Şekil 16).

Şekil 15: SSD Bölümleme

Şekil 16: Ext4 Bölüm Türü
SSD’yi kontrol edin:
$ ls /dev/sda*

Sistem dosyalarını SSD’ye kopyalayın:
$ ./copyRootToUSB.sh -p /dev/sda1

SSD’nin boot/extlinux dizinine gidin ve bir terminal açın:
$ sudo cp extlinux.conf extlinux.conf.original

extlinux.conf dosyasını düzenleyin:
$ sudo gedit extlinux.conf


Şekil 17: extlinux.conf Düzenleme
İşaretli bölümü kopyalayın, altına yapıştırın ve “primary” kısmını “sdcard” ile değiştirin (Şekil 18).

Şekil 18: extlinux.conf Güncelleme
SSD’den önyükleme için root kısmını güncelleyin:
$ ./partUUID.sh


Şekil 19: SSD PARTUUID Bulma
“root=PARTUUID=...” dizesini kopyalayın ve extlinux.conf dosyasındaki primary girişinin “root” kısmına yapıştırın (Şekil 20).

Şekil 20: Root Bölümünü Güncelleme

⚠️ Not: PARTUUID (ör. “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1”) sizin SSD’nize özeldir. Doğru değeri kullandığınızdan emin olun.

extlinux.conf dosyasını Ctrl+S ile kaydedip kapatın.
🌟 SD Kart Destekli Jetson Nano
Eğer Jetson Nano’nuz SD kart destekliyse, cihazı kapatın, SD kartın takılı olmadığından emin olun ve açın. Önyükleme durumunu kontrol edin:
$ lsblk


Şekil 21: SSD Önyükleme Doğrulama
sda1 yanında “/” görünüyorsa, SSD önyüklemesi başarılıdır.
🌟 SD Kart Desteksiz Jetson Nano
SD kart desteği olmayan Jetson Nano’larda, dahili depolamadaki tüm sistem dosyalarını silin. Cihaz bir süre sonra kapanacaktır. SSD takılıyken yeniden başlatın; SSD’den önyükleme yapacaktır. Doğrulamak için:
$ lsblk

sda1 yanında “/” olduğundan emin olun.
🖼️ JETSON NANO YOLOV5 KURULUMU
Yararlanılan Video: [5] https://youtu.be/oKaLyow7hWU
Gerçek zamanlı nesne algılama için YOLOv5’i kuralım! YOLOv5 deposunu kopyalayın:
$ git clone https://github.com/ultralytics/yolov5.git

yolov5 dizinine gidin ve requirements.txt dosyasını açarak gerekli kütüphaneleri görün. OpenCV 4.1.1’i (listede 4.1.2 olarak görünse de) pip olmadan kuracağız, böylece GPU performansını CUDA ile maksimize edeceğiz.
🎯 1. Adım: OpenCV Yükleme

Not: OpenCV’yi Nvidia SDK Manager ile yüklediyseniz bu adımı atlayabilirsiniz.

OpenCV deposunu kopyalayın:
$ git clone https://github.com/JetsonHacksNano/buildOpenCV.git

buildOpenCV dizinine gidin ve SD kart destekli olmayan modeller için “NUM_JOBS” değerini 1 yapın (Şekil 22).

Şekil 22: NUM_JOBS Düzenleme
Dosyayı kaydedin ve şu komutları çalıştırın:
$ cd buildOpenCV
$ ./buildOpenCV

🎯 2. Adım: Diğer Kütüphaneleri Yükleme
python3-pip’i yükleyin:
$ sudo apt install python3-pip

Gerekli kütüphaneleri yükleyin:
$ pip3 install -U PyYAML==5.3.1
$ pip3 install tqdm
$ pip3 install cython
$ pip3 install -U numpy==1.18.5
$ sudo apt install build-essential libssl-dev python3-dev
$ pip3 install cycler==0.10
$ pip3 install kiwisolver==1.3.1
$ pip3 install pyparsing==2.4.7
$ pip3 install python-dateutil==2.8.2
$ pip3 install --no-deps matplotlib==3.2.2
$ sudo apt install gfortran
$ sudo apt install libopenblas-dev
$ sudo apt install liblapack-dev
$ pip3 install scipy==1.4.1
$ sudo apt install libjpeg-dev
$ pip3 install pillow==8.3.2
$ pip3 install typing-extensions==3.10.0.2

🎯 3. Adım: PyTorch ve Torchvision Yükleme
Jetson Nano’nun ARM mimarisi nedeniyle PyTorch kurulumu özel bir yaklaşım gerektirir. Nvidia’nın forumundaki talimatları takip edin: [6] https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

Şekil 23: PyTorch Sürümleri
PyTorch 1.10’u Python 3.6 için seçin (Şekil 24).

Şekil 24: PyTorch ve Torchvision Uyumluluğu
PyTorch wheel dosyasını indirin (Şekil 25):
$ wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O torch-1.10.0-cp36-cp36m-linux_aarch64.whl

Bağımlılıkları yükleyin:
$ sudo apt-get install python3-pip libopenblas-base libopenmpi-dev libomp-dev

PyTorch wheel dosyasını yükleyin:
$ pip3 install --no-deps torch-1.10.0-cp36-cp36m-linux_aarch64.whl

Torchvision’ı yükleyin:
$ sudo apt-get install libjpeg-dev zlib1g-dev libpython3-dev libavcodec-dev libavformat-dev libswscale-dev
$ git clone --branch v0.11.1 https://github.com/pytorch/vision torchvision
$ cd torchvision
$ export BUILD_VERSION=0.9.0
$ python3 setup.py install --user

Seaborn’u yükleyin:
$ pip3 install --no-deps seaborn==0.11.0

yolov5 dizinine gidin ve YOLOv5’i test edin:
$ cd yolov5
$ python3 detect.py --source data/images --weights yolov5s.pt


Şekil 26: YOLOv5 Test Sonuçları
Önceden eğitilmiş yolov5s.pt modeli, insanlar ve otobüs gibi nesneleri başarıyla algıladı (Şekil 26).
📷 Gerçek Zamanlı Görüntü İşleme için RealSense Kütüphanesi
Gerçek zamanlı görüntü işleme için RealSense SDK’yı yükleyin:
$ git clone https://github.com/jetsonhacks/installRealSenseSDK.git
$ cd installRealSenseSDK

buildLibrealsense dosyasını düzenleyin, “NUM_PROCS” değerini 1 yapın (Şekil 27).

Şekil 27: NUM_PROCS Düzenleme
Derleme komutunu çalıştırın:
$ ./buildLibrealsense.sh

Yüklemeyi doğrulayın:
$ python3
$ import pyrealsense2

Hata alırsanız (Şekil 28), Python yolunu güncelleyin.

Şekil 28: Pyrealsense Hata
.bashrc dosyasını düzenleyin, /usr/local/lib’i /usr/local/lib/python3.6/pyrealsense2 ile değiştirin (Şekil 29).

Şekil 29: Python Yolu Güncelleme
Değişiklikleri uygulayın:
$ source ~/.bashrc

Tekrar doğrulayın:
$ python3
$ import pyrealsense2 as rs

Alt satıra geçerse kurulum başarılıdır (Şekil 30).

Şekil 30: Başarılı Pyrealsense İçe Aktarma
libcanberra-gtk’yı yükleyin:
$ sudo apt install libcanberra-gtk*

🎥 Kamera ile Test
yolov5 dizinine gidin ve gerçek zamanlı algılama için şu komutu çalıştırın:
$ python detect.py --weights yolov5s.pt --source 0

.pt dosyası eğitilmiş modeli içerir. yolov5s.pt kullanırsanız, insanlar, bilgisayarlar gibi önceden eğitilmiş modelleri test edersiniz. Teknofest Tarımsal İnsansız Aracı CORE Ekibi olarak, yarışma gereklilikleri doğrultusunda yabancı bitki algılama ve ilaçlama için özel bir .pt dosyası eğittik (Şekil 31).

Şekil 31: Özel YOLOv5 Algılama
📚 Kaynakça

https://releases.ubuntu.com/18.04/
https://developer.nvidia.com/drive/sdk-managerhttps://youtu.be/0nplGFQ07po
https://github.com/55selcukozdemir/web_self-car/blob/main/README.md
https://youtu.be/53rRMr1IpWs
https://youtu.be/oKaLyow7hWU
https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

