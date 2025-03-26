# Elastick-SIEM-
Bu repo, ELK Stack'in bulut tabanlı deneme sürümü üzerinden temel entegrasyonlarına ve SIEM çözümlerine giriş sağlayan bir rehberdir. İçerik; sistem entegrasyonu, ağ paket entegrasyonu ve ELK endpoint entegrasyonu gibi konuları kapsamaktadır.
(Bu çalışmada toplanıp işlenen bütün veriler kişisel bilgisayarım üzerinden gerçekleştirilmiştir.)
<hr>

Elastic Cloud Deneme sayfasına gidin = https://cloud.elastic.co/registration?elektra=guide-welcome-cta <br>
Gerekli bilgiler doğrultusunda giriş yapın.

<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/sign-up-trial.png" width="auto">
Giriş yaptıktan sonra bir dağıtım oluşturabilirsiniz. Dağıtımınıza bir ad verin ve Dağıtım oluştur'u seçin.
<br><br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/create-first-deployment.png" width="auto">
<hr>
<h2>Ajan oluşturma</h2>
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
<h2>System Entegrasyonu ekleme</h2>
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
<h2>Network Packed Capture Entegrasyonu </h2>
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
<h2>Elastic Defend Entegrasyonu</h2>
<h4>Elastic Defend Elastic Stack'in bir güvenlik çözümü olarak sisteminizi koruma, tehditleri algılama ve müdahale yetenekleri sunar. Uç noktaları (endpoint) izleyerek kötü amaçlı yazılımları, şüpheli davranışları ve güvenlik açıklarını gerçek zamanlı olarak tespit etmeyi hedefler.</h4>
1.Entegrasyonlar sayfasında, sorgu çubuğunu kullanarak Network Elastic Defend'i arayın ve entegrasyonu seçin.<br>
2.Managment->Integrations->Elastic Defend>add Elastic Defend<br>
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-integration.png" width="auto"><br><br>
3.Entegrasyonumuzu isimlendirip diğer seçeneklere dokunmadan, en alt kısımda bulunan "Existing Hosts" seçeneğine tıklıyoruz. Daha önce tanımladığımız "Agent Policies" varlığımızı seçtikten sonra "Save and continue" diyerek işlemimizi tamamlıyoruz.
<img src="https://github.com/Serhatti-007/Elastick-SIEM-/blob/main/Picture/defender-integration-add.png" width="auto"><br><br>
