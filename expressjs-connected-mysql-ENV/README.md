# nodejs sederhana dengan framework expressjs #

---


instalasi expressjs:

    > npm install express



pastikan sebelumnya telah menginstall paket diperlukan yaitu :

- mysql

    - cara install

        $ npm install mysql

        $ npm install dotenv

    - tampilkan list paket
    
        $ npm list

            ├── dotenv@16.0.3

            ├── express@4.18.0
        
            └── mysql@2.18.1



periksa file json dan buat file js secara manual serta isinya.

- package.json

- app.js
  
- .env

---

		❯ cat .env

	    DB_HOST=127.0.0.1
	    DB_USER=root
	    DB_PASSWORD=password
	    DB_DATABASE=ujimysqlkudb
	    DB_PORT=3309
	    DB_INSECUREAUTH=true

---

jalankan (command) :

    ❯ node app.js
        op:
        Server running on port 3000




---


desclimer:

saat menjalankan pertama kali pada container mysql maka akan terdapat error sebagai berikut:

    ❯ node app.js


Server berjalan pada port 3000
Koneksi ke database gagal:  Error: ER_NOT_SUPPORTED_AUTH_MODE: Client does not support authentication protocol requested by server; consider upgrading MySQL client

untuk mengatasi hal tersebut lakukan langkah berikut:


    ❯ mysql -h 127.0.0.1 -P 3309 -u root -p --ssl-mode=DISABLED
        mysql> ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
        Query OK, 0 rows affected (0.03 sec)



        mysql> use ujimysqlkudb;
        
        mysql> select * from users;
    
        +------+---------+--------+
        | id   | nama    | alamat |
        +------+---------+--------+
        |    1 | andara  | jaksel |
        |    2 | sukiman | bekasi |
        +------+---------+--------+
        
        2 rows in set (0.00 sec)

---

### lanjut coba jalankan kembali aplikasi

    ❯ node app.js

        Server berjalan pada port 3000
        Terhubung ke database MySQL

### menampilkan hasil pada browser:

    http://localhost:3000/users

    output :
        [{"id":1,"nama":"andara","alamat":"jaksel"},{"id":2,"nama":"sukiman","alamat":"bekasi"}]


---
