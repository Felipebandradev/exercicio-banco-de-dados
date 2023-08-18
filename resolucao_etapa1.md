# Resolução da etapa 1 

## Modelagem logica

!["Modelo lógico do banco de dados com a tabela cursos, professores, alunos."](/img/modelagem_logica_finalizada.png)

---
## Modelagem física

```sql

-- Criação do Banco de dados
CREATE DATABASE tecinternet_escola_felipe_barbosa CHARACTER SET utf8mb4;

-- Criação das Tabelas

-- Cursos
CREATE TABLE cursos (
    id TINYINT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL,
    carga_horaria TINYINT NOT NULL,
    professor_id TINYINT NULL 
);

-- Professores
CREATE TABLE professores(
    id TINYINT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    area_de_atuacao ENUM('Desing','Desenvolvimento','Infra'),
    curso_id TINYINT NOT NULL    
);

-- Alunos
CREATE TABLE alunos(
    id TINYINT PRIMARY KEY NOT NULL AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    data_de_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2) NOT NULL,
    segunda_nota DECIMAL(4,2) NOT NULL,
    curso_id TINYINT NOT NULL    
);

-- Criação das Chaves estrangeiras
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