# Elastic-SIEM-
Bu repo, Elastic'in bulut tabanlı deneme sürümü üz0erinden temel entegrasyonlarına ve SIEM çözümlerine giriş sağlayan bir rehberdir. İçerik; sistem entegrasyonu, ağ paket entegrasyonu ve Elastic endpoint ve alarm oluşturma entegrasyonu gibi konuları kapsamaktadır.
(Bu çalışma kişisel Windows client üzerinden gerçekleştirilmiştir.)
<hr>

Elastic Cloud Deneme sayfasına gidin = https://cloud.elastic.co/registration?elektra=guide-welcome-cta <br>
Gerekli bilgiler doğrultusunda giriş yapın.

<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/sign-up-trial.png" width="auto">
Giriş yaptıktan sonra bir dağıtım oluşturabilirsiniz. Dağıtımınıza bir ad verin ve Dağıtım oluştur'u seçin.
<br><br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/create-first-deployment.png" width="auto">
<hr>
<h2>➡️ Ajan oluşturma</h2>
<h4>İlk olarak bir Agent Policy oluşturacağız Elastic Agent Policy, Elastic Agent'ın topladığı verileri tanımlayan bir ayar ve girişler koleksiyonudur. Her Elastic Agent yalnızca bir politikaya kaydedilebilir. Bu politikalar, Fleet UI'da görsel bir temsil sağlar ve YAML dosyası olarak saklanır.</h4><br>
1.Managment->Fleet->Agent Policies->Create Agent Policy<br>
2.Politikanıza bir isim verin, dilerseniz "Advance option" kısmından kişisel düzenlemelerinizi sağlayabilirsiniz.<br>
3.Create Agent Policy
<br><br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/Fleet-agent-policy.png" width="auto"><br>
4.Şimdi kullandığımız istemciye bir agent servisi ekliyoruz.Elastic Agent, Elastic'in bir parçası olan ve çeşitli veri kaynaklarından loglar, metrikler ve güvenlik olayları gibi bilgileri toplayan birleşik bir veri toplayıcısıdır. Elastic Agent, merkezi bir şekilde yönetilebilir ve kullanıcıların farklı veri toplama işlemleri için birden fazla araç kullanma ihtiyacını ortadan kaldırır.<br>
5.Managment->Fleet->Agents->add agents<br>
6.Oluşturduğunuz Agent Policy kuralını seçiyorsunuz.<br><br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/add-agents.png" width="auto"><br>
7."Install Elastic Agent on your host" Doğru platformu seçin (Linux, Mac, Windows, vb. gibi) ben host olarak kendi "Windows" istemcimi kullanıyorum .<br>
8.Shell üzerinden Elastic Agent'ı yüklemek, kaydetmek ve çalıştırmak için bazı komutlar mevcut siz hangi OS kullanıyorsanız seçiminizi yapıp kurulumu tamamlayabilirsiniz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/add-agent-host.png" width="auto"><br>

<hr>
<h2>➡️ System Entegrasyonu ekleme</h2>
<h4>Elastic Stack'te System entegrasyonu, bir hostun sistem metriklerini ve loglarını toplamak için kullanılan bir yapılandırmadır. Bu entegrasyon, CPU kullanımı, bellek durumu, disk performansı ve ağ aktiviteleri gibi kritik sistem bilgilerini izlemeye ve Elastic Stack içinde analiz etmeye olanak tanır(Windows için Event Log'larını toplar Application,System,Security).</h4>
1.Bulut dağıtımınızda oturum açın, bu sizi Kibana Home'a götürecektir. Elastic simgesine tıklayarak her zaman Ana Sayfa'ya dönebilirsiniz.
2.Entegrasyon ekle'ye tıklayın.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/home-page.png" width="auto">

