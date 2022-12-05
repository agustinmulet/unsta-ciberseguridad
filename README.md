# UNSTA - Diplomatura en Desarrollo seguro de aplicaciones

## Grupo 2

### Objetivo 1

Nota: Se utilizó MySQL como DBMS.

#### Requisitos:

- Tener [Docker Desktop](https://www.docker.com/products/docker-desktop/) instalado (o alguna alternativa).

#### Instrucciones:

1. Correr MySQL usando Docker:

```bash
docker run --name mysql-grupo2 -p 3306:3306 -v ~/MySQL:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=password1 -e MYSQL_DATABASE=mydb -d mysql
```

2. Ingresar al container de MySQL corriendo lo siguiente en una terminal:

```bash
docker exec -it mysql-grupo2 bash
```

3. Una vez dentro del container, descargaremos archivos que nos serán útiles luego:

```bash
curl https://raw.githubusercontent.com/al34n1x/DataScience/master/data/BankChurners.csv -o /var/lib/mysql-files/data.csv
curl -LJO https://gist.github.com/agustinmulet/2a492587d19d89cee7d91b014dc18b9c/raw/f0b9bd8d89158dbdcb9fb8350792536ca1b8c807/grupo2.sql
```

4. Usaremos el comando `mysql` para trabajar correr contra nuestra DB el script SQL descargado anteriormente:

```bash
mysql -u root -p mydb < /grupo2.sql # Ingresar password1 como password
```

5. Nuestro script crea una tabla `customers` y una vista `customers_mask` si es que no existen y popula nuestra DB con la data del archivo provisto.

Luego podemos chequear la data enmascarada ingresando a `mysql` haciendo un `SELECT`. Ingresamos a `mysql` de la siguiente manera:

```bash
mysql -u root -p mydb # Ingresar password1 como password
```

Y una vez dentro de `mysql`:

```sql
SELECT * from customers_mask LIMIT 5;
```
