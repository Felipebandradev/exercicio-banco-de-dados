# Resolução da Etapa 3 (CRUD)

## Consultas

1) Alunos que nasceram antes do ano 2009:
- código :
```sql
SELECT nome as Aluno, data_de_nascimento as "Data de Nascimento"  FROM alunos
     WHERE data_de_nascimento < '2009-01-01';
``` 
- Resposta Visual: <br>
![alunos que nasceram antes do ano 2009](/img/1_data_de_nascimento_menor_que_2009.png)

---

2) Média das notas de cada aluno:

- Código
```sql
SELECT nome as Aluno, primeira_nota as "1ª Nota", segunda_nota as "2ª Nota",
ROUND((( primeira_nota + segunda_nota)/ 2), 2) as "Média" FROM alunos;
```

- Resposta Visual: <br>
![Tabela com a Média dos Alunos](/img/media_dos_alunos.png)

---

3) Limite de faltas de cada curso de acordo com a carga horária. Considere o limite como 25% da carga horária:

- Código:
```sql
SELECT titulo as Curso, carga_horaria as Horas, (carga_horaria*0.25) as "Limite de faltas horas" FROM cursos ORDER BY titulo ;
```
- Resposta Visual: <br>
![Tabela com o Limite de Falta dos Alunos](/img/limite_de_falta.png)

---

4)  Mostre os nomes dos professores que são somente da área "desenvolvimento":

- Código:
```sql
SELECT nome as professor , area_de_atuacao as "Área de Atuação" FROM professores WHERE area_de_atuacao IN('Desenvolvimento');
```
- Resposta Visual: <br>
![Tabela com Professores de Desenvolvimento](/img/professores_de_desenvolvimento.png)

---

5) mostre a quantidade de professores que cada área ("design", "infra", "desenvolvimento") possui:

- Código:
```sql
SELECT area_de_atuacao as "Área de Atuação", COUNT(*) as "Qtd de Professores" FROM professores GROUP BY area_de_atuacao;
```
- Resposta Visual: <br>
![Tabela com a quantidade de professores em cada area de atuação](/img/area_de_atuacao_qtd_de_prof.png)

---

6) Mostre o nome dos alunos, o título e a carga horária dos cursos que fazem:

- Código:
```sql
SELECT
    alunos.nome as Alunos,
    cursos.titulo as Curso,
    cursos.carga_horaria as "Carga Horária"
FROM alunos INNER JOIN cursos
ON alunos.curso_id = cursos.id
ORDER BY carga_horaria; 
```

- Resposta Visual: <br>
![Tabela com os alunos cursos que fazem e a carga horária](/img/alunos_cursos_carga_horaria_exercicio_seis.png)

---

7)  Mostre o nome dos professores e o título do curso que lecionam. Classifique pelo nome do professor:

- Código:
```sql
SELECT 
     professores.nome as Professor,
     cursos.titulo as "Curso que Leciona"
FROM professores INNER JOIN cursos
ON professores.curso_id = cursos.id
ORDER BY professores.nome;
```
- Resposta Visual: <br>
![Tabela com os professores e a materia que ensina](/img/exercicio_sete.png)

---

8)  Mostre o nome dos alunos, o título dos cursos que fazem, e o professor de cada curso:

- Código:
```sql
SELECT 
     alunos.nome as Aluno,
     cursos.titulo as Curso,
     professores.nome as "Professor do curso"
FROM alunos JOIN cursos
ON alunos.curso_id = cursos.id
JOIN professores
ON cursos.professor_id = professores.id;
```

- Resposta Visual: <br>
![Tabela com os alunos, curso e professores de cada curso](/img/exercicio_oito.png)

---

9)  Mostre a quantidade de alunos que cada curso possui. Classifique os resultados em ordem descrecente de acordo com a quantidade de alunos:

- Código:
```sql
SELECT 
     cursos.titulo as Curso,
     COUNT( alunos.curso_id) as "Qtd de alunos"
FROM alunos INNER JOIN cursos
ON alunos.curso_id = cursos.id
GROUP BY cursos.titulo
ORDER BY  COUNT( alunos.curso_id)  DESC;
```

