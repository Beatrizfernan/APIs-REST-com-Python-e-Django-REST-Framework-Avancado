# ****API Avançada****

Este é um projeto avançado de API REST desenvolvido em Python utilizando o framework Django REST Framework (DRF). A API possui duas versões: a V1 e a V2. Nesta documentação, focaremos na versão 2 da API.

## **Conteúdo**

1. [Estrutura do Projeto](#estrutura-do-projeto)
2. [Configuração do Ambiente](#configuracao-do-ambiente)
3. [Modelos de Dados](#modelos-de-dados)
4. [Serializadores](#serializadores)
5. [Permissões](#permissoes)
6. [Endpoints da API](#endpoints-da-api)
7. [Instruções de Uso](#instrucoes-de-uso)
8. [Notas Adicionais](#notas-adicionais)

## **1. Estrutura do Projeto**

O projeto está organizado em dois aplicativos principais: **`cursos`** e **`escola`**. Cada aplicativo tem uma estrutura de arquivos padrão, incluindo modelos, serializadores, views, e URLs.

- **`cursos` Aplicativo:**
    - **`admin.py`**: Configuração do painel de administração do Django.
    - **`apps.py`**: Configuração da aplicação.
    - **`models.py`**: Definição dos modelos de dados.
    - **`permissions.py`**: Definição de permissões personalizadas.
    - **`serializers.py`**: Serializadores para converter modelos em formatos JSON.
    - **`urls.py`**: Configuração dos URLs da API.
    - **`views.py`**: Definição das views.
- **`escola` Aplicativo:**
    - **`settings.py`**: Configurações gerais do Django, incluindo autenticação com Token.
    - **`urls.py`**: Configuração dos URLs globais do projeto.
    - **`wsgi.py`**: Configuração para deploy do WSGI.
    - **`manage.py`**: Script para execução de comandos do Django.
    - **`requirements.txt`**: Lista de dependências do projeto.

## **2. Configuração do Ambiente**

O arquivo **`settings.py`** no aplicativo **`escola`** contém as configurações gerais do projeto, incluindo a definição do banco de dados, autenticação, e outras configurações do Django. O ambiente virtual pode ser configurado e as dependências instaladas utilizando o seguinte:

```bash
bashCopy code
pip install -r requirements.txt

```

## **3. Modelos de Dados**

Os modelos de dados são definidos no arquivo **`models.py`** do aplicativo **`cursos`**. O projeto possui dois modelos principais: **`Curso`** e **`Avaliacao`**. A classe **`Base`** é uma classe abstrata contendo campos comuns a ambos os modelos.

- **`Curso`:**
    - **`titulo`**: Título do curso.
    - **`url`**: URL única do curso.
    - **`criacao`**, **`atualizacao`**, **`ativo`**: Campos padrão da classe **`Base`**.
- **`Avaliacao`:**
    - **`curso`**: Chave estrangeira relacionando a avaliação a um curso.
    - **`nome`**, **`email`**: Informações do avaliador.
    - **`comentario`**: Comentário opcional.
    - **`avaliacao`**: Nota atribuída ao curso (de 1 a 5).
    - **`criacao`**, **`atualizacao`**, **`ativo`**: Campos padrão da classe **`Base`**.

## **4. Serializadores**

Os serializadores, definidos em **`serializers.py`** no aplicativo **`cursos`**, convertem os modelos de dados em formatos JSON para facilitar a comunicação com a API. A classe **`CursoSerializer`** inclui uma relação com as avaliações e calcula a média das avaliações.

## **5. Permissões**

O arquivo **`permissions.py`** no aplicativo **`cursos`** contém uma classe **`EhSuperUser`** que permite exclusivamente aos superusuários realizar operações de exclusão (DELETE) na API.

## **6. Endpoints da API**

Os endpoints da API estão definidos no arquivo **`urls.py`** no aplicativo **`cursos`**. A API possui endpoints para listar, criar, visualizar, atualizar e excluir cursos e avaliações. A versão 2 da API também inclui endpoints para listar as avaliações de um curso específico.

## **7. Instruções de Uso**

Para iniciar o servidor de desenvolvimento, utilize o seguinte comando:

```bash
bashCopy code
python manage.py runserver

```

Acesse a API no navegador em **`http://localhost:8000/api/v2/`**. O painel de administração do Django está disponível em **`http://localhost:8000/admin/`** para gerenciar cursos e avaliações.

## **8. Notas Adicionais**

- **Autenticação:**
    - A autenticação na API é realizada através de tokens. Cada usuário autenticado recebe um token único.
- **Paginação e Throttling:**
    - A API inclui paginação para limitar o número de resultados retornados. Além disso, é implementado throttling para controlar a taxa de solicitações.
- **Superusuário:**
    - O superusuário tem permissões especiais, incluindo a capacidade de excluir cursos.

Esta documentação fornece uma visão geral detalhada da estrutura e funcionalidades da API. Sinta-se à vontade para explorar mais a fundo os diferentes componentes e personalizar conforme necessário para atender aos requisitos específicos do seu projeto.
