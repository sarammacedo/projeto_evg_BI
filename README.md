<img width="1369" height="725" alt="imagem" src="https://github.com/user-attachments/assets/0f38c544-cb25-4117-ab21-4862db01f0b7" />
![Modelagem dos dados evg]("imagem.png")

# Projeto de Modelagem de Dados - Matrículas

## 📌 Visão Geral do Projeto
Este repositório contém o projeto de modelagem e estruturação da base de dados de matrículas em cursos, desenvolvido com o intuito de organizar e otimizar o acesso às informações analíticas.

---

## 🛠️ Modelagem de Dados (DrawDB)

A modelagem foi estruturada seguindo o padrão **Star Schema (Esquema em Estrela)**, onde uma tabela de fatos centraliza as métricas e eventos de matrícula, relacionando-se com diversas tabelas dimensão.

![Diagrama de Modelagem de Dados - DrawDB](assets/diagrama.png)

### 📊 Estrutura do Modelo

#### **Tabela Fato**
* **`fato_matriculas`**: Armazena as métricas e transações das matrículas, contendo as chaves estrangeiras (FKs) que conectam às dimensões, além das datas de início/fim e situação da matrícula.

#### **Tabelas Dimensão**
1. **`dim_turma`**: Informações sobre as turmas (`cod_turma`, nome, modalidade, situação).
2. **`dim_curso`**: Detalhes dos cursos (`cod_curso`, nome, carga horária, instituição, temática).
3. **`dim_pessoa`**: Dados cadastrais dos alunos (`codigo_pessoa`, município, UF, nacionalidade, sexo, idade, telefone, e-mail).
4. **`dim_conteudista`**: Dados dos autores/conteudistas do material (`cod_conteudista`, nome, e-mail).
5. **`dim_poder`**: Classificação por poder governamental (`cod_poder`, descrição do poder).
6. **`dim_esfera`**: Classificação por esfera de atuação (`cod_esfera`, descrição da esfera).

---

## ❓ Perguntas de Negócio Respondidas pelo Modelo

1. **Qual é o perfil demográfico dos alunos matriculados?**
   * *Relacionamento:* `fato_matriculas` ↔ `dim_pessoa`
   * Permite analisar distribuição por sexo, idade, município, UF e nacionalidade.

2. **Quais são os cursos e turmas com maior volume de matrículas?**
   * *Relacionamento:* `fato_matriculas` ↔ `dim_curso` / `dim_turma`
   * Permite avaliar o engajamento por modalidade, temática e carga horária.

3. **Qual a distribuição de alunos por Poder e Esfera governamental?**
   * *Relacionamento:* `fato_matriculas` ↔ `dim_poder` / `dim_esfera`
   * Identifica a representatividade dos setores público/privado nas formações.

---

