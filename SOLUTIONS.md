
# VIT3 Database-Module-Week9
### Not:Konu anlatiminda bahsedilen, derse tedarik ederek geleceginiz data uzerinden asagidaki sorgulamalari yapmaniz gerekmektedir ;
### *Note: You are required to perform the following queries on the data you will procure by attending the lecture;*
* 1) İlk isminde Nick, Ed ve Jennifer adları bulunan aktörlerin adını ve soyadını gösterin. *(Show the first name and last name of actors whose first names are Nick, Ed, and Jennifer.)*
```sql
SELECT first_name, last_name 
FROM actor 
WHERE first_name='Nick' or first_name='Ed' or first_name='Jennifer';
```
* 2) İlk isminde adları Ed, Nick ve Jennifer olan aktörün sadece soyadını gösterin. *(Show only the last name of the actor whose first names are Ed, Nick, and Jennifer.)*
```sql
SELECT last_name 
FROM actor 
WHERE first_name='Nick' or first_name='Ed' or first_name='Jennifer';
```
* 3) Adres tablosunun bütün ayrıntılarını gösterin. *(Show all details of the address table.)*
```sql
SELECT * FROM address;
```
* 4) Adres tablosunda ilçe ve telefonu (district & phone) azalan sırada gösterin *(Display district and phone from the address table in descending order.)*
```sql
SELECT district, phone 
FROM address 
ORDER BY district DESC;
```
* 5) Film ve envanter tablosundaki film_id’yi kullanarak, Film tablosundan film_id’yi, title’ i ve Envanter tablosundan envanter_id'sini gösterin. *(Using film_id from the Film and Inventory tables, display film_id and title from the film table, and inventory_id from the inventory table.)*
```sql
SELECT film.film_id, inventory.inventory_id, film.title 
FROM film 
INNER JOIN inventory ON film.film_id = inventory.film_id;
```
* 6) Envanter tablosu ve rental tablosundan oluşan ilk 5 satırı gösterin. *(Display the first 5 rows from the Inventory table combined with the Rental table.)*
```sql
SELECT * 
FROM inventory 
JOIN rental ON inventory.inventory_id = rental.inventory_id
LIMIT 5;
```
* 7) Rental ve Payment tablolarından oluşan amount a göre azalan olarak sıralanmış rental_id, rental_date, payment_id ‘den oluşan ilk 10 satırı gösterin. *(Show the first 10 rows consisting of rental_id, rental_date, and payment_id sorted by amount in descending order from the Rental and Payment tables.)*
```sql
SELECT rental.rental_id, rental.rental_date, payment.payment_id, payment.amount
FROM rental 
INNER JOIN payment ON rental.rental_id = payment.rental_id 
ORDER BY amount DESC LIMIT 10;
```
* 8) Actor tablosunda actor_id 'nin boş olduğu satırların diğer detaylarını gösteriniz. *(Show details of rows in the Actor table where actor_id is empty.)*
```sql
SELECT * 
FROM actor 
WHERE actor_id IS NULL;
```
* 9) Actor tablosunda actor_id 'nin boş olmadığı satırların diğer detaylarını gösteriniz. *(Show details of rows in the Actor table where actor_id is not empty.)*
```sql
SELECT * 
FROM actor 
WHERE actor_id IS NOT NULL;
```
* 10) Film tablosunda boş olmayan satırların sayısını bulunuz. *(Find the number of non-empty rows in the Film table.)*
```sql
SELECT COUNT(*) 
FROM film 
WHERE film_id IS NOT NULL;
```
* 11) Payment tablosundan amount’un toplamını çıktı başlığı sum_amt olarak gösteriniz. *(Show the total of amount from the Payment table with the output title as sum_amt.)*
```sql
SELECT SUM(amount) 
AS sum_amt 
FROM payment;
```
* 12) Payment tablosundan maximum ve minimum amount ‘u gösteriniz. *(Display the maximum and minimum amount from the Payment table.)*
```sql
SELECT 
MAX(amount) AS max_amount, 
MIN(amount) AS min_amount 
FROM payment;
```
