# Criação e Configuração do Site Dinâmico (WordPress)

## Configuração

Configure o MariaDB:

`mysql_secure_installation`

Crie um banco de dados para o WordPress:

```
mysql -u root -p
CREATE DATABASE wordpress;
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost' IDENTIFIED BY 'Ifrn.2024';
FLUSH PRIVILEGES;
EXIT;
```
## Instalação

Acesse `http://www.kelvin.lab` e siga as instruções para configurar o WordPress. Utilize as seguintes credenciais para o banco de dados:

- Database Name: wordpress
- Username: wpuser
- Password: Ifrn.2024