# 16-Bit RISC Processor Simulator (Phase 1)

Bu proje, MIPS mimarisinden esinlenerek geliştirilmiş **16-bit RISC işlemci** tasarımının ilk aşamasıdır. Python ve Tkinter kullanılarak geliştirilen bu simülatör, Assembly komutlarını makine koduna (binary) dönüştürme ve adım adım (step-by-step) çalıştırma yeteneğine sahiptir.



## 🚀 Öne Çıkan Özellikler

* **GUI Tabanlı Simülasyon:** Komut girişinden register takibine kadar her işlem görsel arayüz üzerinden yapılır.
* **Anlık Makine Kodu Çevirisi:** Yazılan Assembly kodlarını donanımın anlayacağı **16-bit binary** formatına otomatik dönüştürür.
* **Esnek Çalışma Modları:**
    * **Step:** Komutları tek tek işleterek register ve bellek değişimlerini gözlemleme.
    * **Run:** Tüm programı otomatik ve hızlı bir şekilde koşturma.
* **Bellek Yönetimi:** 512 Byte Instruction ve 512 Byte Data Memory ayrımı (Harvard Mimarisi yaklaşımı).

## 🛠 Teknik Mimari

### 1. Yazmaç Yapısı (Register File)
MIPS standartlarına uygun **32 adet genel amaçlı yazmaç** tanımlanmıştır:
* `$zero`: Her zaman 0 değerini tutar.
* `$t0-$t9`, `$s0-$s7`: Geçici ve saklanan veriler için.
* `$ra`: Fonksiyon dönüş adresleri (`jal` ve `jr` komutları için).

### 2. Desteklenen Komut Seti (ISA)
Simülatör şu komut tiplerini tam olarak destekler:
* **Aritmetik/Mantık (R-Type):** `add`, `sub`, `and`, `or`, `slt`
* **Kaydırma (Shift):** `sll`, `srl`
* **Hafıza ve Immediate (I-Type):** `addi`, `lw`, `sw`
* **Dallanma (Branch):** `beq`, `bne`
* **Atlama (J-Type):** `j`, `jal`, `jr`

## 🖥️ Arayüz Rehberi

Simülatör kullanımı kolaylaştırmak için renklerle ayrılmış bölümlerden oluşur:
* **Pembe Alan (Input):** Assembly kodlarının yazıldığı bölümdür.
* **Yeşil Alan (Registers):** Yazmaçlardaki değerlerin anlık değişimini gösterir.
* **Mavi Alan (Machine Code):** Kodun 16-bitlik binary karşılığını gösterir.
* **Turuncu Alan (Instruction Memory):** Belleğe yüklenen komutları adresleriyle listeler.
* **Sarı Alan (Program Counter):** İşlemcinin o an hangi adreste olduğunu gösterir.

## 📖 Çalıştırma Adımları

1.  **Kod Yazımı:** `MIPS Komutları` alanına geçerli bir Assembly kodu yazın. (Örn: `addi $t0, $zero, 10`)
2.  **Yükleme:** `Load` butonuna basarak kodları belleğe aktarın ve etiketleri (labels) tanımlayın.
3.  **Yürütme:** * Değişimleri görmek için `Step` butonunu kullanın.
    * Programın tamamını bitirmek için `Run` butonunu kullanın.

---

### Örnek Test Senaryosu
```mips
addi $t0, $zero, 5
addi $t1, $zero, 10
add $t2, $t0, $t1
sw $t2, 0($zero)
```
*Bu kod çalıştırıldığında `$t2` yazmacında 15 değeri görülecek ve Data Memory'nin 0. adresine 15 yazılacaktır.*

---

**Geliştirici Notu:** Bu Phase 1 çalışması, işlemcinin mantıksal doğrulamasını yapmak için tasarlanmıştır. Bir sonraki aşamada (Phase 2) pipeline yapısı ve hazard yönetimi bu temel üzerine inşa edilecektir.

<img width="1920" height="1080" alt="Machinli" src="https://github.com/user-attachments/assets/78ccd1dd-dad0-4333-a106-c11c109c8f00" />   
görsel ek olarak paylaşılmıştır.
