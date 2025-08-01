# Sistema de Controle de Empréstimos

Um sistema completo de controle de empréstimos desenvolvido em Django com recursos avançados para gerenciamento de funcionários, itens e empréstimos.

## 🚀 Funcionalidades

### Core Features
- ✅ Gerenciamento completo de funcionários
- ✅ Controle de itens com status (disponível, emprestado, manutenção)
- ✅ Sistema de empréstimos com datas de retirada e devolução
- ✅ Interface web responsiva e intuitiva
- ✅ Filtros e busca avançada
- ✅ Paginação de resultados

### Recursos Avançados
- 🐳 **Docker** - Containerização completa do projeto
- 🧪 **Testes Automatizados** - Cobertura completa com pytest
- 📚 **API REST** - Endpoints completos com DRF
- 📖 **Swagger/OpenAPI** - Documentação automática da API
- 🛡️ **Tratamento de Erros** - Sistema robusto de tratamento de exceções
- 📊 **Relatórios PDF** - Geração automática de relatórios
- 📧 **Emails Automatizados** - Notificações por email
- 📱 **WhatsApp Integration** - Mensagens automáticas via WhatsApp
- 🔒 **Segurança** - Rate limiting, CORS, validações
- 📝 **Logging** - Sistema completo de logs
- ⚡ **Cache** - Redis para performance
- 🔄 **CI/CD Ready** - Preparado para automação

## 🛠️ Tecnologias

- **Backend**: Django 5.2.4, Django REST Framework
- **Database**: PostgreSQL (produção) / SQLite (desenvolvimento)
- **Cache**: Redis
- **Documentação**: Swagger/OpenAPI (drf-yasg)
- **Testes**: pytest, factory-boy, coverage
- **PDF**: ReportLab
- **Email**: django-anymail
- **WhatsApp**: pywhatkit
- **Containerização**: Docker, Docker Compose
- **Frontend**: Bootstrap, HTML5, CSS3, JavaScript

## 📋 Pré-requisitos

- Python 3.11+
- Docker e Docker Compose (opcional)
- PostgreSQL (se não usar Docker)
- Redis (se não usar Docker)

## 🚀 Instalação

### Opção 1: Docker (Recomendado)

1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd controle-emprestimos
```

2. **Configure as variáveis de ambiente**
```bash
cp env.example .env
# Edite o arquivo .env com suas configurações
```

3. **Execute com Docker Compose**
```bash
docker-compose up --build
```

4. **Acesse o sistema**
- Web: http://localhost:8000
- API: http://localhost:8000/api/v1/
- Swagger: http://localhost:8000/swagger/
- Admin: http://localhost:8000/admin/

### Opção 2: Instalação Local

1. **Clone o repositório**
```bash
git clone <url-do-repositorio>
cd controle-emprestimos
```

2. **Crie um ambiente virtual**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate  # Windows
```

3. **Instale as dependências**
```bash
pip install -r requirements.txt
```

4. **Configure as variáveis de ambiente**
```bash
cp env.example .env
# Edite o arquivo .env
```

5. **Execute as migrações**
```bash
python manage.py migrate
```

6. **Crie um superusuário**
```bash
python manage.py createsuperuser
```

7. **Execute o servidor**
```bash
python manage.py runserver
```

## 📚 Uso da API

### Endpoints Disponíveis

#### Funcionários
- `GET /api/v1/funcionarios/` - Lista funcionários
- `POST /api/v1/funcionarios/` - Cria funcionário
- `GET /api/v1/funcionarios/{id}/` - Detalhes do funcionário
- `PUT /api/v1/funcionarios/{id}/` - Atualiza funcionário
- `DELETE /api/v1/funcionarios/{id}/` - Remove funcionário

#### Itens
- `GET /api/v1/itens/` - Lista itens
- `POST /api/v1/itens/` - Cria item
- `GET /api/v1/itens/{id}/` - Detalhes do item
- `PUT /api/v1/itens/{id}/` - Atualiza item
- `DELETE /api/v1/itens/{id}/` - Remove item
- `POST /api/v1/itens/{id}/colocar_em_manutencao/` - Coloca em manutenção
- `POST /api/v1/itens/{id}/retornar_disponivel/` - Retorna para disponível

#### Empréstimos
- `GET /api/v1/emprestimos/` - Lista empréstimos
- `POST /api/v1/emprestimos/` - Cria empréstimo
- `GET /api/v1/emprestimos/{id}/` - Detalhes do empréstimo
- `PUT /api/v1/emprestimos/{id}/` - Atualiza empréstimo
- `DELETE /api/v1/emprestimos/{id}/` - Remove empréstimo
- `POST /api/v1/emprestimos/{id}/devolver/` - Devolve empréstimo
- `GET /api/v1/emprestimos/estatisticas/` - Estatísticas

### Exemplo de Uso

