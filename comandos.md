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
<!-- ____________________________________________________________________ -->
### Criação da chave estrangeira (relacionamento entre as tabelas)

```sql
-- Criação das chaves estrangeiras (Exercício)
ALTER TABLE cursos 
    ADD CONSTRAINT fk_cursos_professores1
    FOREIGN KEY (professor_id) REFERENCES professores(id);

ALTER TABLE professores 
    ADD CONSTRAINT fk_professores_cursos1
    FOREIGN KEY (curso_id) REFERENCES cursos(id);

ALTER TABLE alunos 
    ADD CONSTRAINT fk_alunos_cursos
    FOREIGN KEY (curso_id) REFERENCES cursos(id);

```
