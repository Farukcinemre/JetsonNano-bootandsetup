# JetsonNano-bootandsetup
## JETSON NANO SIFIRLAMA

Jetson Nano ‘ya sıfırlama yapılması için bilgisayara sanal bilgisayar kuruyoruz ve bu sanal bilgisayara Ubuntu Linux işletim sistemi kuruyoruz. 


**Not:** Ubuntu 18.04 versiyonu olan işletim sistemi indirilmelidir. Aksi halde başka versiyonlarda çalışmaz. 

Sanal bilgisayar indirme linki :  [1] https://releases.ubuntu.com/18.04/

![Ubuntu İSO dosyası ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ubuntu%20versiyon%2018.04%20indirme.png)

Ubuntu indirildikten sonra sanal makineye Nvidia SDK Manager indirilmesi gerekir. Aşağıdaki linkten indirin. İndirme yaparken aşağıdaki resimde de görüldüğü gibi “.deb Ubuntu “yazan kısma tıklayıp indirmelisiniz. İndirirken sizden üyelik istiyor üye olun ya da hali hazırda bir üyeliğiniz varsa giriş yapmanız yeterlidir. Eğer üye olmazsanız ya da giriş yapmazsanız uygulamayı yükleyemezsiniz. 

  Link:  [2] https://developer.nvidia.com/drive/sdk-manager
  
  ![Nvidia SDK Manager indirme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20jetson%20nano%20indirme.png)
  
Daha sonra Ubuntu Linux’ta yükleme yapabilmek için dosyanın indirildiği yere gelip terminal açıyoruz.

     $sudo dpkg -i nvidiasdkmanager.deb 
     
Bu kodu çalıştırıyoruz. Eğer yüklemede hata veriyorsa 

     $sudo apt  --fix-broken install 
          
Bu kodu çalıştırıyoruz. Bunu yaptıktan sonra tekrar “$ sudo dpkg -i nvidiasdkmanager.deb “kodunu tekrar denediğinizde çalışacaktır.

Daha sonra Nvidia SDK Manager uygulamasını açıyoruz Aşağıdaki resimdeki gibi bir ekran geliyor. “ logging in “ kısmından tekrar giriş yaptıktan sonra uygulama arayüzü açılıyor. 

![Nvidia SDK Manager login ekranı](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/nvidia%20log%20in%20ekran%C4%B1.png)

Aşağıdaki ekrandaki gibi arayüz ekranı geliyor. Burada “Target Hardware” başlıklı kısımı seçip oradan elimizdeki Jetson Nano modeli ne ise onu seçmek gerekir.