<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/system-integration.png" width="auto">
3.Entegrasyonlar sayfasında, sorgu çubuğunu kullanarak System'i arayın ve entegrasyonu seçin.<br>
4.Managment->Integrations->System->add System<br>
5.Entegrasyonumuzu isimlendirip diğer seçeneklere dokunmadan, en alt kısımda bulunan "Existing Hosts" seçeneğine tıklıyoruz. Daha önce tanımladığımız "Agent Policies" varlığımızı seçtikten sonra "Save and continue" diyerek işlemimizi tamamlıyoruz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/system-integration-add.png" width="auto"><br><br>
6.Artık "System" entegrasyonumuzu sağladığımıza göre, bir "Dashboard" görüntüleyelim. Örnek olarak, sistem metrikleri hakkında bize bilgi versin.<br>
7.Managment->Integrations->System->Assets->[Metrics System] Host overview<br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/system-host-overview.png" width="auto"><br><br>
<h2>➡️ Network Packed Capture Entegrasyonu </h2>
<h4>Network Packet Capture entegrasyonu, bir ağdaki paket trafiğini yakalamak ve analiz etmek için kullanılan bir özelliktir. Elastic Stack içinde bu entegrasyon, ağ güvenliğini sağlamak ve olası tehditleri belirlemek için detaylı veri sağlar. Özellikle, ağdaki şüpheli aktiviteleri izleme, performansı analiz etme ve sorun giderme gibi amaçlar için kullanılır.</h4>
1.Entegrasyonlar sayfasında, sorgu çubuğunu kullanarak Network Packed Capture'i arayın ve entegrasyonu seçin.<br>
2.Managment->Integrations->Network Packed Capture>add System<br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/network-capture-integration.png" width="auto"><br><br>
3.Entegrasyonumuzu isimlendirip diğer seçeneklere dokunmadan, en alt kısımda bulunan "Existing Hosts" seçeneğine tıklıyoruz. Daha önce tanımladığımız "Agent Policies" varlığımızı seçtikten sonra "Save and continue" diyerek işlemimizi tamamlıyoruz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/network-capture-add.png" width="auto"><br><br>
4.Artık "Network Packed Capture" entegrasyonumuzu sağladığımıza göre, Kibana üzerinden bir "Dashboard" görüntüleyelim. Örnek olarak, ağ trafiği hakkında genel grafikleri alalım.<br>
5.Kibana->Dashboard->[Network Packet Capture] Overview
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/network-capture-overview.png" width="auto"><br><br>
6.Şimdi dashboard üzerinde 24 saat içerisinde gelmiş olan bütün logları "Discover" sekmesi üzerinden görüntüleyelim.  
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/network-capture-overview-discover.png" width="auto"><br><br>
7.Aşağıda görüldüğü üzere 24 saat içerisinde gelen logları "Discover" sayesinde görüntüleyebilir ve detayları inceleyebilirsiniz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/Network-capture-discover.png" width="auto"><br><br>
 <h2>➡️ Elastic Defend Entegrasyonu Genel Bakış</h2>
 <h4>Elastic Defend Elastic Stack'in bir güvenlik çözümü olarak sisteminizi koruma, tehditleri algılama ve müdahale yetenekleri sunar. Uç noktaları (endpoint) izleyerek kötü amaçlı yazılımları, şüpheli davranışları ve güvenlik açıklarını gerçek zamanlı olarak tespit etmeyi hedefler.</h4>
    <h4>1. Elastic Endpoint Agent</h4>
    <ul>
        <li>Zararlı yazılımları, şüpheli aktiviteleri ve güvenlik tehditlerini algılar.</li>
        <li>Gerçek zamanlı sistem izleme ve proaktif tehdit müdahalesi sağlar.</li>
        <li>Windows, macOS ve Linux gibi işletim sistemlerini destekler.</li>
        <li>Tespit edilen tehditlere müdahale ederek dosyaları karantinaya alabilir ve süreçleri durdurabilir.</li>
    </ul>
    <h4>2. Log Toplama</h4>
    <ul>
        <li><strong>Process Events:</strong> Çalıştırılan programlar ve parent-child ilişkileri.</li>
        <li><strong>File Events:</strong> Dosya oluşturma, değiştirme ve işlemle ilişkili aktiviteler.</li>
        <li><strong>Network Events:</strong> IP bağlantıları ve kullanılan portlar (ör. 80, 443).</li>
        <li><strong>Registry Events:</strong> Kayıt defteri değişiklikleri ve yeni kayıt anahtarları.</li>
        <li><strong>Security Events:</strong> Kullanıcı giriş/çıkış işlemleri ve yetki yükseltme girişimleri.</li>
    </ul>
    <h4>3. Alarm ve Uyarılar</h4>
    <ul>
        <li>Elastic Security, tespit edilen tehditlere dayalı olarak uyarılar oluşturur.</li>
        <li>Fidye yazılımı veya yetkisiz erişim gibi tehditlere karşı alarmlar üretir.</li>
        <li>Alarmlar, detaylı analiz için Elastic SIEM'de görüntülenir.</li>
    </ul> 
    <h4>4. Özelleştirilebilir Kurallar</h4>
    <ul>
        <li>Sistem davranışlarına göre tehditleri algılamak için özelleştirilebilir.</li>
        <li>Hem alarm üretmek hem de otomatik müdahale mekanizmalarını tetiklemek için kullanılabilir.</li>
    </ul> 
    <h4>5. Kullanım Amacı</h4>
    <ul>
        <li>Siber tehditlere karşı modern bir koruma sağlamak.</li>
        <li>Şüpheli olayları ve tehditleri tespit ederek hızlı aksiyon almak.</li>
        <li>Logları analiz ederek güvenlik açıklarına karşı erken önlem almak.</li>
    </ul>

