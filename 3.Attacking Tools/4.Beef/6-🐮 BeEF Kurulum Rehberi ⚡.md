**1. Ön Gereksinimlerin Kurulumu 📦**
```bash
# Ruby reposunu ekle:
sudo apt-add-repository -y ppa:brightbox/ruby-ng

# Ruby'yi yükle:
sudo apt-get install ruby

# Bundler'ı kur:
gem install bundler
```

**2. BeEF'i İndirme ve Kurma 🚀**
```bash
# /opt klasörüne git ve BeEF'i klonla:
cd /opt
sudo git clone https://github.com/beefproject/beef

# BeEF klasörüne gir ve kurulumu başlat:
cd beef
sudo ./install
```

**3. Son Güncellemeleri Yap 🔄**
```bash
# BeEF'i güncelle:
sudo ./update-beef
```

---

### ✅ Kurulum Kontrol Listesi 📋
- [ ] Ruby reposu eklendi
- [ ] Ruby kuruldu
- [ ] Bundler yüklendi
- [ ] BeEF klonlandı
- [ ] Kurulum scripti çalıştı
- [ ] Güncelleme tamamlandı

**🎯 Not:** Kurulum tamamlandığında `./beef` komutu ile BeEF'i başlatabilirsin! 🚀