# SQL Sorgu Alıştırmaları

Bu hafta SQL sorguları üzerine çalışıyorsunuz. Bugünkü alıştırmada sizin için hazırladığımız veritabanında aşağıda istediğimiz sonuçları elde etmenize yarayan SQL sorgularını oluşturacaksınız.

# Proje Kurulumu
Projeyi forklayın ve clonlayın. Tamamladığınızda da pushlayın.

## Kütüphane Bilgi Sistemi

Bu veritabanı, bir okulun kütüphanesinden öğrencilerin aldıkları kitapların bilgisini barındırmaktadır.

#Tablolar 
`ogrenci` tablosu öğrencilerin listesini tutar.
`islem` tablosu öğrencilerin kütüphaneden aldıkları kitapların bilgilerini tutar
`kitap` tablosu kütüphanedeki kitapların bilgisini tutar
`yazar` tablosu kitapların yazarları bilgisini tutar
`tur` tablosu kitapların türlerini tutar.

Tablo ilişiklerini görmek için [ktphn.png] dosyasına göz atın.

Yazdığınız sorguları buradan test edebilirsiniz: [https://ergineer.com/assets/materials/fkg36so5-kutuphanebilgisistemi-sql/] (update, delete, drop sorguları iptal edilmiştir).

### Görevler

Aşağıda istenilen sonuçlara ulaşabilmek için gerekli SQL sorgularını altlarına yazın. 


	1) ÖRNEK SORU: Öğrenci tablosundaki tüm kayıtları listeleyin.
	
		CEVAP: SELECT * FROM ogrenci

	2) Öğrenci tablosundaki öğrencinin adını ve soyadını ve sınıfını listeleyin.
 
                CEVAP: SELECT ograd, ogrsoyad, sinif FROM ogrenci ;
	
	3) Öğrenci tablosundaki kız öğrencileri listeleyin. 
                
		CEVAP: SELECT * FROM ogrenci WHERE cinsiyet='K' ;
	
	4) Öğrenci tablosunda kaydı bulunan sınıfların adını her sınıf bir kez görüntülenecek şekilde listeleyiniz
                 
		 CEVAP : SELECT DISTINCT sinif FROM ogrenci
	
	5) Öğrenci tablosunda, 10A sınıfında olan kız öğrencileri listeleyiniz.

                 CEVAP : SELECT ograd, ogrsoyad,sinif,cinsiyet  FROM ogrenci WHERE sinif='10A' AND cinsiyet='K'
	
	6) Öğrenci tablosundaki 10A veya 10B sınıfındaki öğrencilerin adını, soyadını ve sınıfını listeleyiniz.

	         CEVAP : SELECT ograd, ogrsoyad,siniF  FROM ogrenci WHERE sinif IN ('10A', '10B') 
	
	7) Öğrenci tablosundaki öğrencinin adını, soyadını ve numarasını okul numarası olarak listeleyiniz. (as kullanım örneği)

	         CEVAP : SELECT ograd, ogrsoyad, ogrno AS 'Okul Numarası' FROM ogrenci 
	    
	8) Öğrenci tablosundaki öğrencinin adını ve soyadını birleştirip, adsoyad olarak listeleyiniz. (concat, as kullanım örneği)

	          CEVAP : SELECT CONCAT(ograd, ' ', ogrsoyad) AS adsoyad FROM ogrenci
	
	9) Öğrenci tablosundaki Adı ‘A’ harfi ile başlayan öğrencileri listeleyiniz.

		  CEVAP : SELECT ograd FROM ogrenci WHERE ograd LIKE 'A%';
	
	10) Kitaplar tablosundaki sayfa sayısı 50 ile 200 arasında olan kitapların adını ve sayfa sayısını listeleyiniz.

	          CEVAP : SELECT kitapadi,sayfasayisi FROM kitap WHERE sayfasayisi BETWEEN 50 AND 200

	11) Öğrenci tablosunda adı Fidan, İsmail ve Leyla olan öğrencileri listeleyiniz.

                  CEVAP : SELECT ograd,ogrsoyad FROM ogrenci WHERE ograd IN ('Fidan', 'İsmail', 'Leyla');
	
	12) Öğrenci tablosundaki öğrencilerden adı A, D ve K ile başlayan öğrencileri listeleyiniz.

                  CEVAP : SELECT ograd FROM ogrenci WHERE ograd LIKE 'A%' OR ograd LIKE 'D%' OR ograd LIKE 'K%';
	
	13) Öğrenci tablosundaki sınıfı 9A olan Erkekleri veya sınıfı 9B olan kızların adını, soyadını, sınıfını ve cinsiyetini listeleyiniz.

                 CEVAP :SELECT ograd, ogrsoyad, sinif, cinsiyet FROM ogrenci WHERE (sinif = '9A' AND cinsiyet = 'E') OR (sinif = '9B' AND cinsiyet = 'K'); 
	
	14) Sınıfı 10A veya 10B olan erkekleri listeleyiniz.

		CEVAP:SELECT ograd, ogrsoyad, sinif, cinsiyet FROM ogrenci WHERE (sinif = '10A' OR sinif = '10B') AND cinsiyet = 'E';
	
	15) Öğrenci tablosunda doğum yılı 1989 olan öğrencileri listeleyiniz.

                CEVAP : SELECT * FROM ogrenci WHERE YEAR(dtarih) = 1989;
	
	16) Öğrenci numarası 30 ile 50 arasında olan Kız öğrencileri listeleyiniz.

                CEVAP : SELECT ogrno, ograd, ogrsoyad, cinsiyet FROM ogrenci WHERE ogrno BETWEEN 30 AND 50 AND cinsiyet='K'
	
	17) Öğrencileri adına göre sıralayınız (alfabetik).

		 CEVAP: SELECT * FROM ogrenci ORDER BY ograd
	
	18) Öğrencileri adına, adı aynı olanlarıda soyadlarına göre sıralayınız.

                 CEVAP: SELECT * FROM ogrenci ORDER BY ograd,ogrsoyad
	
	
	19) 10A sınıfındaki öğrencileri okul numarasına göre azalan olarak sıralayınız.

		 CEVAP : SELECT ogrno,ograd, ogrsoyad, sinif FROM ogrenci WHERE sinif = '10A' ORDER BY ogrno DESC;
        
	20) Öğrenciler tablosundaki ilk 10 kaydı listeleyiniz.
	[İPUCU: `Select top tüm mysql versiyonlarında düzgün çalışmaz. LİMİT kullanmak daha faydalıdır`]

		   CEVAP : SELECT * FROM ogrenci LIMIT 10 
                   
	21) Öğrenciler tablosundaki ilk 10 kaydın ad, soyad ve doğum tarihi bilgilerini listeleyiniz.

                   CEVAP : SELECT ograd,ogrsoyad,dtarih FROM ogrenci LIMIT 10
	
	22) Sayfa sayısı en fazla olan kitabı listeleyiniz.

                   CEVAP: SELECT * FROM kitap WHERE sayfasayisi = (SELECT MAX(sayfasayisi) FROM kitap);
	
	
	23) Öğrenciler tablosundaki en genç öğrenciyi listeleyiniz.

                   CEVAP: SELECT * FROM ogrenci ORDER BY dtarih IS NULL  ASC LIMIT 1;
	
	
	24) 10A sınıfındaki en yaşlı öğrenciyi listeyin.

                 CEVAP : SELECT * FROM ogrenci WHERE sinif='10A' ORDER BY dtarih DESC  LIMIT 1 
	
	
	25) İkinci harfi N olan kitapları listeleyiniz.

	       CEVAP : SELECT * FROM kitap WHERE kitapadi LIKE '_N%';
	
	26) Öğrencileri sınıflarına göre gruplayarak listeleyin.

               CEVAP : SELECT sinif, COUNT(*) AS Ogrenci_sayisi FROM ogrenci GROUP BY sinif   (?)
		
	27) Öğrencileri her sorgulamada sıralaması farklı olacak şekilde rastgele listeleyin. 
	[İPUCU: rand() fonksiyonu] 

               CEVAP : SELECT * FROM ogrenci ORDER BY RAND();
	
	28) Öğrenci tablosundan Rastgele bir öğrenci seçiniz.

              CEVAP: SELECT * FROM ogrenci ORDER BY RAND() LIMIT 1
	
	29) 10A sınıfından rastgele bir öğrencinin adını, soyadını, numarasını ve sınıfını getirin.

              CEVAP : SELECT ograd, ogrsoyad, ogrno , sinif FROM ogrenci WHERE sinif='10A' ORDER BY RAND() LIMIT 1
	
	
	# Esnek
	30) Öğrenci tablosunda aynı isimde kaçar öğrenci olduğunu bulmak istiyoruz. 
	Öğrenci isimlerinin sayısını "adet" olarak öğrencilerin isimleri "isim" olarak listeleyin. 
	[İPUCU: count() ve group by] 

              CEVAP: SELECT ograd AS isim , COUNT(*) AS adet FROM ogrenci GROUP BY ograd 

