## Modelagem física

### Criar banco de dados
```sql
CREATE DATABASE tecinternet_escola_ignacio CHARACTER SET utf8mb4;
```
<!-- ____________________________________________________________________ -->
### Criar tabela cursos
```sql
CREATE TABLE cursos(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria SMALLINT NOT NULL,
    professor_id INT NOT NULL
);
```
<!-- ____________________________________________________________________ -->
### Criar tabela professores
```sql
CREATE TABLE professores(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    area_de_atuacao ENUM('design','desenvolvimento','infra') NOT NULL,
    curso_id SMALLINT NOT NULL
);
```
<!-- ____________________________________________________________________ -->
### Criar tabela alunos
```sql
CREATE TABLE alunos(
    id SMALLINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(30) NOT NULL,
    data_de_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2) NOT NULL,
    segunda_nota DECIMAL(4,2) NOT NULL,
    curso_id SMALLINT NOT NULL
);
```