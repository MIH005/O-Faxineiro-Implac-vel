# 📚 Sistema de Gerenciamento de Biblioteca

Este projeto implementa um sistema básico de gerenciamento de uma biblioteca com banco de dados normalizado. O banco foi criado para organizar informações sobre livros, autores e editoras, utilizando boas práticas de modelagem relacional e comandos SQL avançados.

---

## 🚀 Funcionalidades

- **Criação do banco de dados**: Um banco chamado `Biblioteca` é criado para armazenar as tabelas.
- **Tabela de Livros**: Informações sobre livros, como título, ano de publicação e ISBN.
- **Tabelas normalizadas**:
  - **Autores**: Informações separadas sobre os autores dos livros.
  - **Editoras**: Informações separadas sobre as editoras.
- **Relacionamentos**: Uso de chaves estrangeiras para conectar `Livros`, `Autores` e `Editoras`.
- **Correção de erros no script inicial**: Ajustes no uso de `AUTO_INCREMENT`, remoção de colunas desnecessárias e inserção de dados normalizados.
- **Inserção de dados**: Exemplos de livros, autores e editoras, além de um script para normalizar e adicionar novos registros.

---

## 📂 Estrutura do Banco de Dados

### Tabelas
1. **Livros**:
   - `livro_id` (Primary Key, AUTO_INCREMENT)
   - `titulo` (Título do livro)
   - `ano_publicacao` (Ano de publicação)
   - `isbn` (Código ISBN do livro)
   - `autor_id` (Foreign Key → `Autores.autor_id`)
   - `editora_id` (Foreign Key → `Editoras.editora_id`)

2. **Autores**:
   - `autor_id` (Primary Key, AUTO_INCREMENT)
   - `nome_autor` (Nome do autor)

3. **Editoras**:
   - `editora_id` (Primary Key, AUTO_INCREMENT)
   - `nome_editora` (Nome da editora)

---

## 🛠️ Scripts SQL

### 1️⃣ Criação do Banco de Dados
```sql
CREATE DATABASE IF NOT EXISTS Biblioteca;
USE Biblioteca;
```

### 2️⃣ Criação das Tabelas
#### Livros
```sql
CREATE TABLE IF NOT EXISTS Livros (
    livro_id INT AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(255) NOT NULL,
    ano_publicacao INT,
    isbn VARCHAR(13),
    autor_id INT,
    editora_id INT,
    FOREIGN KEY (autor_id) REFERENCES Autores(autor_id),
    FOREIGN KEY (editora_id) REFERENCES Editoras(editora_id)
);
```

#### Autores
```sql
CREATE TABLE IF NOT EXISTS Autores (
    autor_id INT AUTO_INCREMENT PRIMARY KEY,
    nome_autor VARCHAR(255) NOT NULL
);
```

#### Editoras
```sql
CREATE TABLE IF NOT EXISTS Editoras (
    editora_id INT AUTO_INCREMENT PRIMARY KEY,
    nome_editora VARCHAR(255) NOT NULL
);
```

### 3️⃣ Inserção de Dados
#### Populando a Tabela Autores
```sql
INSERT INTO Autores (nome_autor) VALUES
('John Green'),
('J.K. Rowling'),
('J.R.R. Tolkien'),
('J.D. Salinger'),
('George Orwell'),
('Rick Riordan');
```

#### Populando a Tabela Editoras
```sql
INSERT INTO Editoras (nome_editora) VALUES
('Intrínseca'),
('Rocco'),
('Martins Fontes'),
('Little, Brown and Company'),
('Companhia Editora Nacional');
```

#### Populando a Tabela Livros
```sql
INSERT INTO Livros (titulo, ano_publicacao, isbn, autor_id, editora_id) VALUES
('A Culpa é das Estrelas', 2012, '978-85-8057-346-6', 1, 1),
('Harry Potter e a Pedra Filosofal', 1997, '9788532511010', 2, 2),
('O Senhor dos Anéis: A Sociedade do Anel', 1954, '9788533603149', 3, 3),
('The Catcher in the Rye', 1951, '9780316769488', 4, 4),
('1984', 1949, '978-85-221-0616-9', 5, 5),
('Percy Jackson e o Ladrão de Raios', 2005, '9788598078355', 6, 1);
```

#### Inserção de Novos Livros
```sql
INSERT INTO Livros (titulo, ano_publicacao, isbn, autor_id, editora_id) VALUES
('Grande Sertão: Veredas', 1956, '978-85-209-2325-1', 7, 6),
('Memórias Póstumas de Brás Cubas', 1881, '9788535910663', 8, 7),
('Vidas Secas', 1938, '9788572326972', 9, 5),
('O Alienista', 1882, '9788572327429', 8, 8),
('O Cortiço', 1890, '9788579027048', 10, 9),
('Dom Casmurro', 1899, '9788583862093', 8, 9),
('Macunaíma', 1928, '9788503012302', 11, 5);
```

---

## 📜 Instruções para Execução

1. Clone este repositório para sua máquina local.
2. Abra seu cliente de banco de dados favorito (como MySQL Workbench ou DBeaver).
3. Execute os scripts SQL fornecidos na ordem apresentada:
   - Criação do banco de dados.
   - Criação das tabelas.
   - Inserção de dados.
4. Faça consultas na tabela `Livros` utilizando os relacionamentos com as tabelas `Autores` e `Editoras`.
