Amazon AWS Hesabı Oluşturun:
AWS üzerinden bir hesap oluşturun.

EC2 Dashboard'a Giriş Yapın:
AWS ana sayfasında "EC2" seçeneğini belirleyin ve ardından "Launch Instance" butonuna tıklayın.

EC2 Dashboard

Örnek Oluşturun:
Amazon Linux Machine seçerek yeni bir örnek oluşturun.

Örnek Oluştur

Anahtar Oluşturun:
"Create new key pair" seçeneğine tıklayarak bir anahtar oluşturun ve .ppk uzantılı olarak kaydedin.
Not: Eğer .pem uzantılı bir anahtara sahipseniz, PuTTYgen kullanarak .ppk uzantısına dönüştürün.

Anahtar Oluştur

HTTP ve HTTPS Protokollerine İzin Verin: HTTP ve HTTPS protokollerini işaretleyip "Launch Instance" butonuna tıklayarak makine kurulumunu tamamlayın.

Protokoller ve Başlatma

PuTTY'i İndirin:

PuTTY adresinden PuTTY'i indirin ve kurun.

Not: PuTTY aynı zamanda .pem uzantısını .ppk uzantısına dönüştürmek için PuTTYgen programını içermektedir.

.pem Uzantılı Anahtarı .ppk'ya Dönüştürün (Opsiyonel):

PuTTYgen uygulamasını başlatın, "Load private key" seçeneğiyle .pem uzantılı anahtarı yükleyin ve .ppk dosyasını kaydedin.

PuTTYgen

PuTTY ile SSH Bağlantısı Kurun:

PuTTY'i başlatın, AWS'deki makinenizin Public IPv4 adresini girin, .ppk dosyasını ekleyin ve bağlantıyı kurun.

PuTTY

Bilgisayardaki Dosyaları Makineye Yükleyin:

mkdir website

cd website

wget --no-check-certificate -r 'https://drive.google.com/uc?export=download&id=12xMi5wTIbRvaCNVgPdodLJgI2-TdxRSI' -O bulut.zip

unzip bulut.zip

Docker Kurun

sudo yum update -y

sudo yum install docker -y

sudo service docker start

sudo usermod -aG docker ec2-user

Dockerfile Oluşturun

vim Dockerfile

İçeriğe geçmek için Insert tuşuna basın ve aşağıdaki içeriği ekleyin:

FROM httpd

COPY . /usr/local/apache2/htdocs/

Çıkış yapmak için esc tuşuna basın :wq! yazın ve enter tuşuna basın.

Docker Image Oluşturun ve Çalıştırın

docker build -t website .

docker images

docker run -itd -p 80:80 --name website website

docker ps

Websitenizi Kullanmaya Başlayın: Tarayıcınıza Public IPv4 adresini girerek websitenizi başarıyla kullanabilirsiniz.

website
