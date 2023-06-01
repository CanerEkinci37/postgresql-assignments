# Patika PostgreSQL Assignments
#### 1

- film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```sql
                  SELECT title, description FROM film;
```

- film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
```sql
                  SELECT * FROM film
                  WHERE length > 60 AND length < 75;
```

- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
```sql
                  SELECT * FROM film
                  WHERE rental_rate = 0.99 AND (replacement_cost = 12.99 OR replacement_cost = 28.99);
```

- customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
```sql
                  SELECT * FROM customer
                  WHERE first_name = 'Mary';
```

- film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
```sql
                  SELECT * FROM film
                  WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99);
```

#### 2

- film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```sql
                  SELECT * FROM film
                  WHERE replacement_cost BETWEEN 12.99 AND 16.98;
```

- .actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```sql
                  SELECT first_name, last_name FROM actor
                  WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```

- film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

```sql
                  SELECT * FROM film
                  WHERE rental_rate IN (0.99, 2.99, 4.99) AND replacement_cost IN (12.99, 15.99, 28.99);
```


#### 3

- country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```sql
                  SELECT country FROM country
                  WHERE country LIKE 'A%a';
```

- country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```sql
                  SELECT country FROM country
                  WHERE country LIKE '%_____%';
```

- film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```sql
                  SELECT country FROM country
                  WHERE country ILIKE '%T%%T%%T%%T%';
```

- film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```sql
                  SELECT * FROM film
                  WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99;
```


#### 4

- film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

```sql
                  SELECT DISTINCT replacement_cost FROM film;
```

- film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```sql
                  SELECT COUNT(DISTINCT replacement_cost) FROM film;
```

- film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```sql
                  SELECT COUNT(title) FROM film
                  WHERE title LIKE 'T%' AND rating = 'G';
```


- country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```sql
                  SELECT COUNT(*) FROM country
                  WHERE country LIKE '_____';
```

- city tablosundaki şehir isimlerinin kaç tanesi 'R' veya r karakteri ile biter?

```sql
                  SELECT COUNT(*) FROM city
                  WHERE city LIKE 'R%' OR city LIKE '%r';
```


#### 5

- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.


```sql
                  SELECT title, length FROM film
                  WHERE title LIKE '%n'
                  ORDER BY length DESC
                  LIMIT 5;
```


- film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci(6,7,8,9,10) 5 filmi(6,7,8,9,10) sıralayınız.

```sql
                  SELECT title, length FROM film
                  WHERE title LIKE '%n'
                  ORDER BY length ASC
                  OFFSET 5
                  LIMIT 5;
```


- customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```sql
                  SELECT store_id, last_name FROM customer
                  WHERE store_id = 1
                  ORDER BY last_name DESC
                  LIMIT 4;
```


#### 6

- film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```sql
                  SELECT AVG(rental_rate) FROM film;
```

- film tablosunda bulunan filmlerden kaç tanesi 'C' karakteri ile başlar?

```sql
                  SELECT COUNT(*) FROM film
                  WHERE title LIKE 'C%';
```

- film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```sql
                  SELECT MAX(length) FROM film
                  WHERE rental_rate = 0.99;
```

- film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```sql
                  SELECT COUNT(DISTINCT replacement_cost) FROM film
                  WHERE length > 150;
```


#### 3

- film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

```sql
                  SELECT rating, COUNT(*) FROM film
                  GROUP BY rating;
```

- film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

```sql
                  SELECT replacement_cost, COUNT(*) FROM film
                  GROUP BY replacement_cost
                  HAVING COUNT(*) > 50;
```

- customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir? 

```sql
                  SELECT store_id, COUNT(*) FROM customer
                  GROUP BY store_id;
```

- city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıran country_id bilgisini ve şehir sayısını paylaşınız.

```sql
                  SELECT country_id, COUNT(*) FROM city
                  GROUP BY country_id
                  ORDER BY COUNT(*) DESC
                  LIMIT 1;
```

#### 8 

- test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

```sql
                  CREATE TABLE employee (
                    id INTEGER,
                    name VARCHAR(50),
                    birthday DATE,
                    email VARCHAR(100)
                  );
```

- Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

