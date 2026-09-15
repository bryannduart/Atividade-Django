# Atividade 6 Extra — Django

## Sistema Web de Gestão de Tarefas

Atividade prática da disciplina de **Back-End**, desenvolvida utilizando **Python** e o framework **Django**.

O objetivo é criar uma primeira interface web para um Sistema de Gestão de Tarefas, disponibilizando uma página inicial e uma página de listagem de tarefas acessíveis pelo navegador.

Nesta etapa, as tarefas são mantidas temporariamente em memória, sem utilização de banco de dados para os dados da aplicação.

---

## Objetivo da atividade

Desenvolver uma aplicação Django chamada `tarefas` com duas páginas funcionais:

* `/` — página inicial do sistema;
* `/tarefas/` — listagem inicial de tarefas.

A listagem apresenta as seguintes informações para cada tarefa:

* título;
* prioridade;
* situação.

---

## Tecnologias utilizadas

* **Python**
* **Django**
* **HTML**
* **Git**
* **GitHub**

---

## Estrutura do projeto

```text
gestao_tarefas/
│
├── manage.py
├── README.md
│
├── gestao_tarefas/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
└── tarefas/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── tests.py
    ├── views.py
    ├── urls.py
    │
    └── templates/
        └── tarefas/
            ├── inicio.html
            └── lista.html
```

O ambiente virtual `.venv/` é utilizado localmente e não é versionado no GitHub.

---

## Configuração do projeto

O projeto Django foi criado com o nome:

```text
gestao_tarefas
```

A aplicação criada para o sistema foi:

```text
tarefas
```

A aplicação `tarefas` foi registrada no arquivo `gestao_tarefas/settings.py`.

---

## Rotas

As URLs da aplicação são configuradas em `tarefas/urls.py` e incluídas nas URLs principais do projeto.

### Página inicial

```text
/
```

A página inicial apresenta o título do sistema, uma breve mensagem e um link para acessar a lista de tarefas.

### Lista de tarefas

```text
/tarefas/
```

A página apresenta as tarefas temporárias cadastradas na view, mostrando:

* título;
* prioridade;
* situação.

---

## Views

As funcionalidades das páginas são implementadas no arquivo:

```text
tarefas/views.py
```

A view `inicio` renderiza a página inicial:

```python
def inicio(request):
    return render(request, "tarefas/inicio.html")
```

A view `lista_tarefas` cria os dados temporários em memória e envia essas informações para o template:

```python
def lista_tarefas(request):
    tarefas = [
        {
            "titulo": "Revisar URLs no Django",
            "prioridade": "Alta",
            "situacao": "Pendente",
        },
        {
            "titulo": "Criar template de listagem",
            "prioridade": "Média",
            "situacao": "Concluída",
        },
    ]

    contexto = {"tarefas": tarefas}
    return render(request, "tarefas/lista.html", contexto)
```

Nesta etapa, não existe cadastro ou persistência das tarefas. Os dados são definidos diretamente na view e permanecem apenas durante a execução da aplicação.

---

## Templates

Os templates estão organizados em:

```text
tarefas/templates/tarefas/
```

### `inicio.html`

Responsável pela página inicial do sistema.

A página possui:

* título;
* texto de apresentação;
* link para a lista de tarefas.

### `lista.html`

Responsável pela exibição das tarefas.

O template utiliza:

```django
{% if tarefas %}
```

para verificar se existem tarefas.

Também utiliza:

```django
{% for tarefa in tarefas %}
```

para percorrer e apresentar cada tarefa.

Caso a lista esteja vazia, é exibida a mensagem:

```text
Nenhuma tarefa cadastrada até o momento.
```

---

## Como executar o projeto

### 1. Clonar o repositório

```bash
git clone https://github.com/bryannduart/Atividade-Django.git
```

Entre na pasta da atividade:

```bash
cd "Atividade-Django/Atividade 6 Extra (Django)/gestao_tarefas"
```