- Resposta Visual: <br>
![Tabela com os cursos e os alunos cadastrados em cada curso](/img/exercicio_nove.png)

10) Mostre o nome dos alunos, suas notas, médias, e o título dos cursos que fazem. Devem ser considerados somente os alunos de Front-End e Back-End. Mostre os resultados classificados pelo nome do aluno: 

- Código:
```sql
SELECT 
     alunos.nome as Aluno,
     alunos.primeira_nota as "1ª Nota",
     alunos.segunda_nota as "2ª Nota",
     ROUND((alunos.primeira_nota + alunos.segunda_nota)/2,2) as "Média",
     cursos.titulo as Curso
FROM alunos INNER JOIN cursos 
ON alunos.curso_id = cursos.id
WHERE cursos.id IN(1,2);

```

- Resposta Visual: <br>
![Tabela com os alunos notas e média e o curso que fazem ](/img/exercicio_dez.png)

---
11) Altere o nome do curso de Figma para Adobe XD e sua carga horária de 10 para 15:

- Código:
```sql
UPDATE cursos SET titulo = 'Adobe XD'
    WHERE id = 4;
UPDATE cursos SET carga_horaria = 15
    WHERE id = 4;
```

- Resposta Visual: <br>
![Tabela curso com adobe xd e a carga horária de 15 horas ](/img/exercicio_onze.png)

---

12) Exclua um aluno do curso de Redes de Computadores e um aluno do curso de UX/UI:

- Código:
```sql
-- id 5 = rede de computadores
DELETE FROM alunos WHERE nome = "Harley Quinn" AND curso_id = 5 ; 

-- id 3 = UX/UI
DELETE FROM alunos WHERE nome = "Zerine" AND curso_id = 3;
```

- Resposta Visual: <br>
![Tabela de alunos sem as estudantes do curso de rede de computadores e UX/UI](/img/exercicio_doze.png)

---

13) Mostre a lista de alunos atualizada e o título dos cursos que fazem, classificados pelo nome do aluno:

- Código:
```sql
SELECT
     alunos.*,
     cursos.titulo as Curso
FROM alunos INNER JOIN cursos
ON alunos.curso_id = cursos.id
ORDER BY alunos.nome;
```
- Resposta Visual: <br>
![Tabela de alunos atualizada e com o nome dos cursos](/img/exercicio_treze.png)

---

## Desafios

1)  Calcule a idade do aluno:

- Código:
```sql
SELECT
     nome as Aluno,
     data_de_nascimento as 'Data de Nascimento',
     TIMESTAMPDIFF(YEAR, data_de_nascimento, NOW())  as Idade
FROM alunos
ORDER BY Idade ;
```

- Resposta Visual: <br>
![Tabela de alunos com a idade de cada](/img/desafio_um.png)

---

2) Calcule a média das notas de cada aluno e mostre somente os alunos que tiveram a média **maior ou igual a 7**:

- Código:
```sql
SELECT 
     nome as Aluno,
     ROUND((primeira_nota + segunda_nota)/2,2) as "Média"
FROM alunos WHERE ROUND((primeira_nota + segunda_nota)/2,2)  >= 7;
```

- Resposta Visual: <br>
![Tabela de alunos com os alunos com as maiores médias](/img/desafio_dois.png)

---

3) Calcule a média das notas de cada aluno e mostre somente os alunos que tiveram a média **menor que 7**:

- Código:
```sql
SELECT 
     nome as Aluno,
     ROUND((primeira_nota + segunda_nota)/2,2) as "Média"
FROM alunos WHERE ROUND((primeira_nota + segunda_nota)/2,2)  < 7;
```

- Resposta Visual: <br>
![Tabela de alunos com os alunos com as menores médias](/img/desafio_tres.png)

4)  Mostre a quantidade de alunos com média **maior ou igual a 7**:

- Código:
```sql
SELECT 
     COUNT(*) as "Qtd de alunos"
FROM alunos WHERE ROUND((primeira_nota + segunda_nota)/2,2) >= 7;

```

- Resposta Visual: <br>
![Tabela de alunos com a quantidade de alunos com as maiores médias](/img/desafio_quatro.png)