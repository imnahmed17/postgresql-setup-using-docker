# PostgreSQL setup using Docker

Here, I have given the complete process of PostgreSQL setup using Docker.

**Clone this repository:**
```bash
git clone https://github.com/imnahmed17/postgresql-setup-using-docker.git
cd postgresql-setup-using-docker
```

**PostgreSQL setup:**
```bash
docker-compose up -d
```
To find containers name and ports:
```bash
docker ps -a
```
To stop docker containers:
```bash
docker-compose down
```
To remove exited containers:
```bash
docker container prune
y
```
Now open your browser and type `http://localhost:8000` into the url to access PostgreSQL. For login give `Email: admin@user.com` and `Password: adminuser`. After that, right click on `Server > Register > Server` in left sidemenu. In general tab give type any name you want as Server name (ex:- server01). In connection tab give `Host name: postgres, Username: myuser, Password: mypassword` and save it. Then expand your server name and create a database right clicking on `Databases`. For writing database queries open `Query Tool`. To open `Query Tool` right click on your database name. Let's create a table and insert some data into it.
```bash
CREATE TABLE Student (  
    Student_id SERIAL PRIMARY KEY,  
    Student_name VARCHAR(100) NOT NULL,
    Student_age INT NOT NULL,
	Student_address TEXT NOT NULL
);

INSERT INTO Student 
(Student_id, Student_name, Student_age, Student_address)
VALUES  
(1, 'Anderson', 14, 'Dhaka'),
(2, 'Smith', 12, 'Khulna');
(3, 'Jack', 15, 'Rajshahi');
```

**Database backup:**

To backup your database, right click on your database name select `Backup...`. Then click on the file icon. Type any name (ex:- new) and save it as sql format.

**Copy database backup file from container to local:**

To navigate your `new.sql` file write below commands:
```bash
docker cp container_id:/src_path/target_file target_file
```
Ex:-
```bash
docker cp 79298332506d:/var/lib/pgadmin/storage/admin_user.com/new.sql new.sql
```
To delete database backup file or folder after coping it:
```bash
docker exec -it container_id sh
cd /file_path
ls
rm -f file_name
rm -rf "folder name"
```
Ex:-
```bash
docker exec -it 79298332506d sh
cd /var/lib/pgadmin/storage/admin_user.com
ls
rm -f new.sql
```