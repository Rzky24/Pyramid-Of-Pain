# Pyramid-Of-Pain
Perkenalan
Konsep yang terkenal ini diterapkan pada solusi keamanan siber seperti Cisco Security , SentinelOne , dan SOCRadar untuk meningkatkan efektivitas CTI (Cyber ​​Threat Intelligence), perburuan ancaman, dan latihan respons insiden.

Memahami konsep Piramida Rasa Sakit sebagai Pemburu Ancaman, Penanggap Insiden, atau Analis SOC sangatlah penting.
Nilai Hash (Sepele)
Menurut Microsoft, nilai hash adalah nilai numerik dengan panjang tetap yang secara unik mengidentifikasi data. Nilai hash adalah hasil dari algoritma hashing. Berikut adalah beberapa algoritma hashing yang paling umum: 

MD5 (Message Digest, didefinisikan oleh  RFC 1321 ) - dirancang oleh Ron Rivest pada tahun 1992 dan merupakan fungsi hash kriptografi yang banyak digunakan dengan nilai hash 128-bit. Hash MD5 TIDAK  dianggap aman secara kriptografi . Pada tahun 2011, IETF menerbitkan RFC 6151,  "Updated Security Considerations for the MD5 Message-Digest and the HMAC- MD5 Algorithms ," yang menyebutkan sejumlah serangan terhadap hash MD5 , termasuk tabrakan hash.
SHA-1 (Secure Hash Algorithm 1, didefinisikan oleh  RFC 3174 ) - diciptakan oleh Badan Keamanan Nasional Amerika Serikat pada tahun 1995. Ketika data dimasukkan ke Algoritma Hashing SHA-1, SHA-1 mengambil input dan menghasilkan string nilai hash 160-bit sebagai angka heksadesimal 40 digit.  NIST menghentikan penggunaan SHA-1 pada tahun 2011 dan melarang penggunaannya untuk tanda tangan digital pada akhir tahun 2013 karena rentan terhadap serangan brute-force. Sebagai gantinya, NIST merekomendasikan migrasi dari SHA-1 ke algoritma hash yang lebih kuat dalam keluarga SHA-2 dan SHA-3.
SHA-2 (Secure Hash Algorithm 2) -  Algoritma Hashing SHA-2 dirancang oleh National Institute of Standards and Technology ( NIST ) dan National Security Agency (NSA) pada tahun 2001 untuk menggantikan SHA-1. SHA-2 memiliki banyak varian, dan yang paling umum adalah SHA-256 . Algoritma SHA-256 mengembalikan nilai hash 256-bit sebagai angka heksadesimal 64 digit.
Sebuah hash tidak dianggap aman secara kriptografis jika dua file memiliki nilai hash atau digest yang sama.

Para profesional keamanan biasanya menggunakan nilai hash untuk mendapatkan wawasan tentang sampel malware tertentu, file berbahaya atau mencurigakan, dan sebagai cara untuk mengidentifikasi dan merujuk artefak berbahaya tersebut secara unik.

 Anda mungkin pernah  membaca laporan ransomware di masa lalu, di mana para peneliti keamanan akan memberikan hash yang terkait dengan file berbahaya atau mencurigakan yang digunakan di akhir laporan. Anda dapat melihat  Laporan DFIR dan Blog Riset Ancaman Trellix  jika Anda tertarik untuk melihat contohnya.

Berbagai alat online dapat digunakan untuk melakukan pencarian hash seperti VirusTotal dan Metadefender Cloud - OPSWAT .

VirusTotal:<img width="1844" height="813" alt="image" src="https://github.com/user-attachments/assets/aa529a63-23b9-4ca4-a02a-864b8eaa5fdb" />

Di bawah tanda pagar pada tangkapan layar di atas, Anda dapat melihat nama file. Dalam hal ini, nama filenya adalah "m_croetian.wnry".