```sql
                  insert into employee (id, name, birthday, email) values (1, 'Michel Frangione', '1984-03-27', 'mfrangione0@histats.com');
                  insert into employee (id, name, birthday, email) values (2, 'Davon Cowton', '1952-01-05', 'dcowton1@indiegogo.com');
                  insert into employee (id, name, birthday, email) values (3, 'Emelda Antat', '1998-01-31', 'eantat2@pbs.org');
                  insert into employee (id, name, birthday, email) values (4, 'Giavani McCorrie', '1937-10-10', 'gmccorrie3@ocn.ne.jp');
                  insert into employee (id, name, birthday, email) values (5, 'Tim Basler', '1977-06-21', 'tbasler4@xing.com');
                  insert into employee (id, name, birthday, email) values (6, 'Nydia Ewan', '1947-03-17', 'newan5@angelfire.com');
                  insert into employee (id, name, birthday, email) values (7, 'Vita Benam', '2007-08-15', 'vbenam6@google.ru');
                  insert into employee (id, name, birthday, email) values (8, 'Kathe Land', '2006-04-24', 'kland7@skyrock.com');
                  insert into employee (id, name, birthday, email) values (9, 'Windham Minillo', '1961-09-07', 'wminillo8@thetimes.co.uk');
                  insert into employee (id, name, birthday, email) values (10, 'Marchelle Plues', '2000-09-08', 'mplues9@smugmug.com');
                  insert into employee (id, name, birthday, email) values (11, 'Gib Robert', '1954-11-21', 'groberta@nature.com');
                  insert into employee (id, name, birthday, email) values (12, 'Minor Datte', '1975-03-15', 'mdatteb@abc.net.au');
                  insert into employee (id, name, birthday, email) values (13, 'Annmaria Brand-Hardy', '1969-07-22', 'abrandhardyc@ow.ly');
                  insert into employee (id, name, birthday, email) values (14, 'Amery Middlewick', '1982-04-27', 'amiddlewickd@apple.com');
                  insert into employee (id, name, birthday, email) values (15, 'Fabien Patifield', '1981-12-09', 'fpatifielde@desdev.cn');
                  insert into employee (id, name, birthday, email) values (16, 'Amalea Brient', '1939-05-08', 'abrientf@amazon.de');
                  insert into employee (id, name, birthday, email) values (17, 'Gabbey Broadberrie', '1961-01-06', 'gbroadberrieg@constantcontact.com');
                  insert into employee (id, name, birthday, email) values (18, 'Lionello Klugman', '2009-09-29', 'lklugmanh@tumblr.com');
                  insert into employee (id, name, birthday, email) values (19, 'Amara Larder', '1938-02-17', 'alarderi@hao123.com');
                  insert into employee (id, name, birthday, email) values (20, 'Tyne Orris', '1959-10-12', 'torrisj@google.com.hk');
                  insert into employee (id, name, birthday, email) values (21, 'Karna Panons', '1984-03-21', 'kpanonsk@kickstarter.com');
                  insert into employee (id, name, birthday, email) values (22, 'Verney Stening', '1950-07-09', 'vsteningl@blogger.com');
                  insert into employee (id, name, birthday, email) values (23, 'Sloan Pengelley', '1958-07-18', 'spengelleym@archive.org');
                  insert into employee (id, name, birthday, email) values (24, 'Tammie Klejna', '1971-04-01', 'tklejnan@elegantthemes.com');
                  insert into employee (id, name, birthday, email) values (25, 'Miguela Houndsom', '2000-05-01', 'mhoundsomo@webeden.co.uk');
                  insert into employee (id, name, birthday, email) values (26, 'Artair Winridge', '1940-05-13', 'awinridgep@theatlantic.com');
                  insert into employee (id, name, birthday, email) values (27, 'Frank Marco', '1949-11-27', 'fmarcoq@loc.gov');
                  insert into employee (id, name, birthday, email) values (28, 'Keith Moody', '1969-09-18', 'kmoodyr@networkadvertising.org');
                  insert into employee (id, name, birthday, email) values (29, 'Fredric MacLice', '1987-02-03', 'fmaclices@cbc.ca');
                  insert into employee (id, name, birthday, email) values (30, 'Karney Hefner', '1981-02-14', 'khefnert@zdnet.com');
                  insert into employee (id, name, birthday, email) values (31, 'Joceline Yearsley', '2010-05-05', 'jyearsleyu@reuters.com');
                  insert into employee (id, name, birthday, email) values (32, 'Riccardo Yann', '2023-05-01', 'ryannv@twitpic.com');
                  insert into employee (id, name, birthday, email) values (33, 'Karlotta Sutherland', '1987-08-30', 'ksutherlandw@google.com.br');
                  insert into employee (id, name, birthday, email) values (34, 'Helge Romer', '1989-09-29', 'hromerx@usatoday.com');
                  insert into employee (id, name, birthday, email) values (35, 'Christiana Gateley', '2014-11-18', 'cgateleyy@harvard.edu');
                  insert into employee (id, name, birthday, email) values (36, 'Svend Winstone', '1938-12-08', 'swinstonez@networkadvertising.org');
                  insert into employee (id, name, birthday, email) values (37, 'Nadine Clemitt', '1989-09-23', 'nclemitt10@merriam-webster.com');
                  insert into employee (id, name, birthday, email) values (38, 'Fulvia Tarpey', '1946-02-18', 'ftarpey11@live.com');
                  insert into employee (id, name, birthday, email) values (39, 'Kessiah Wardhaw', '2012-11-01', 'kwardhaw12@uol.com.br');
                  insert into employee (id, name, birthday, email) values (40, 'Brandie Chidley', '2019-03-02', 'bchidley13@businessinsider.com');
                  insert into employee (id, name, birthday, email) values (41, 'Arlie Pochin', '1957-03-05', 'apochin14@joomla.org');
                  insert into employee (id, name, birthday, email) values (42, 'Eddy Sadlier', '1937-05-14', 'esadlier15@weebly.com');
                  insert into employee (id, name, birthday, email) values (43, 'Ursuline Alphonso', '1935-02-24', 'ualphonso16@wikimedia.org');
                  insert into employee (id, name, birthday, email) values (44, 'Mellie Wimpress', '1964-08-31', 'mwimpress17@bluehost.com');
                  insert into employee (id, name, birthday, email) values (45, 'Josephina Gerb', '1992-11-22', 'jgerb18@ask.com');
                  insert into employee (id, name, birthday, email) values (46, 'Alvera Schiefersten', '1963-06-09', 'aschiefersten19@whitehouse.gov');
                  insert into employee (id, name, birthday, email) values (47, 'Donaugh Rosone', '1986-12-21', 'drosone1a@prweb.com');
                  insert into employee (id, name, birthday, email) values (48, 'Joyan Monteaux', '1951-10-21', 'jmonteaux1b@independent.co.uk');
                  insert into employee (id, name, birthday, email) values (49, 'Ashlie Shury', '1989-01-06', 'ashury1c@w3.org');
                  insert into employee (id, name, birthday, email) values (50, 'Linnell Haley', '1936-01-13', 'lhaley1d@fema.gov');
```

- Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

```sql
                  UPDATE employee
                  SET name = 'Edited'
                  WHERE name LIKE 'G%';
                  
                  UPDATE employee
                  SET id = 99
                  WHERE name ILIKE '%A%';
                  
                  UPDATE employee
                  SET birthday = '2023-02-06'
                  WHERE name ILIKE '%k%%m%';
                  
                  UPDATE employee
                  SET email = 'none@gmail.com'
                  WHERE id BETWEEN 30 AND 39;   
                  
                  UPDATE employee
                  SET id = 1
                  WHERE name ILIKE '%V%' AND ID < 50;
```

- Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

```sql
                  DELETE FROM employee
                  WHERE id = 99 AND name ILIKE '%A%%B%';
                  
                  DELETE FROM employee
                  WHERE id = 99 AND email ILIKE '%z%';
                  
                  DELETE FROM employee
                  WHERE id IN (99, 11) AND name LIKE '__________';
                  
                  DELETE FROM employee
                  WHERE id = 99 AND email LIKE '%a%%c%';
                  
                  DELETE FROM employee
                  WHERE id BETWEEN 34 AND 99;
```

#### 9

- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
                  SELECT city.city, country.country FROM city
                  JOIN country ON city.country_id = country.country_id;
```

- customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
                  SELECT payment.payment_id, customer.first_name, customer.last_name FROM payment
                  JOIN customer ON payment.customer_id = customer.customer_id;
```

- customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

```sql
                  SELECT rental.rental_id, customer.first_name, customer.last_name FROM customer
                  JOIN rental ON customer.customer_id = rental.customer_id;
```


#### 10

- city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

```sql
                  SELECT city.city, country.country FROM country
                  LEFT JOIN city ON city.country_id = country.country_id;
```

- customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

```sql
                  SELECT customer.first_name, customer.last_name, payment.payment_id FROM payment
                  RIGHT JOIN customer ON customer.customer_id = payment.customer_id;
```

- customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

```sql
                  SELECT customer.first_name, customer.last_name, rental.rental_id FROM rental
                  FULL JOIN customer ON customer.customer_id = rental.customer_id;
```


#### 11 

- actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

```sql
                  (
                  SELECT first_name FROM actor
                  )
                  UNION
                  (
                  SELECT first_name FROM customer
                  );
```

- actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

```sql
                  (
                  SELECT first_name FROM actor
                  )
                  INTERSECT
                  (
                  SELECT first_name FROM customer
                  );
```

- actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

```sql
                  (
                  SELECT first_name FROM actor
                  )
                  EXCEPT
                  (
                  SELECT first_name FROM customer
                  );
```

- İlk 3 sorguyu tekrar eden veriler için de yapalım.

```sql
                  (
                  SELECT first_name FROM actor
                  )
                  UNION ALL
                  (
                  SELECT first_name FROM customer
                  );
                  
                  (
                  SELECT first_name FROM actor
                  )
                  INTERSECT ALL
                  (
                  SELECT first_name FROM customer
                  );
                  
                  (
                  SELECT first_name FROM actor
                  )
                  EXCEPT ALL
                  (
                  SELECT first_name FROM customer
                  );
```