---

### 2. Criar o ambiente virtual

Caso ainda não exista:

```bash
py -m venv .venv
```

---

### 3. Ativar o ambiente virtual

No Windows:

```bash
.venv\Scripts\activate
```

Após a ativação, o terminal deverá apresentar algo semelhante a:

```text
(.venv)
```

---

### 4. Instalar o Django

Com o ambiente virtual ativado:

```bash
python -m pip install django
```

Para verificar a instalação:

```bash
python -m django --version
```

---

### 5. Verificar o projeto

Execute:

```bash
python manage.py check
```

O projeto deve passar pela verificação sem apresentar erros.

---

### 6. Iniciar o servidor

Execute:

```bash
python manage.py runserver
```

O servidor será iniciado em:

```text
http://127.0.0.1:8000/
```

---

## Testando no navegador

### Página inicial

Acesse:

```text
http://127.0.0.1:8000/
```

A página inicial deve apresentar o sistema e o link para acessar a lista de tarefas.

### Lista de tarefas

Acesse:

```text
http://127.0.0.1:8000/tarefas/
```

A página deve apresentar as tarefas temporárias, contendo título, prioridade e situação.

---

## Tarefas utilizadas

A aplicação possui inicialmente duas tarefas temporárias:

| Título                     | Prioridade | Situação  |
| -------------------------- | ---------- | --------- |
| Revisar URLs no Django     | Alta       | Pendente  |
| Criar template de listagem | Média      | Concluída |

Esses dados são definidos diretamente na view e não são armazenados de forma persistente.

---

## Banco de dados

O escopo desta atividade não utiliza banco de dados para armazenar as tarefas.

As tarefas são definidas temporariamente dentro da view `lista_tarefas`.

Portanto, a aplicação trabalha com dados em memória nesta etapa.

---

## Versionamento

O projeto é versionado utilizando **Git** e disponibilizado no **GitHub**.

Repositório:

```text
https://github.com/bryannduart/Atividade-Django
```

O projeto possui commits para registrar as alterações realizadas durante o desenvolvimento da atividade.

Exemplo de commit descritivo utilizado para a entrega:

```bash
git add .
git commit -m "Adiciona Atividade 6 Extra Django"
git push
```

---

## `.gitignore`

O projeto possui um arquivo `.gitignore` para evitar o versionamento de arquivos e pastas desnecessários, incluindo o ambiente virtual Python:

```gitignore
.venv/
__pycache__/
*.pyc
db.sqlite3
```

O ambiente virtual deve permanecer apenas no computador local e não deve ser enviado ao GitHub.

---

## Checklist da atividade

* [x] Ambiente virtual Python configurado.
* [x] Projeto Django criado ou confirmado.
* [x] Aplicação `tarefas` criada.
* [x] Aplicação `tarefas` registrada em `INSTALLED_APPS`.
* [x] Arquivo `tarefas/urls.py` criado.
* [x] URLs da aplicação incluídas no projeto.
* [x] View `inicio` implementada.
* [x] View `lista_tarefas` implementada.
* [x] Template `inicio.html` criado.
* [x] Template `lista.html` criado.
* [x] Tarefas temporárias adicionadas.
* [x] Título, prioridade e situação exibidos.
* [x] Rota `/` testada no navegador.
* [x] Rota `/tarefas/` testada no navegador.
* [x] README atualizado.
* [x] Projeto versionado com Git.
* [x] Commit descritivo realizado.

---

## Resultado

A atividade apresenta uma primeira interface web funcional para o **Sistema Web de Gestão de Tarefas**, com separação entre URLs, views e templates, utilizando o framework Django.

O sistema permite acessar a página inicial em `/` e a listagem de tarefas em `/tarefas/`, apresentando tarefas temporárias com título, prioridade e situação.

---

## Autor

**Bryan Duarte**

Atividade acadêmica da disciplina de **Back-End**.
