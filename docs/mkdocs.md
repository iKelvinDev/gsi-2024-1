# Criação e Configuração do Site EStático (MkDocs)

## Instalação

Para instalar o MkDocs, utilize o comando:

```
pip3 install mkdocs
```

Crie um projeto MkDocs e gere as páginas estáticas:

```
mkdocs new my-project
cd my-project
mkdocs build
```

## Configuração

Edite o arquivo de configuração do Apache para adicionar o site:

```
micro /etc/apache2/sites-available/docs.kelvin.lab.conf
```

Edite o arquivo de configuração:

```
<VirtualHost *:80>
    ServerName docs.kelvin.lab
    DocumentRoot /home/madrid/projetos/my-docs/site

    <Directory /home/madrid/projetos/my-docs/site>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/docs.kelvin.lab.error.log
    CustomLog ${APACHE_LOG_DIR}/docs.kelvin.lab.access.log combined
</VirtualHost>
```
Com essa configuração definiu o nome do servidor e também será possível acessar
a documentação no diretório especificado.

Agora ative o site e recarregue o Apache2:

```
sudo a2ensite docs.kelvin.lab.conf
sudo systemctl reload apache2
```

Edite o arquivo `mkdocs.yml` para adicionar suas páginas e configurar o site:

```
site_name: Documentação da Atividade Avaliativa
nav:
    - Home: index.md
    - Página 1: pagina1.md
    - Página 2: pagina2.md
    - Página 3: pagina3.md
    - Página 4: pagina4.md
    - Página 5: pagina5.md
```

## Construção do Site

Construa o site para gerar os estáticos que foram definidos:

```
mkdocs build
```

## Servir o Site Localmente

Para visualizar o site localmente, use:

`mkdocs serve`