# ÖDEV 1

<ol>

<h3>
<li>
Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.<br>
</h3>
<h3>
<span style="color: green;"><u><b>SONUÇ:</b></u> SELECT title, description FROM film</span>
</h3>
</li><br><br>


<h3>
<li>
Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
</h3>
<h3>
<span style="color: green;"><u><b>SONUÇ:</b></u> SELECT * FROM film WHERE length>60 AND length<75</span>
</h3>
</li><br><br>


<h3>
<li>
Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
</h3>
<h3>
<span style="color: green;"><u><b>SONUÇ:</b></u> SELECT * FROM film WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99</span>
</h3>
</li><br><br>


<h3>
<li>
Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
</h3>
<h3>
<span style="color: green;"><u><b>SONUÇ:</b></u> Smith</span>
</h3>
</li><br><br>


<h3>
<li>
Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
</h3>
<h3>
<span style="color: green;"><u><b>SONUÇ:</b></u> SELECT * FROM film WHERE NOT length>50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99)</span>
</h3>
</li><br><br>

</ol>