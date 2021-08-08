# PostgreSQL ödevleri

<a href='#Ödev 1'>ÖDEV 1</a><br>
<a href='#Ödev 2'>ÖDEV 2</a><br>
<a href='#Ödev 3'>ÖDEV 3</a><br>
<a href='#Ödev 4'>ÖDEV 4</a><br>
<a href='#Ödev 5'>ÖDEV 5</a><br>
<a href='#Ödev 6'>ÖDEV 6</a><br><br><br>

# <p id = 'Ödev 1' > ÖDEV 1 </p>

### 1. Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

~~~sql
SONUÇ: SELECT title, description FROM film
~~~
<br>

### 2. Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

~~~sql
SONUÇ: SELECT * FROM film 
       WHERE length>60 AND length<75
~~~
<br>

### 3. Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

~~~sql
SONUÇ: SELECT * FROM film 
       WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99
~~~
<br>

### 4. Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

~~~sql
SONUÇ: Smith
~~~
<br>

### 5. Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

~~~sql
SONUÇ: SELECT * FROM film 
       WHERE NOT length>50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99)
~~~
<br>
----------------------------------------------------------------------------------------------------

# <p id='Ödev 2'> ÖDEV 2 </p>

### 1. Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

~~~sql
SONUÇ: SELECT * FROM film
->WHERE replacement_cost BETWEEN 12.99 AND 16.99
->WHERE replacement_cost>=12.99 AND replacement_cost<=16.99
~~~
<br>

### 2. .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

~~~sql
SONUÇ: SELECT first_name,last_name FROM actor
       WHERE first_name IN('Penelope','Nick','Ed')
~~~
<br>

### 3. Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

~~~sql
SONUÇ: SELECT * FROM film
       WHERE rental_rate IN(0.99,2.99,4.99) AND replacement_cost IN(12.99,15.99,28.99)
~~~
<br>
----------------------------------------------------------------------------------------------------

# <p id='Ödev 3'>ÖDEV 3</p>

### 1. Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

~~~sql
SONUÇ: SELECT * FROM country
       WHERE country LIKE 'A%a'
~~~
<br>

### 2. Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

~~~sql
SONUÇ: SELECT * FROM country
       WHERE country LIKE '_____n'
~~~
<br>

### 3. Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

~~~sql
SONUÇ: SELECT title FROM film
       WHERE title ~~* '%t%t%t%t%'
~~~
<br>

### 4. Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

~~~sql
SONUÇ: SELECT * FROM film
       WHERE title ~~'C%' AND length>90 AND rental_rate=2.99
~~~
<br>

----------------------------------------------------------------------------------------------------

# <p id='Ödev 4'>ÖDEV 4</p>

### 1. Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

~~~sql
SONUÇ: SELECT DISTINCT replacement_cost FROM film
~~~
<br>

### 2. Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

~~~sql
SONUÇ: '21' SELECT COUNT(DISTINCT replacement_cost) FROM film 
~~~
<br>

### 3. Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

~~~sql
SONUÇ: '9' SELECT COUNT(*) FROM film
        WHERE (title LIKE 'T%') AND (rating='G') 
~~~
<br>

### 4. Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

~~~sql
SONUÇ: '13' SELECT COUNT(*) FROM country
        WHERE country LIKE '_____'
~~~
<br>

### 5. City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

~~~sql
SONUÇ: '33' SELECT COUNT(*) FROM city
        WHERE city ~~*'%r'
~~~
<br>

----------------------------------------------------------------------------------------------------

# <p id='Ödev 5'>ÖDEV 5</p>

### 1. Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

~~~sql
SONUÇ: SELECT title, length FROM film
       WHERE title LIKE '%n'
       ORDER BY length DESC
       LIMIT 5
~~~
<br>

### 2. Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

~~~sql
SONUÇ: SELECT title, length FROM film
       WHERE title LIKE '%n'
       ORDER BY length ASC
       OFFSET 5
       LIMIT 5
~~~
<br>

### 3. Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

~~~sql
SONUÇ: SELECT * FROM customer
       WHERE store_id = 1
       ORDER BY last_name DESC 
       LIMIT 4
~~~
<br>

----------------------------------------------------------------------------------------------------

# <p id='Ödev 6'>ÖDEV 6</p>

### 1. Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

~~~sql
SONUÇ: SELECT AVG(rental_rate) FROM film
~~~
<br>

### 2. Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

~~~sql
SONUÇ: SELECT COUNT(*) FROM film
       WHERE title LIKE 'C%'
~~~
<br>

### 3. Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

~~~sql
SONUÇ: SELECT MAX(length) FROM film
       WHERE rental_rate = 0.99
~~~
<br>

### 4. Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

~~~sql
SONUÇ: SELECT COUNT(DISTINCT(replacement_cost)) FROM film
       WHERE length>150
~~~
<br>