[Jetson Nano Model seçim ekranı](https://github.com/Farukcinemre/JetsonNano-bootandsetup/raw/main/images/jetson%20nano%20modelleri%20se%C3%A7im%20ekran%C4%B1%20.png)

Jetson Nanoyu seçtiğimizde “ADDITIONAL SDKS” kısmında sadece DeepStream deki tik işaretine basıp işaretliyoruz ve 2.adıma geçiyoruz.

![Nvidia SDK 2.adım ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/download%20ve%20install%20ekran%C4%B1.png)

2.Adıma geçtiğimizde ise yükleme yapmadan önce bizden privacy policy kabul etmemizi söylüyor. Ve onun yanındaki “Download now. İnstall later“ Seçeneğine tıklarsanız Nvidia Jetson Nano için gerekli olan dosyaları indirir yüklemeyi kendiniz indirdikten sonra yaparsınız eğer o seçeneği işaretlemeden ilerlerseniz direkt download ve install’u yapar(Bu işlem uzun sürebilir). Download ve install devam ederken  aşağıdaki karşımıza resimdeki ekran geliyor. Oradaki “ Automatic Setup -Jetson nano” seçeneği işaretli olacak ekranda görüldüğü üzere “Manual Setup” seçeneğini seçmelisiniz.	 

![Manuel Setup Ekrani](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/manuel%20setup%20jetson%20nano.png)

Bunu seçtiğiniz zaman sizden Jetson Nano’nun yeni kullanıcı adı ve şifresini girmenizi isteyecektir. Bunları girdikten sonra finish e tıklayın. Download ve install işlemi devam edecektir.

Yüklemeye devam ederken karşınıza aşağıdaki gibi bir ekran çıkacak (SDK components yükleme ekranı). Bu ekran Jetson Nano’da görüntü işleme, derin öğrenme ile ilgili çalışma yapmak istiyorsanız o çalışmalar için gerekli olan yazılımları  (CUDA, CUDA X-AI, OPENCV vb.) Jetson Nano’ya yüklemenizi sağlıyor. Burada yazılımları Jetson Nano’ya yüklemeniz için iki seçeneğiniz var

![Jetson Nano SDK components yükleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/raw/main/images/jetson%20nano%20paketleri%20y%C3%BCkleme%20.png)

**1.Seçenek:** İsterseniz resimde de gördüğünüz gibi connection olarak USB’den yükleme yapabilirsiniz. Yani sanal bilgisayar Jetson Nano ile USB üzerinden köprü bağlantı kurup kendi içindeki interneti Jetson Nano’nun da kullanmasını sağlayacak. Eğer USB’den bağlantı yapıp install edecekseniz IP kısmını değiştirmemeniz gerekir.

**2.seçenek:** İsterseniz connection olarak ethernet seçebilirsiniz ve Jetson Nano’ya bir USB wifi adapter bağlayıp onun IP’sini yazıp install'a tıklayıp yüklemesini beklemelisiniz.

Bu yükleme bittiğinde Jetson Nano’ya derin öğrenme için gerekli olan bazı dosyalar yüklenmiş olacak.

Bu işlem bittikten sonra Jetson Nano kendiliğinden açılacaktır. Jetson Nano ‘nun ekranını görebilmek için bir monitör kullanmanız gerekir. Monitöre bağladığınızda giriş ekranı önünüze çıkacak. Kullanıcı adı ve şifrenizi girerek giriş yapabilirsiniz.

Siz bu işleme install yapmadan skip düğmesine basıp geçerseniz yukarıda bahsettiğim yazılımları manuel olarak yani Jetson Nano’nun terminalinden tek tek yüklemeniz gerekecektir.

Tek tek yüklemek için gereken kodlar: [3] https://github.com/55selcukozdemir/web_self-car/blob/main/README.md

Linkte derin öğrenme için gerekli kütüphaneleri adım adım nasıl yüklemeniz gerektiği anlatılıyor. Adım adım işlemleri takip ettiğinizde kütüphaneleri yüklemiş olacaksınız.

![Jetson Nano Modelleri](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/jetson%20nano%20modelleri.png)

Yukarıdaki resimde de görüldüğü gibi Jetson Nano’nun 3 modeli vardır ve bu modeller Jetson Nano, Jetson Nano (developer kit), Jetson Nano (2 gb developer kit version) 

Jetson Nano’nun sdcard destekli modeline sahipseniz 64GB hafızaya sahip bir sdcard bağlarsanız derin öğrenme için gerekli kütüphaneleri yüklemek için yeterli alanınız olmuş olur.

Eğer Jetson Nano’nun sdcard desteği olmayan 4GB ram 16GB dahili hafızası olan modeline sahipseniz bu depolama alanı sizin için yeterli olmayacaktır. Bu nedenle harici başka bir depolama cihazıyla (harddisk, SSD, flash bellek) Jetson Nano’yu çalıştırmanız gerekecektir. Eğer flash bellek ile boot etmeyi denerseniz flash bellek ne kadar hızlı olursa olsun okuma yazma oranı düşük kalacağı için işlemler çok yavaş gerçekleşecektir. Harddiskte kullanırsanız aynı şekilde hızı sizi tatmin etmeyecektir. Burada en mantıklı tercih SSD olacaktır.   

# SSD'den Boot Etme
Yararlandığım video linki: [4]https://youtu.be/53rRMr1IpWs

SSD den boot edebilmemiz için github linkini kopyalıyoruz.

     $ git clone https://github.com/JetsonHacksNano/bootFromUSB.git
     
Daha sonra yüklediğimiz github klasörüne giriş yapıyoruz

     $ cd bootFromUSB
     
![Jetson Nano diskler](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/diskler.png)

Jetson Nano’yu boot edileceğinden SSD ‘nin formatlanması gerekir. Resimde gördüğünüz gibi arama kısmına “disks” yazıp ilk çıkana tıklıyoruz.

![Jetson Nano SSD ](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ssd.png)

esimdeki gibi SSD’yi seçip sağ üstteki 3 çizgi olan kutucuğu seçiyoruz. Format disk’e tıklıyoruz ve Partitioning kısmını GPT olan kısım ile değiştiriyoruz. Daha sonra format a tıklıyoruz ve tekrar formata tıklıyoruz.

![Jetson Nano format disk](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/format.png)

![Jetson Nano format GPT](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/GPT.png)

![Jetson Nano format onay](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/areyousure.png)

Bu işlemleri yaptıktan sonra SSD formatlanmış oluyor. İşlem bittikten sonra resimdeki gibi “+” kısmına basıp disk bölümü yapıyoruz.

![SSD disk bölme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/%2Bssd.jpg)

Daha sonra SSD diskine isim veriyoruz. Burada “Type” kısmında “Internal disk for use with Linux systems only (Ext4)” bu seçeneği işaretliyoruz. Sonra “Create” e tıklayarak ilerliyoruz ve SSD diskin bölümlenmesini yapılmış oluyor.

![SSD bölümleme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/disk%20b%C3%B6lme.png)

![SSD disk format](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/ext4.png)

     $ ls /dev/sda* 

Komutunu kullanarak SSD diski kontrol edebiliyoruz.

     $ ./copyRootToUSB.sh -p /dev/sda1 
                
Bu komutu kullanarak SSD’ye sistem dosyalarını kopyalıyoruz. Daha sonra SSD’ye girip boot/extlinux klasörünün giriyoruz. Klasör içerisinde terminal açıyoruz.

     $ sudo cp extlinux.conf extlinux.conf.original

Burada extlinux dosyalarını kopyalıyoruz.

     $ sudo gedit extlinux.conf 
     
bu komutla birlikte extlinux dosyasının içine giriyoruz.

![Extlinux config dosyası](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/extlinuxconfig.png)

Resimdeki işaretlenen bölgeyi kopyalayıp altına yapıştırıyoruz ve yapıştırılan kısımdaki “primary” kısmına sdcard yazıyoruz.

![Extlinux sdcard](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/sdcard.png)

SSD’den boot etmek istiyorsak root kısmını değiştirmemiz gerekir.Root kısmına SSD’nin sistem dosyalarının olduğu adresi yazmamız gerekir.

     $ ./partUUID.sh 
     
Bu komutu kullanarak SSD’deki sistem dosyalarının adresini bulabiliyoruz.

![Jetson SSD adres](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/partuuid.png)

Buradaki “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1” kısmını kopyalıyoruz ve extlinux içerisindeki primary kısmında bulunan root kısmına yapıştırıyoruz.

![SSD root](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/root.png)

**Not:** Tırnak içinde belirtilen ifade “root=PARTUUID=d75abef0-345f-4f10-b327-5927034572e1” kısmı özel bir kısımdır bu kısım sizde farklı olacaktır. Buna dikkat etmek gerekir. Yapılacak işlemlerde değişiklik yoktur.

Daha sonra extlinux dosyasını ctrl+s ile kaydedip dosyayı kapatıyoruz.

Buradan sonraki kısımda gidişat değişiyor bu nedenle bu kısmı ikiye ayırarak anlatmanın daha sağlıklı olduğunu düşünüyorum.

**1.Jetson Nano sdcard destekli ise**
Eğer sizde bulunan Jetson Nano sdcard destekliyse Jetson Nano’yu kapatıyoruz ve açmadan önce sdcard’ın takılmadığından emin olup Jetson Nano’yu açıyoruz.

     $lsblk
     
![Boot kontrol etme](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/lsblk.png)

Terminali açıp yukardaki kodu yazıyoruz ve Eğer sda1 kısmında part’ın yanındaki kısımda sadece “/” varsa başarıyla boot edilmiş demektir.

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
**Not:**Eğer opencv’yi nvidia SDK Manager’dan Jetson Nano’ya yükleme yapmışsanız bu adımı atlayabilirsiniz.

Opencv dosyalarını kopyalıyoruz

     $git clone https://github.com/JetsonHacksNano/buildOpenCV.git
     
Dosya yüklendikten sonra “buildopencv” dosyasının içine giriyoruz. Orada bulunan  “$NUM_JOBS” kısmını 1 yaparak değiştiriyoruz(eğer Jetson Nano modeliniz sd card destekliyse değiştirme yapmayın)

![OPENCV num jobs](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_jobs.png)

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

Jetson Nano’nun ARM tabanlı işlemci mimarisinden olduğundan dolayı windowstaki gibi torch’un sitesine girip yükleme söz konusu değildir. Daha farklıdır. Torch yüklerken bir de Torchvision yüklememiz gerekir.

Nvidia’nın forum sitesinde Torch kütüphanesini nasıl yükleyeceğinize dair 
Sitenin linki:
[6]https://forums.developer.nvidia.com/t/pytorch-for-jetson/72048

![Torch setup](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/torchvision.png)

Resimde de gördüğünüz gibi Torch’un versiyonları mevcut. Burada  installation kısmına tıkladığınız zaman hangi Torch’un komutlarla adım adım yüklendiğini göstermektedir. Vertification kısmı ise yüklediğimiz Torch ve Torchvision dosyalarını kontrol etmek için kullanılır.

![Python3.6 ve torchvision](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/python%20torchvision.png)

Burada installation’a girdiğimizde Torch’u indirmek için kodlar bulunuyor. Biz Python 3.6 için oluşturulan kod dizinini kullanacağız ve  Torch’un 1.10 sürümünü kuracağız.

![Torch .whl dosyası](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/whl%20dosyas%C4%B1.png)

Resimde de görüldüğü üzere pyhon3.6 için Torch 1.10’u indirmek için “torch-1.10.0-cp36-cp36m-linux_aarch64.whl” dosyasını kullanmamız  gerekir.

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

Yolov5 başarılı bir şekilde resimdeki sonuçları vermeyi başardı.Hazır olarak eğitilen yolov5s.pt modeli insanları ve otobüsü doğru bir şekilde tanımladı.

Jetson Nano’da gerçek zamanlı görüntü işleme yapmak için realsense kütüphanesini yüklememiz gerekir.

İlk olarak githubdaki dosyaları kopyalıyoruz.

     $ git clone https://github.com/jetsonhacks/installRealSenseSDK.git
     
Sonra klasörün içine giriyoruz   

     $cd installRealSenseSDK
     
“buildLibrealsense” dosyasını texteditor ile açıyoruz 

![Num proc dosyası](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/num_proc.png)

Resimde de görülen “$NUM_PROCS” yazısını silip yerine 1 yazıyoruz

Daha sonra buildLibRealsense dosyasını çalıştırıyoruz

     $./buildLibRealsense.sh
     
Yükleme bittikten sonra kütüphanenin yüklenip yüklenmediğini kontrol etmemiz gerekir.

Python’u açıyoruz
 
     $python3  
     
Kütüphaneyi import ediyoruz

     $import pyrealsense2
     
Eğer hata vermeyip bir alt satıra geçmişse yüklenmiş demektir.

![Pyrealsense Hata](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense.png)

Eğer resimdeki gibi hata vermişsse python’un path’ini değiştirmek gerekir.Python’un realsense kütüphanesinin path’ini bulmak gerekiyor.

Pyrealsense2 kütüphanesi /usr/local/lib/python3.6/pyrealsense2 klasöründe bulunuyor.

Home klasörüne gelip üç çizgiye tıklayıp “show hidden files” seçeneğini işaretliyoruz ve .bashrc klasörüne tıklayıp texteditor ile giriş yapıyoruz.

![Pyrealsense PATH](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pythonpath.png)

Resimde de görüldüğü gibi /usr/local/lib olan yeri /usr/local/lib/python3.6/pyrealsense2 olarak değiştirip kaydediyoruz.

Aşağıdaki komutu kullanıyoruz.

     $source ~/.bashrc
     
Python3’ü çalıştırıp kütüphaneyi kontrol ediyoruz.

     $python3 
     
$import pyrealsense2 as rs

![Pyrealsense Python](https://github.com/Farukcinemre/JetsonNano-bootandsetup/blob/main/images/pyrealsense2.png)

Eğer bu şekilde alt satıra geçiyorsa işlemi başarıyla tamamlamışsınız demektir.

Sonra libcanberra-gtk dosyasını kuruyoruz

     $sudo apt install libcanberra-gtk*
     
Ve yolov5 için kurulacak olan kütüphaneleri tamamlıyoruz.

**Kamera ile Test**