MetaDefender Cloud - OPSWAT:<img width="1546" height="694" alt="image" src="https://github.com/user-attachments/assets/8837560e-31fa-44a5-a8ba-a83728263f94" />
Seperti yang mungkin Anda perhatikan, sangat mudah untuk mendeteksi file berbahaya jika kita memiliki hash-nya. Namun, sebagai penyerang, memodifikasi file bahkan hanya dengan satu bit pun sangat mudah, yang akan menghasilkan nilai hash yang berbeda. Dengan begitu banyak variasi dan contoh malware atau ransomware yang dikenal, perburuan ancaman menggunakan hash file sebagai IOC (Indikator Kompromi) dapat menjadi sulit.

Mari kita lihat contoh bagaimana Anda dapat mengubah nilai hash sebuah file hanya dengan menambahkan string ke akhir file menggunakan perintah `echo : File Hash (Before Modification)`.
PS C:\Users\THM\Downloads> Get-FileHash .\OpenVPN_2.5.1_I601_amd64.msi -Algorithm MD5
Algorithm Hash                             Path                                                 
_________ ____                             ____                                                 
MD5       D1A008E3A606F24590A02B853E955CF7 C:\Users\THM\Downloads\OpenVPN_2.5.1_I601_amd64.msi
Hash File (Setelah Modifikasi)

PS C:\Users\THM\Downloads> echo "AppendTheHash" >> .\OpenVPN_2.5.1_I601_amd64.msi
PS C:\Users\THM\Downloads> Get-FileHash .\OpenVPN_2.5.1_I601_amd64.msi -Algorithm MD5
Algorithm Hash                             Path                                                 
_________ ____                             ____                                                 
MD5       9D52B46F5DE41B73418F8E0DACEC5E9F C:\Users\THM\Downloads\OpenVPN_2.5.1_I601_amd64.msi
Jawablah pertanyaan-pertanyaan di bawah ini.
Analisis laporan yang terkait dengan hash "b8ef959a9176aef07fdca8705254a163b50b49a17217a4ff0107487f59d4a35d" di sini. Apa nama file sampel tersebut?
Sales_Receipt 5606.xls

Alamat IP (Mudah)
Anda mungkin telah mempelajari pentingnya Alamat IP dari Ruang "Apa itu Jaringan?" .  Alamat IP digunakan untuk mengidentifikasi perangkat apa pun yang terhubung ke jaringan. Perangkat ini berkisar dari komputer desktop, server, hingga kamera CCTV!  Kita bergantung pada alamat IP untuk mengirim dan menerima informasi melalui jaringan. Tetapi kita tidak akan membahas struktur dan fungsi alamat IP.  Sebagai bagian dari Piramida Rasa Sakit, kita akan mengevaluasi bagaimana alamat IP digunakan sebagai indikator.

Dalam Piramida Rasa Sakit, alamat IP ditunjukkan dengan warna hijau. Anda mungkin bertanya-tanya mengapa dan apa yang dapat Anda kaitkan dengan warna hijau?

 

Dari sudut pandang pertahanan, pengetahuan tentang alamat IP yang digunakan musuh dapat sangat berharga. Taktik pertahanan umum adalah memblokir, menolak, atau menolak permintaan masuk dari alamat IP pada firewall parameter atau eksternal Anda . Taktik ini seringkali tidak sepenuhnya aman karena sangat mudah bagi musuh yang berpengalaman untuk memulihkannya hanya dengan menggunakan alamat IP publik baru.
Koneksi IP berbahaya ( app.any.run ):<img width="656" height="157" alt="image" src="https://github.com/user-attachments/assets/8a9abd77-ea0a-48d6-974a-51de5a70fe19" />
CATATAN! Jangan mencoba berinteraksi dengan alamat IP yang tertera di atas.

Salah satu cara yang dapat dilakukan oleh pihak lawan untuk mempersulit keberhasilan pemblokiran IP adalah dengan menggunakan  Fast Flux .

Menurut Akamai , Fast Flux adalah teknik DNS yang digunakan oleh botnet untuk menyembunyikan aktivitas phishing , web proxy, pengiriman malware, dan komunikasi malware di balik host yang disusupi yang bertindak sebagai proxy. Tujuan penggunaan jaringan Fast Flux adalah untuk membuat komunikasi antara malware dan server perintah dan kontrolnya (C&C) sulit dideteksi oleh para profesional keamanan. 

