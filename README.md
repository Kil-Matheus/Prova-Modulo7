# Prova-Modulo7

Primeiramente eu comecei criando as intâncias EC2 e o RDS
* front-prova
* back-prova
* db-prova

Nas instâncias, eu crie para cada uma delas um elastic IP para que os endereços não ficassem trocando, depois eu fui editar os códigos.

Comecei primeiramente alterando os códigos do backend que fazem conexão com o Banco RDS, trocando os endpoint, user e senha e tambem a porta que a aplicação roda de 8000 para 80. Após isso eu fiz conexão com o DBeaver para testar a conexão. Com ela funcionado, eu tentei executar os códigos de SQL para criar as tabelas oferecidas no repositório do Murilo, mas por algumo motivo elas não funcionaram. Então eu copiei o código SQL:

```
DROP TABLE IF EXISTS minhas_notas ;

    CREATE TABLE minhas_notas (
        id SERIAL PRIMARY KEY,
        titulo VARCHAR(255) NOT NULL,
        descricao TEXT NOT null,
        data_criacao TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP
    );
```

E executei diretamente no DBeaver e funcionou, o print esta na pasta .zip. Depois disso eu criei um docker file para o backend e subi no Git (https://github.com/Kil-Matheus/Prova-Modulo7). De lá, eu fui para o ec2 back-prova, atualizei o apt, baixei o docker na máquina e depois clonei o meu repositório, entrei na pasta backend e criei a imagem e rodei ela na porta 80 'sudo docker run 80:80 back'

Depois disso passei para o Front que eu alterei as seguinte informações. Após ter alocado um elastic api em cada ec2, eu peguei o endereço do backend e fui alterando todas as rotas de requisição para o seguinte endereço:

```
3.225.207.236
```

E como isso eu rodei primeiramente localmente para ver se as portas estavam certas com o backend, vendo que a aplicação já funcionava, o rds estava funcionado, o front estava rodando (por algum motivo diferente no Apache2 e localmente correto) e o back interconectado nos 2. Eu abri o ec2 do front, baixei o Apache2 dei um 'cd /var/www/index/' e o arquivo de lá eu editei, apaguei tudo e colei o front da aplicação oferecido pelo Murilo lá, como eu não sabia como iria subir todos os arquivos, eu juntei tudo, o css e o javascript tudo no html e rodei de lá

Eu tirei vários prints e gravei um vídeo, segue a baixo a aplicação rodando:

https://drive.google.com/file/d/1_H7xXOkLOxlUSEZQTVYGDwGBHWAyGO49/view?usp=sharing