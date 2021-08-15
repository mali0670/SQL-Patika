# PostgreSQL ödevleri

<a href='#Ödev 1'>ÖDEV 1</a><br>
<a href='#Ödev 2'>ÖDEV 2</a><br>
<a href='#Ödev 3'>ÖDEV 3</a><br>
<a href='#Ödev 4'>ÖDEV 4</a><br>
<a href='#Ödev 5'>ÖDEV 5</a><br>
<a href='#Ödev 6'>ÖDEV 6</a><br>
<a href='#Ödev 7'>ÖDEV 7</a><br>
<a href='#Ödev 8'>ÖDEV 8</a><br>
<a href='#Ödev 9'>ÖDEV 9</a><br><br><br>

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

----------------------------------------------------------------------------------------------------

# <p id='Ödev 7'>ÖDEV 7</p>

### 1. Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

~~~sql
SONUÇ: SELECT rating FROM film
       GROUP BY rating
~~~
<br>

### 2. Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

~~~sql
SONUÇ: SELECT replacement_cost, COUNT(*) FROM film
       GROUP BY replacement_cost
       HAVING COUNT(*)>50
~~~
<br>

### 3. Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

~~~sql
SONUÇ: SELECT store_id, COUNT(*) FROM customer
       GROUP BY store_id
~~~
<br>

### 4. City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

~~~sql
SONUÇ: SELECT country_id, COUNT(*) FROM city
       GROUP BY country_id
       ORDER BY COUNT(*) DESC
       LIMIT 1
~~~
<br>

----------------------------------------------------------------------------------------------------

# <p id='Ödev 8'>ÖDEV 8</p>

### 1. Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

~~~sql
SONUÇ: CREATE TABLE employee(
	id SERIAL PRIMARY KEY,
	name VARCHAR(50) NOT NULL,
	email VARCHAR(100),
	birthday DATE
);
~~~
<br>

### 2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

