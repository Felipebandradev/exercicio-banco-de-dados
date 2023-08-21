# Resolução da Etapa 2 (CRUD) 

# Cadastro-Geral

## CREATE

###  Cursos

- código
```sql
INSERT INTO cursos(
    titulo, carga_horaria  
) 
VALUES (
    "Front-End",  40
),(
    "Back-End", 80
),(
    "UX/UI",  30
),(
    "Figma", 10
),(
    "Rede de Computadores", 100
);
```

- resultado visual
![Tabela com os cursos já cadastrados](/img/dados-tabela-cursos.png)

### Professores

- código
```sql
INSERT INTO professores (
    nome, area_de_atuacao, curso_id  
) 
VALUES (
    "Jon Oliva",  'Infra', 5
),(
    "Lemmy Kilmister", 'Desing', 4
),(
    "Neil Peart", 'Desing', 3
),(
    " Ozzy Osbourne", 'Desenvolvimento',2
),(
    "David Gilmour", 'Desenvolvimento',1
);
```
- resultado visual <br>
![Tabela com os professores já cadastrados](/img/dados-tabela-professores.png)

### Alunos

- código
```sql
INSERT INTO alunos (
    nome, data_de_nascimento, primeira_nota, segunda_nota, curso_id  
) 
VALUES (
    "Harley Quinn", '1992-08-10', 10.00, 7.5, 5
),(
    "Melissa", '1999-03-04', 3.5, 2.1, 2
),(
    "Elielison", '1990-03-12', 1.5, 8.0, 4
),(
    "Robôcop", '2000-02-15', 7.7, 8.8, 4
),(
    "Renata", '1955-08-21',8.6, 9.5, 3
),(
    "Seraphine", '2007-09-05', 10.00, 5.0, 5
),(
    "Zerine", '1998-01-17', 4.5, 3.0, 3
),(
    "Katarina", '1968-10-09', 9.5, 8.7, 2
),(
    "Alineane", '1988-12-28', 9.9, 8.5, 1
),(
    "Josefina",'1973-11-18', 2.0, 1.5, 1
);
```

- resultado visual <br>
![Tabela com alunos ja cadastrados](/img/dados-tabela-alunos.png)

---
## UPDATE

### Colocando os Professores nos Cursos

- código
```sql
-- Front-End
UPDATE cursos SET professor_id = 5 WHERE id = 1;

-- Back-End
UPDATE cursos SET professor_id = 4 WHERE id = 2;

-- UX/UI
UPDATE cursos SET professor_id = 3 WHERE id = 3;

-- Figma
UPDATE cursos SET professor_id = 2 WHERE id = 4;

-- Rede de computadores
UPDATE cursos SET professor_id = 1 WHERE id = 5;
```

- Resultado visual <br>
![Professor id Cadastrado](/img/professores_id_cadastrado.png)