```bash
# Listar funcionários
curl -X GET http://localhost:8000/api/v1/funcionarios/

# Criar funcionário
curl -X POST http://localhost:8000/api/v1/funcionarios/ \
  -H "Content-Type: application/json" \
  -d '{
    "nome": "João Silva",
    "matricula": "123456",
    "setor": "TI",
    "email": "joao@exemplo.com",
    "telefone": "11999999999"
  }'
```

## 🧪 Testes

### Executar Testes
```bash
# Todos os testes
pytest

# Com cobertura
pytest --cov=core

# Testes específicos
pytest core/tests/test_models.py
pytest core/tests/test_views.py
```

### Cobertura de Testes
```bash
coverage run --source='.' manage.py test
coverage report
coverage html  # Gera relatório HTML
```

## 📊 Relatórios PDF

O sistema gera automaticamente relatórios em PDF:

- **Relatório de Empréstimos**: Lista todos os empréstimos com filtros
- **Relatório de Funcionários**: Lista todos os funcionários
- **Relatório de Itens**: Lista todos os itens com status
- **Dashboard**: Relatório geral com estatísticas

### Gerar Relatórios via API
```bash
# Relatório de empréstimos
curl -X GET "http://localhost:8000/api/v1/emprestimos/relatorio/" \
  -H "Accept: application/pdf"

# Relatório de funcionários
curl -X GET "http://localhost:8000/api/v1/funcionarios/relatorio/" \
  -H "Accept: application/pdf"
```

## 📧 Emails Automatizados

O sistema envia automaticamente:

- **Confirmação de Empréstimo**: Quando um empréstimo é criado
- **Confirmação de Devolução**: Quando um item é devolvido
- **Lembretes de Vencimento**: 3 dias e 1 dia antes do vencimento
- **Notificação de Vencimento**: Quando um item está vencido
- **Relatório Diário**: Para administradores

### Configurar Emails
Edite o arquivo `.env`:
```env
EMAIL_BACKEND=anymail.backends.sendgrid.EmailBackend
SENDGRID_API_KEY=sua-chave-sendgrid
```

## 📱 WhatsApp Integration

O sistema envia mensagens automáticas via WhatsApp:

- **Confirmação de Empréstimo**
- **Confirmação de Devolução**
- **Lembretes de Vencimento**
- **Notificações de Vencimento**

### Configurar WhatsApp
Edite o arquivo `.env`:
```env
WHATSAPP_API_KEY=sua-chave-whatsapp
```

## 🔧 Configuração

### Variáveis de Ambiente

Crie um arquivo `.env` baseado no `env.example`:

```env
# Django
DEBUG=True
SECRET_KEY=sua-chave-secreta
ALLOWED_HOSTS=localhost,127.0.0.1

# Database
USE_POSTGRES=True
DB_NAME=controle_emprestimos
DB_USER=postgres
DB_PASSWORD=postgres
DB_HOST=localhost
DB_PORT=5432

# Redis
REDIS_URL=redis://localhost:6379/1

# Email
EMAIL_BACKEND=anymail.backends.sendgrid.EmailBackend
SENDGRID_API_KEY=sua-chave-sendgrid

# WhatsApp
WHATSAPP_API_KEY=sua-chave-whatsapp

# Sentry (opcional)
SENTRY_DSN=sua-dsn-sentry
```

## 🚀 Deploy

### Docker Compose (Produção)
```bash
# Build das imagens
docker-compose -f docker-compose.prod.yml build

# Executar em produção
docker-compose -f docker-compose.prod.yml up -d
```

### Servidor Tradicional
```bash
# Coletar arquivos estáticos
python manage.py collectstatic

# Configurar servidor web (nginx + gunicorn)
# Ver documentação do Django para deploy
```

## 📝 Logs

Os logs são salvos em:
- `logs/django.log` - Logs da aplicação
- Console - Logs em tempo real

### Níveis de Log
- **DEBUG**: Informações detalhadas
- **INFO**: Informações gerais
- **WARNING**: Avisos
- **ERROR**: Erros
- **CRITICAL**: Erros críticos

## 🔒 Segurança

- **Rate Limiting**: Proteção contra ataques de força bruta
- **CORS**: Configuração de origens permitidas
- **Validação**: Validação rigorosa de dados
- **Logs de Segurança**: Registro de atividades suspeitas
- **HTTPS**: Recomendado para produção

## 🤝 Contribuição

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 👥 Autores

- **Seu Nome** - *Desenvolvimento inicial* - [SeuGitHub](https://github.com/seugithub)

## 🙏 Agradecimentos

- Django Community
- Bootstrap
- Todos os contribuidores

## 📞 Suporte

Para suporte, envie um email para suporte@exemplo.com ou abra uma issue no GitHub.

---

**⭐ Se este projeto te ajudou, considere dar uma estrela!**
