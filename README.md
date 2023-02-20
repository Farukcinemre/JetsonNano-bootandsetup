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

     $ cd boot FromUSB
     



  