Jadi, konsep utama jaringan Fast Flux adalah memiliki banyak alamat IP yang terkait dengan nama domain, yang terus berubah. Palo Alto menciptakan skenario fiktif yang bagus untuk menjelaskan Fast Flux:  " Fast Flux 101: Bagaimana Penjahat Siber Meningkatkan Ketahanan Infrastruktur Mereka untuk Menghindari Deteksi dan Penangkapan oleh Penegak Hukum"

Nama Domain (Sederhana)
Mari kita naiki Piramida Penderitaan dan beralih ke Nama Domain. Anda dapat melihat transisi warnanya - dari hijau ke biru kehijauan.

Nama domain dapat dianggap sebagai pemetaan sederhana antara alamat IP dan serangkaian teks. Sebuah nama domain dapat berisi domain dan domain tingkat atas (misalnya evilcorp.com) atau subdomain yang diikuti oleh domain dan domain tingkat atas (misalnya ). Namun, kita tidak akan membahas detail cara kerja Sistem Nama Domain (DNS). Anda dapat mempelajari lebih lanjut tentang DNS di Ruang "DNS Secara Detail"tryhackme.evilcorp.com ini . 

Mengubah nama domain bisa sedikit lebih merepotkan bagi penyerang karena mereka kemungkinan besar perlu membeli domain, mendaftarkannya, dan memodifikasi catatan DNS. Sayangnya bagi pihak yang bertahan, banyak penyedia DNS memiliki standar yang longgar dan menyediakan API yang semakin memudahkan penyerang untuk mengubah domain.

Domain  C2 ( Infrastruktur Komando dan Kontrol)  Sodinokibi yang berbahaya  :<img width="1463" height="592" alt="image" src="https://github.com/user-attachments/assets/e7e47cf1-db2d-498a-9666-1047f7e5b7a0" />
<img width="441" height="45" alt="image" src="https://github.com/user-attachments/assets/5dfd47b4-0dfc-4290-a2fe-e789da4bf3f8" /> Bisakah Anda menemukan sesuatu yang berbahaya di tangkapan layar di atas? Sekarang, bandingkan dengan tampilan situs web yang sah di bawah ini:<img width="390" height="56" alt="image" src="https://github.com/user-attachments/assets/016c65b8-86a4-4d90-b47d-3b23998e3fb4" />
Ini adalah salah satu contoh serangan Punycode yang digunakan oleh penyerang untuk mengarahkan pengguna ke domain berbahaya yang sekilas tampak sah.

Apa itu Punycode? Menurut Jamf , "Punycode adalah cara untuk mengkonversi kata-kata yang tidak dapat ditulis dalam ASCII, menjadi pengkodean Unicode ASCII."

 

Yang Anda lihat di URL di atas adalah  adıdas.de  yang memiliki Punycode berupa  http://xn--addas-o4a.de/

Internet Explorer, Google Chrome, Microsoft Edge, dan Apple Safari kini cukup baik dalam menerjemahkan karakter yang disamarkan menjadi nama domain Punycode lengkap.
 
Untuk mendeteksi domain berbahaya, log proxy atau log server web dapat digunakan.
 
Penyerang biasanya menyembunyikan domain berbahaya di bawah layanan pemendek URL.   Pemendek URL adalah alat yang membuat URL pendek dan unik yang akan mengarahkan ke situs web tertentu yang ditentukan pada langkah awal pengaturan tautan pemendek URL. Penyerang biasanya menggunakan layanan pemendek URL berikut untuk menghasilkan tautan berbahaya: 
 
bit.ly
goo.gl
ow.ly
s.id
smarturl.it
kecil.pl
tinyurl.com
x.co
Anda dapat melihat situs web sebenarnya yang dituju oleh tautan yang dipersingkat dengan menambahkan "+" di belakangnya (lihat contoh di bawah). Ketik URL yang dipersingkat di bilah alamat peramban web dan tambahkan karakter di atas untuk melihat URL pengalihan. CATATAN: Contoh tautan yang dipersingkat di bawah ini tidak ada.<img width="1140" height="800" alt="image" src="https://github.com/user-attachments/assets/c9db1625-ec8f-4eb1-958a-c16375895b14" />
Melihat Koneksi di Any.run:

 