<h2>➡️ Elastic Defend Entegrasyonu</h2>
1.Entegrasyonlar sayfasında, sorgu çubuğunu kullanarak Network Elastic Defend'i arayın ve entegrasyonu seçin.<br>
2.Managment->Integrations->Elastic Defend>add Elastic Defend<br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-integration.png" width="auto"><br><br>
3.Entegrasyonumuzu isimlendirip diğer seçeneklere dokunmadan, en alt kısımda bulunan "Existing Hosts" seçeneğine tıklıyoruz. Daha önce tanımladığımız "Agent Policies" varlığımızı seçtikten sonra "Save and continue" diyerek işlemimizi tamamlıyoruz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-integration-add.png" width="auto"><br><br>
4.Entegrasyon tamamlandıktan sonra, kurulumun tamamlanmasını bekliyoruz. Ardından, istemcinizde "Elastic Endpoint" servisi eklenmiş ve çalışır durumda olmalıdır.<br>
5.Artık "Elastic Defend" entegrasyonumuzu sağladığımıza göre, bir "Dashboard" görüntüleyelim. Örnek olarak, son 15 dakika içerisindeki güvenlik ortamı etkinliğimizin özetini gösterelim.<br>
6.Security->Dashboard->Overview
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-dashboard-overview.png" width="auto"><br><br>
7.Şimdi "View events" sekmesine gelerek toplanan logları inceleyebiliriz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-events.png" width="auto"><br><br>
<h2>➡️ Elastic Defend Alarm üretme ⏰</h2>
<h4>Elastic alarm üretimi, Elastic Security'de sistemdeki tehditlerin veya anormalliklerin tespit edilmesine ve bunun sonucunda bir uyarı (alarm) oluşturulmasına dayanan önemli bir güvenlik mekanizmasıdır. Bu süreç, Elastic Stack içindeki algılama kuralları ve olay verileri aracılığıyla gerçekleştirilir. İşte detaylar:</h4>
    <h4>1. Algılama Süreci</h4>
    <ul>
        <li>Elastic Defend, sistemde gerçekleşen olayları (ör. process, file, network gibi) izler ve toplar.</li>
        <li>Olaylar, Detection Rules (Algılama Kuralları) ile karşılaştırılır.</li>
        <li>Bir olay, kuralın tanımladığı kriterleri karşılarsa tehdit olarak değerlendirilir.</li>
    </ul>
    <h4>2. Alarm Oluşturma</h4>
    <ul>
        <li>Bir tehdit tespit edildiğinde Elastic Security bir alarm oluşturur.</li>
        <li>Alarm, tehdidin türü, etkilenen bileşenler ve bağlamsal bilgiler gibi detayları içerir.</li>
    </ul>  
    <h4>3. Alarmın Amacı</h4>
    <ul>
        <li>Güvenlik ekiplerini potansiyel tehditlere karşı bilgilendirir.</li>
        <li>Olaylara hızlı müdahale imkanı sağlar.</li>
    </ul>   
    <h4>4. Proaktif Güvenlik</h4>
    <ul>
        <li>Alarm üretimi otomatik müdahale süreçlerini tetikleyebilir.</li>
        <li>Örneğin, tehdit algılandığında ilgili dosya karantinaya alınabilir veya süreç durdurulabilir.</li>
    </ul>
    <h4>5. Örnek Kullanım Alanları</h4>
    <ul>
        <li>Fidye yazılımı saldırılarına karşı koruma.</li>
        <li>Yetki yükseltme girişimlerinin tespiti.</li>
        <li>Şüpheli ağ bağlantılarının tespiti.</li>
    </ul>