~~~sql
SONUÇ: insert into employee (name, email, birthday) values ('Chaim Arnott', 'carnott0@blog.com', null);
insert into employee (name, email, birthday) values ('Eddi Mabbe', 'emabbe1@dmoz.org', '1995/11/13');
insert into employee (name, email, birthday) values ('Rees Kays', null, null);
insert into employee (name, email, birthday) values ('Cristabel Sheasby', 'csheasby3@yellowbook.com', '1934/04/21');
insert into employee (name, email, birthday) values ('Ellwood Deering', null, '1941/06/25');
insert into employee (name, email, birthday) values ('Gabi Pay', null, '1937/05/17');
insert into employee (name, email, birthday) values ('Drusy Lambell', 'dlambell6@washingtonpost.com', '1980/12/13');
insert into employee (name, email, birthday) values ('Reagan Whimper', 'rwhimper7@amazonaws.com', '1983/11/21');
insert into employee (name, email, birthday) values ('Harrietta Corbett', 'hcorbett8@examiner.com', null);
insert into employee (name, email, birthday) values ('Cheston Dalloway', 'cdalloway9@cloudflare.com', '1920/06/03');
insert into employee (name, email, birthday) values ('Tabatha Lovat', 'tlovata@indiatimes.com', '1975/09/23');
insert into employee (name, email, birthday) values ('Waldon Parnham', null, '1944/02/14');
insert into employee (name, email, birthday) values ('Denyse Gosnay', 'dgosnayc@epa.gov', '1933/02/11');
insert into employee (name, email, birthday) values ('Vonny Pullin', 'vpullind@yellowbook.com', '1931/12/03');
insert into employee (name, email, birthday) values ('Panchito Mewburn', 'pmewburne@apache.org', '1989/01/17');
insert into employee (name, email, birthday) values ('Prudy Rikel', 'prikelf@dot.gov', null);
insert into employee (name, email, birthday) values ('Beatriz Tabourel', 'btabourelg@oracle.com', null);
insert into employee (name, email, birthday) values ('Karney Pablos', 'kpablosh@chronoengine.com', null);
insert into employee (name, email, birthday) values ('Clarisse McEnteggart', 'cmcenteggarti@archive.org', null);
insert into employee (name, email, birthday) values ('Venus Birtchnell', 'vbirtchnellj@surveymonkey.com', '1951/04/14');
insert into employee (name, email, birthday) values ('Christoforo Milbourn', 'cmilbournk@adobe.com', '1912/08/28');
insert into employee (name, email, birthday) values ('Anastasia Olesen', 'aolesenl@123-reg.co.uk', '1958/09/26');
insert into employee (name, email, birthday) values ('Corella Thomasset', 'cthomassetm@spiegel.de', '1904/06/21');
insert into employee (name, email, birthday) values ('Jimmy Viste', 'jvisten@4shared.com', '1908/12/25');
insert into employee (name, email, birthday) values ('Kali Sircombe', 'ksircombeo@nih.gov', '1959/08/23');
insert into employee (name, email, birthday) values ('Frank Yakunchikov', 'fyakunchikovp@github.com', null);
insert into employee (name, email, birthday) values ('Rowena Quinby', 'rquinbyq@pbs.org', '1910/10/09');
insert into employee (name, email, birthday) values ('Francisca Capeling', 'fcapelingr@newyorker.com', '1988/06/18');
insert into employee (name, email, birthday) values ('Sigismondo Ruffle', 'sruffles@vistaprint.com', '1949/10/16');
insert into employee (name, email, birthday) values ('Hamil MacAlpine', 'hmacalpinet@digg.com', '1981/02/01');
insert into employee (name, email, birthday) values ('Zeb Uridge', 'zuridgeu@jugem.jp', '1971/05/08');
insert into employee (name, email, birthday) values ('Myrtle Harmour', 'mharmourv@chicagotribune.com', '1987/01/01');
insert into employee (name, email, birthday) values ('Mommy Quince', 'mquincew@newyorker.com', null);
insert into employee (name, email, birthday) values ('Angelia Trunks', 'atrunksx@constantcontact.com', null);
insert into employee (name, email, birthday) values ('Giff Rockwill', 'grockwilly@biglobe.ne.jp', '1952/08/01');
insert into employee (name, email, birthday) values ('Calla Bartlett', 'cbartlettz@so-net.ne.jp', '1976/09/04');
insert into employee (name, email, birthday) values ('Fidelity Searsby', 'fsearsby10@marriott.com', '1917/01/30');
insert into employee (name, email, birthday) values ('Enos Surmeyer', 'esurmeyer11@mapy.cz', '1958/11/24');
insert into employee (name, email, birthday) values ('Fleurette Goodlud', 'fgoodlud12@irs.gov', '1903/04/27');
insert into employee (name, email, birthday) values ('Allie Canon', 'acanon13@oaic.gov.au', '1911/01/31');
insert into employee (name, email, birthday) values ('Hart Brewer', 'hbrewer14@typepad.com', '1984/12/30');
insert into employee (name, email, birthday) values ('Gradey Lamport', 'glamport15@army.mil', null);
insert into employee (name, email, birthday) values ('Diego Monro', 'dmonro16@alibaba.com', '1924/01/07');
insert into employee (name, email, birthday) values ('Kelcy Eakly', 'keakly17@youtube.com', '1974/08/16');
insert into employee (name, email, birthday) values ('Flossie Castell', 'fcastell18@amazon.de', '1973/06/09');
insert into employee (name, email, birthday) values ('Gwendolin Garralts', 'ggarralts19@washingtonpost.com', '1912/02/20');
insert into employee (name, email, birthday) values ('Evaleen Rudkin', null, '1970/02/01');
insert into employee (name, email, birthday) values ('Irita Thornthwaite', 'ithornthwaite1b@ning.com', '1924/11/29');
insert into employee (name, email, birthday) values ('Doreen Testro', 'dtestro1c@hugedomains.com', '1954/07/19');
insert into employee (name, email, birthday) values ('Alexis Kleingrub', null, '1902/04/07');
~~~
<br>

### 3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

~~~sql
SONUÇ: UPDATE employee
       SET name = 'Chaim',
       email = 'xxx@yyy.com'
       WHERE id = 1;

       UPDATE employee
       SET birthday = '2021-01-01'
       WHERE name = 'Cheston Dalloway';

       UPDATE employee
       SET name = 'Charles Dickens'
       WHERE birthday = '1975-09-23';

       UPDATE employee
       SET birthday = '1994-12-31',
       email = 'emabbe123@dmoz.org'
       WHERE name= 'Eddi Mabbe';

       UPDATE employee
       SET birthday = '1943-05-15',
       email = 'chaim@chaim.org'
       WHERE name= 'Chaim';
~~~
<br>

### 4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

~~~sql
SONUÇ: DELETE FROM employee
       WHERE name = 'Chaim';

       DELETE FROM employee
       WHERE birthday = '1937-05-17';

       DELETE FROM employee
       WHERE email = 'rwhimper7@amazonaws.com';

       DELETE FROM employee
       WHERE id = 3;

       DELETE FROM employee
       WHERE id< 12;
~~~
<br>

----------------------------------------------------------------------------------------------------

# <p id='Ödev 9'>ÖDEV 9</p>

### 1. City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

~~~sql
SONUÇ: SELECT city, country FROM city
INNER JOIN country ON  city.country_id =      country.country_id
~~~
<br>

### 2. Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

~~~sql
SONUÇ: SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment
INNER JOIN customer ON  customer.customer_id = payment.customer_id
~~~
<br>

### 3. Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.


~~~sql
SONUÇ: SELECT rental_id, first_name, last_name FROM rental
INNER JOIN customer ON  customer.customer_id = rental.customer_id
~~~
<br>