Karena Any.run adalah layanan sandboxing yang menjalankan sampel, kita dapat meninjau koneksi apa pun seperti permintaan HTTP , permintaan DNS , atau proses yang berkomunikasi dengan alamat IP. Untuk melakukannya, kita dapat melihat tab "jaringan" yang terletak tepat di bawah cuplikan mesin.

Harap diperhatikan : Anda harus sangat berhati-hati saat mengunjungi alamat IP atau melakukan permintaan HTTP apa pun yang tercantum dalam laporan. Bagaimanapun, ini adalah perilaku dari sampel malware - jadi kemungkinan besar mereka melakukan sesuatu yang berbahay 
Permintaan HTTP :

Tab ini menampilkan permintaan HTTP yang tercatat sejak peledakan sampel. Ini dapat berguna untuk melihat sumber daya apa yang diambil dari server web, seperti dropper atau callback.
<img width="1162" height="276" alt="image" src="https://github.com/user-attachments/assets/e3feb21c-473d-446d-9467-0575da2540ea" />
 
Koneksi:

Tab ini menampilkan semua komunikasi yang dilakukan sejak peledakan sampel. Ini dapat berguna untuk melihat apakah suatu proses berkomunikasi dengan host lain. Misalnya, ini bisa berupa lalu lintas C2 , pengunggahan/pengunduhan file melalui FTP , dll.<img width="1130" height="268" alt="image" src="https://github.com/user-attachments/assets/f0f9877b-20dc-4547-9d43-b3e4f02e7af6" />
Permintaan DNS :

Tab ini menampilkan permintaan DNS yang dilakukan sejak sampel tersebut diaktifkan. Malware sering kali melakukan permintaan DNS untuk memeriksa konektivitas internet (misalnya, jika tidak dapat terhubung ke internet/melakukan panggilan balik, maka kemungkinan besar sedang diisolasi (sandbox) atau tidak berguna). <img width="1136" height="264" alt="image" src="https://github.com/user-attachments/assets/88e65950-d62c-4da2-b9bb-dc46781941de" /> 

Apa istilah yang merujuk pada alamat yang digunakan untuk mengakses situs web?
Domain Name
Jenis serangan apa yang menggunakan karakter Unicode dalam nama domain untuk meniru domain yang dikenal?
Punycode attack
Berikan tautan situs web yang dialihkan untuk URL yang dipersingkat menggunakan pratinjau: https://tinyurl.com/bw7t8p4u
https://tryhackme.com/
Artefak Host (Mengganggu)
Mari kita melangkah lebih jauh ke zona kuning.

Pada level ini, penyerang akan merasa sedikit lebih kesal dan frustrasi jika Anda dapat mendeteksi serangan tersebut.  Penyerang perlu kembali pada level deteksi ini dan mengubah alat serta metodologi serangannya.  Hal ini sangat memakan waktu bagi penyerang, dan kemungkinan besar, ia perlu menghabiskan lebih banyak sumber daya untuk alat-alat lawannya.

Artefak host adalah jejak atau hal-hal yang dapat diamati yang ditinggalkan penyerang pada sistem, seperti nilai registri, eksekusi proses yang mencurigakan, pola serangan atau IOC (Indikator Kompromi), file yang dijatuhkan oleh aplikasi berbahaya, atau apa pun yang eksklusif untuk ancaman saat ini.

Eksekusi proses mencurigakan dari Word: <img width="945" height="44" alt="image" src="https://github.com/user-attachments/assets/79b1972e-8ba0-46e6-95a8-d98bafaee237" />

