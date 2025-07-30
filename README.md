# Sistema de Controle Patrimonial
## Observação: Este repositório contém apenas o README. O código-fonte completo e funcional do projeto está hospedado em um repositório privado, acessível exclusivamente para recrutadores e interessados $$.

Este projeto fornece uma aplicação web para registrar e gerenciar empréstimos de materiais e equipamentos em uma organização. Desenvolvido com Django, o sistema permite o controle de retiradas, devoluções, alertas de vencimento e histórico por funcionário.

---

## ✅ Funcionalidades Implementadas até o momento

### 📦 Gestão de Dados
- Cadastro de **itens** com categoria, código e status (`disponível` ou `emprestado`)
- Cadastro de **funcionários**

### 🔁 Empréstimos e Devoluções
- Registro de **empréstimos** com:
  - Data de retirada
  - Data prevista de devolução
- Atualização **automática do status do item** (emprestado/disponível)
- Processo de **devolução** com:
  - Registro da data real de devolução
  - Botão de devolução na interface pública
- **Edição de Empréstimos**: Permite editar empréstimos já registrados, atualizando a data de devolução e outras informações. Após a edição, o usuário é redirecionado para a lista de empréstimos.

### ⚙️ Administração e Backend
- Visualização e gerenciamento de dados via **Django Admin**
- Filtro por status de devolução (pendente ou devolvido)
- Campo de busca por nome do funcionário ou nome do item
- Link para página de detalhes ao clicar no nome do item

### 🌐 Interface Web Responsiva (Bootstrap 5)
- Página **inicial** amigável
- Lista de **empréstimos atuais**, ordenados por data de retirada
- Formulário de **novo empréstimo** com:
  - Validação de item indisponível
  - Exibição de mensagens de erro
- Página de **confirmação de devolução**

### 🚨 Alertas Visuais Inteligentes
- **Alerta de devolução vencida** (em vermelho):
  - Destaque na linha da tabela
  - Mensagem de aviso no topo da página
- **Alerta de devolução no dia atual** (em amarelo):
  - Destaque na linha da tabela
  - Mensagem informativa no topo da página

---

## 🚀 Tecnologias Utilizadas

- Python 3.x
- Django 5.x
- SQLite (ou PostgreSQL)
- Bootstrap 5 (em templates)
- Django Admin

---

## 🛠️ Como rodar o projeto localmente

### 1. Clone o repositório

```bash
git clone https://github.com/Jef-Oliver/controle-emprestimos.git
cd controle-emprestimos
```

### 2. Crie o ambiente virtual

```bash
python -m venv venv
source venv/Scripts/activate  # Windows
```

### 3. Instale as dependências

```bash
pip install django
```

### 4. Aplique as migrações e crie o superusuário

```bash
python manage.py migrate
python manage.py createsuperuser
```

### 5. Inicie o servidor de desenvolvimento

```bash
python manage.py runserver
```

Acesse: [http://127.0.0.1:8000](http://127.0.0.1:8000)  
Admin: [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

---

## 📁 Estrutura Atual do Projeto

```
controle_emprestimos/
├── core/
│   ├── admin.py
│   ├── models.py
│   ├── urls.py
│   ├── views.py
│   └── templates/
│       └── core/
│           ├── base.html
│           ├── home.html
│           ├── emprestimos.html
│           ├── novo_emprestimo.html
│           └── devolucao.html
├── config/
│   ├── settings.py
│   └── urls.py
├── db.sqlite3
├── manage.py
├── README.md
```

---

## 📌 Próximos Passos

- ✅ Finalizar templates com Bootstrap
- ✅ Implementar alertas de devolução
- 🔜 Exportação de relatórios (PDF/Excel)
- 🔜 Histórico por colaborador
- 🔜 Autenticação e controle de acesso (opcional)

---

## 👨‍💻 Autor

Desenvolvido por Jeferson de Oliveira Santos  
Contato: jeferson.greenish@gmail.com  
LinkedIn: [https://www.linkedin.com/in/jeefisantos](https://www.linkedin.com/in/jeefisantos)  
GitHub: [https://github.com/Jef-Oliver](https://github.com/Jef-Oliver)