<h4>Alarm oluşturabilmek için öncelikle bir kural tanımlamamız gerekir; aksi takdirde alarm üretimi mümkün olmaz, sadece gelen logları manuel inceleyebiliriz ve manuel müdahale edebiliriz. Tanımlanan kural, sistemde gerçekleşen olayları belirlenen kriterlere göre değerlendirir ve tespit edilen tehditlere yönelik uyarılar oluşturur. Bu, güvenlik yönetiminde ilk ve en önemli adımdır.Mevcut durumda birçok kural bulunmaktadır ve çözüm süreçlerinize uygun olarak kurallar ekleyebilirsiniz. Ancak, herhangi bir kural eklemezseniz, otomatik olarak hiçbir alarm almanız mümkün olmaz. Aynı şekilde, kuralların sağladığı otomatik müdahale gibi mekanizmalardan da yararlanamazsınız. Bu sunumda, sürecin daha anlaşılır olması adına yalnızca bir adet kural ekliyoruz. </h4>
1.Şimdi bir kural oluşturacağız, kullanacağımız kural "Endpoint Security (Elastic Defend)".<br><br>
2."Endpoint Security (Elastic Defend)" bu kuralı ne yapıyor ?
    <ul>
        <li>Zararlı yazılımların (malware) tespiti için malware taraması (signature-based detection).</li>
        <li>Dosyaların izolasyonu (file quarantine & deletion).</li>
        <li>Yürütülebilir zararlı dosyaların engellenmesi (.exe, .dll, vb.).</li>
        <li>Şüpheli hash'lere sahip dosyaların algılanması.</li>
        <li>Temel anormalliklere dayalı tehdit algılama (heuristic-based detection).</li>
    </ul>

3.Security->Rules->Detection rules(SIEM).<br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-rules.png" width="auto"><br><br>
4.Artık örnek bir alarm oluşturma zamanı geldi.<br>
5.Kullanacağımız basit yöntem, bir EICAR Test Virüsü, zararsız bir dosya olup, antivirüs yazılımlarını test etmek amacıyla geliştirilmiştir. Gerçek bir virüs değildir ve bilgisayarınıza zarar vermez. Bu dosya, antivirüs yazılımlarının tehdit algılama yeteneklerini test etmek için kullanılır. EICAR dosyası, belirli bir kod dizisi içerir ve bu kod, antivirüs yazılımları tarafından zararlı olarak algılanacak şekilde tasarlanmıştır.<br>
6.Desktop üzerinde bir metin belgesi açalım ( X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H* ) içerisine bu kod parçacığını ekliyoruz, ardından herhangi bir isim verip .exe,.com gibi çalıştırılabilir bir formatta kaydedelim.(Farklı kaydet yapabilirsiniz.)<br><br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/Create-malware.png" width="auto"><br><br>
7.Kayıt tamamlandığı anda, "Elastic Security" bize bir bildirim gönderiyor.<br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-endpoind-alert.png" width="auto"><br><br>
8.Oluşturduğumuz, "Endpoint Security (Elastic Defend)" kuralı, Elastic Endpoint'in imza tabanlı tehdit algılama yeteneklerinden faydalanır. EICAR test dosyası gibi zararsız bir test kodu bile Elastic tarafından algılanabilir çünkü bu kod, önceden tanımlanmış ve tehdit veri tabanında kayıtlı bir imzaya sahiptir."Endpoint Security (Elastic Defend)" kuralı, tespit edilen dosyaya otomatik olarak müdahale eder, karantinaya alır ve sistemden kaldırır.<br>
9.Şimdi aldığımız uyarıyı "Elastic" üzerinden inceleyelim  (Security->Alerts)      
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-alerts-page.png" width="auto" style:><br><br>
10.Dosyanın algılanması ve Elastic'in alarm oluşturması, imza tabanlı algılama mekanizmasının çalıştığını doğruluyor.Bu, sistemin sadece pasif bir şekilde izlemekle kalmayıp, güvenlik olaylarına hızlı ve etkili bir şekilde yanıt verdiğini gösteriyor.<br>
11.Alerts sayfasında "Investigate in Timeline 🖧", Elastic Security'de bir alarmın (alert) detaylarını zaman çizelgesi (timeline) üzerinde incelemenizi sağlayan bir özelliktir. Bu özellik, bir güvenlik olayının nasıl geliştiğini ve hangi süreçlerin bu olaya dahil olduğunu anlamanıza yardımcı olur, tehditleri daha hızlı analiz etmek için çok önemli bir özellik.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-alerts-investigation_timeline.png" width="auto" style:><br><br>