Peristiwa mencurigakan yang diikuti dengan membuka aplikasi berbahaya: <img width="1406" height="709" alt="image" src="https://github.com/user-attachments/assets/1ea07ccc-2e7b-4c4a-b538-526a5383f16d" />
File-file yang dimodifikasi/dihapus oleh pelaku jahat:<img width="1203" height="267" alt="image" src="https://github.com/user-attachments/assets/7a89e5ea-eff9-4ff2-ba60-dcedd9793bd7" />
Artefak Jaringan (Mengganggu)
Artefak Jaringan juga termasuk dalam zona kuning pada Piramida Rasa Sakit. Ini berarti jika Anda dapat mendeteksi dan menanggapi ancaman tersebut, penyerang akan membutuhkan lebih banyak waktu untuk kembali dan mengubah taktiknya atau memodifikasi alat-alatnya, yang memberi Anda lebih banyak waktu untuk menanggapi dan mendeteksi ancaman yang akan datang atau memperbaiki ancaman yang sudah ada.

Artefak jaringan dapat berupa string user-agent, informasi C2 , atau pola URI yang diikuti oleh permintaan HTTP POST. Penyerang mungkin menggunakan string User-Agent yang belum pernah diamati di lingkungan Anda sebelumnya atau tampak tidak biasa. User-Agent didefinisikan oleh RFC2616 sebagai bidang header permintaan yang berisi informasi tentang user agent yang memulai permintaan.

Artefak jaringan dapat dideteksi dalam PCAP Wireshark (file yang berisi data paket jaringan) dengan menggunakan penganalisis protokol jaringan seperti TShark atau dengan menelusuri log IDS (Intrusion Detection System) dari sumber seperti Snort .

Permintaan HTTP POST yang berisi string mencurigakan:<img width="1572" height="139" alt="image" src="https://github.com/user-attachments/assets/4c1af0a8-a70f-4101-b797-dbd9d346ff98" />
Mari kita gunakan TShark untuk menyaring string User-Agent dengan menggunakan perintah berikut:tshark --Y http.request -T fields -e http.host -e http.user_agent -r analysis_file.pcap 
<img width="1395" height="338" alt="image" src="https://github.com/user-attachments/assets/2d4b27db-5845-479f-896d-28a62e279a12" />
Berikut adalah string User-Agent yang paling umum ditemukan untuk Trojan Emotet Downloader.
Jika Anda dapat mendeteksi string User-Agent khusus yang digunakan penyerang, Anda mungkin dapat memblokirnya, menciptakan lebih banyak hambatan dan membuat upaya mereka untuk membahayakan jaringan menjadi lebih menjengkelkan.

Alat (Menantang)
Selamat! Kita telah sampai di bagian yang menantang bagi para musuh!

Pada tahap ini, kami telah meningkatkan ﻿kemampuan deteksi kami terhadap artefak. Penyerang kemungkinan besar akan menyerah untuk mencoba membobol jaringan Anda atau kembali dan mencoba membuat alat baru yang memiliki tujuan yang sama. Ini akan menjadi akhir permainan bagi para penyerang karena mereka perlu menginvestasikan sejumlah uang untuk membangun alat baru (jika mereka mampu melakukannya), menemukan alat yang memiliki potensi yang sama, atau bahkan mendapatkan pelatihan untuk mempelajari cara menjadi mahir dalam alat tertentu. 

Penyerang akan menggunakan utilitas tersebut untuk membuat dokumen makro berbahaya (maldocs) untuk upaya spearphishing, pintu belakang yang dapat digunakan untuk membangun C2 (Infrastruktur Komando dan Kontrol) , file .EXE dan .DLL kustom apa pun , muatan berbahaya, atau peretas kata sandi.

Sebuah Trojan menyebarkan file mencurigakan "Stealer.exe" ke dalam folder Temp:<img width="956" height="430" alt="image" src="https://github.com/user-attachments/assets/2ef3c263-0fe6-4cf2-995d-d6685bf3a4fe" />
Eksekusi file biner yang mencurigakan:<img width="822" height="48" alt="image" src="https://github.com/user-attachments/assets/750b9a00-7831-40cd-9fc4-45e69ad97376" />
Tanda tangan antivirus, aturan deteksi, dan aturan YARA dapat menjadi senjata ampuh yang dapat Anda gunakan untuk melawan penyerang pada tahap ini.

MalwareBazaar  dan  Malshare  adalah sumber daya yang bagus untuk memberi Anda akses ke sampel, umpan berbahaya, dan hasil YARA - semua ini dapat sangat membantu dalam perburuan ancaman dan respons insiden. 

