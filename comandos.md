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
    professor_id INT NULL
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

<!-- ____________________________________________________________________ -->
-- Inclusão dos cursos (5 cursos:) Etapa 2
INSERT INTO cursos (titulo, carga_horaria) VALUES(
    'Front-End',
    40
    ),
(
    'Back-End',
    80
    ),
(
    'UX/UI Design',
    30
),
(
    'Figma',
    10
),
(
    'Redes de Computadores',
    100
);

```
<!-- ____________________________________________________________________ -->
### cadastro dos (5 professores) Etapa 2

```sql
INSERT INTO professores (nome, area_de_atuacao, curso_id) VALUES(
    'Jon Oliva',
    'área infra',
    5
    ),
(
    'Lemmy Kilmister',
    'área design',
    4
    ),
(
    'Neil Peart',
    'área design',
    3
    ),
(
    'Ozzy Osbourne',
    'área desenvolvimento',
    2
    ),
(
    'David Gilmour',
    'área desenvolvimento',
    1
    );
-- Atualização de Id´s

UPDATE cursos SET professor_id = 1 WHERE id = 5;
UPDATE cursos SET professor_id = 2 WHERE id = 4;
UPDATE cursos SET professor_id = 3 WHERE id = 3;
UPDATE cursos SET professor_id = 4 WHERE id = 2;
UPDATE cursos SET professor_id = 5 WHERE id = 1;

-- Cadastro dos alunos

INSERT INTO alunos (nome, data_de_nascimento,primeira_nota, segunda_nota, curso_id) VALUES(
    'Ignacio Neto',
    '1982-02-26',
    8,
    10,
    3
    ),
(
    'Maria Yussef',
    '1985-02-26',
    9,
    10,
    2
    ),
(
    'Robert Sheer',
    '1995-02-03',
    9,
    7,
    5
),
(
    'Rosana Uter',
    '1970-06-09',
    10,
    10,
    1
),
(
    'Vater Gustavo',
    '1955-11-19',
    9,
    9,
    4
),
(
    'Valéria Linda',
    '2005-09-26',
    4,
    7,
    2
),
(
    'Mário Calore',
    '1995-02-03',
    10,
    7,
    3
),
(
    'Ariana Grande',
    '1995-02-03',
    8,
    3,
    4
),
(
    'Michael Robert',
    '1995-02-03',
    9,
    9,
    1
),
(
    'Viviane Lima',
    '2015-01-01',
    10,
    9,
    3
);


```