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


2) Média das notas de cada aluno:

- Código
```sql
SELECT nome as Aluno, primeira_nota as "1ª Nota", segunda_nota as "2ª Nota",
ROUND((( primeira_nota + segunda_nota)/ 2), 2) as "Média" FROM alunos;
```

- Resposta Visual: <br>
![Tabela com a Média dos Alunos](/img/media_dos_alunos.png)

3) Limite de faltas de cada curso de acordo com a carga horária. Considere o limite como 25% da carga horária:

- Código:
```sql
SELECT titulo as Curso, carga_horaria as Horas, (carga_horaria*0.25) as "Limite de faltas horas" FROM cursos ORDER BY titulo ;
```
- Resposta Visual: <br>
![Tabela com o Limite de Falta dos Alunos](/img/limite_de_falta.png)

4)  Mostre os nomes dos professores que são somente da área "desenvolvimento":

```sql

```