Untuk aturan deteksi, SOC Prime Threat Detection Marketplace adalah platform yang bagus, tempat para profesional keamanan berbagi aturan deteksi mereka untuk berbagai jenis ancaman, termasuk CVE terbaru yang dieksploitasi di lapangan oleh pihak-pihak yang tidak bertanggung jawab. 

Hashing fuzzy juga merupakan senjata ampuh melawan alat penyerang. Hashing fuzzy membantu Anda melakukan  analisis kesamaan - mencocokkan dua file dengan perbedaan kecil berdasarkan nilai hash fuzzy. Salah satu contoh hashing fuzzy adalah penggunaan SSDeep ; di  situs web resmi SSDeep, Anda juga dapat menemukan penjelasan lengkap tentang hashing fuzzy.  

Contoh SSDeep dari VirusTotal:<img width="1152" height="648" alt="image" src="https://github.com/user-attachments/assets/e3c8c1d6-0662-4ce4-b160-3441b69acf45" />
Sebutkan metode yang digunakan untuk menentukan kemiripan antara file-file tersebut? Fuzzy Hashing
Berikan nama alternatif untuk hash fuzzy tanpa singkatan? context triggered piecewise hashes

Ini belum berakhir. Tapi kabar baiknya, kita telah sampai di tahap akhir atau puncak Piramida Penderitaan! 

TTPs adalah singkatan dari Taktik, Teknik & Prosedur. Ini mencakup keseluruhan Matriks MITRE  ATT&CK , yang berarti semua langkah yang diambil oleh musuh untuk mencapai tujuannya, mulai dari upaya phishing hingga persistensi dan eksfiltrasi data. 

Jika Anda dapat mendeteksi dan merespons TTP (Tactics, Techniques, and Procedures) dengan cepat, Anda hampir tidak memberi kesempatan kepada musuh untuk melawan balik.  Misalnya, jika Anda dapat mendeteksi serangan Pass-the-Hash menggunakan Pemantauan Log Peristiwa Windows dan memperbaikinya, Anda akan dapat menemukan host yang disusupi dengan sangat cepat dan menghentikan pergerakan lateral di dalam jaringan Anda . Pada titik ini, penyerang akan memiliki dua pilihan:

Kembali lagi, lakukan lebih banyak riset dan pelatihan, konfigurasikan ulang alat khusus mereka.
Menyerah dan cari target lain.
Opsi 2 jelas terdengar lebih hemat waktu dan sumber daya.

Ini belum berakhir. Tapi kabar baiknya, kita telah sampai di tahap akhir atau puncak Piramida Penderitaan! 

TTPs adalah singkatan dari Taktik, Teknik & Prosedur. Ini mencakup keseluruhan Matriks MITRE  ATT&CK , yang berarti semua langkah yang diambil oleh musuh untuk mencapai tujuannya, mulai dari upaya phishing hingga persistensi dan eksfiltrasi data. 

Jika Anda dapat mendeteksi dan merespons TTP (Tactics, Techniques, and Procedures) dengan cepat, Anda hampir tidak memberi kesempatan kepada musuh untuk melawan balik.  Misalnya, jika Anda dapat mendeteksi serangan Pass-the-Hash menggunakan Pemantauan Log Peristiwa Windows dan memperbaikinya, Anda akan dapat menemukan host yang disusupi dengan sangat cepat dan menghentikan pergerakan lateral di dalam jaringan Anda . Pada titik ini, penyerang akan memiliki dua pilihan:

Kembali lagi, lakukan lebih banyak riset dan pelatihan, konfigurasikan ulang alat khusus mereka.
Menyerah dan cari target lain.
Opsi 2 jelas terdengar lebih hemat waktu dan sumber daya.
Buka halaman web ATT&CK Matrix. Berapa banyak teknik yang termasuk dalam kategori Eksfiltrasi? 9
Chimera adalah kelompok peretas yang berbasis di Tiongkok dan telah aktif sejak tahun 2018. Apa nama alat akses jarak jauh komersial yang mereka gunakan untuk beacon C2 dan eksfiltrasi data? Cobalt Strike
























