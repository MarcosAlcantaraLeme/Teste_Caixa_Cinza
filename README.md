# Testes de Caixa Cinza — Supabase e Postman

> Projeto acadêmico desenvolvido na disciplina de UX/UI e Testes de Software para nota na Avaliação Final, com foco na validação funcional de APIs de autenticação utilizando testes de caixa cinza.

---

# Introdução

Este projeto tem como finalidade aplicar conceitos de testes funcionais e testes de caixa cinza em uma API de autenticação, utilizando o Supabase como serviço de gerenciamento de usuários e o Postman para execução das requisições HTTP.

A atividade consiste em configurar um ambiente de autenticação por e-mail e senha, realizar diferentes tentativas de login e verificar se o sistema apresenta os comportamentos esperados diante de cada cenário.

Os testes permitem analisar o funcionamento da autenticação por meio dos endpoints, headers, corpos das requisições e respostas HTTP.

# Objetivo da Atividade

Compreender e aplicar testes de caixa cinza em APIs de autenticação, utilizando ferramentas de desenvolvimento e validação de software.

Durante a atividade foram definidos os seguintes objetivos:

- Configurar um ambiente de autenticação no Supabase.
- Criar usuários para realização dos testes.
- Compreender o funcionamento de requisições HTTP.
- Configurar e utilizar o Postman.
- Realizar Testes para verificar a funcionalidade do sistema.
- Validar respostas de autenticação.
- Identificar possíveis falhas no processo de login.
- Documentar os resultados obtidos durante os testes.

# Configuração do Supabase

O Supabase foi utilizado como plataforma de autenticação e gerenciamento do usuário.

Inicialmente, foi criado um projeto na plataforma, permitindo a utilização dos recursos de autenticação por e-mail e senha.

Após a criação do projeto, foi necessário acessar a seção Authentication e verificar se o provedor Email estava habilitado.

Além de ser realizado o cadastro de um usuário para servir como referência nos testes de autenticação.

As credenciais da API foram obtidas na configuração do projeto, sendo utilizadas posteriormente para estabelecer a comunicação com o Postman.

**Configurações utilizadas:**

- Plataforma: Supabase.
- Serviço: Authentication.
- Método de autenticação: E-mail e senha.
- API: Supabase Auth.
- Usuário: E-mail cadastrado para os testes.

**Evidências da configuração:**

**Print 01 — Projeto criado no Supabase**
```
<img width="1534" height="733" alt="Imagem Projeto Supa Base" src="https://github.com/user-attachments/assets/8728ddf0-2ea2-4789-a4ca-fc7d7539e3fd" />

```

**Print 02 — Autenticação por e-mail habilitada**
```
<img width="1534" height="730" alt="Config  do Email aplicada" src="https://github.com/user-attachments/assets/3d127d8b-4650-4bd7-a521-15b36480c261" />

```

**Print 03 — Usuário cadastrado no Supabase**
```
<img width="1530" height="726" alt="Print Usuario Criado" src="https://github.com/user-attachments/assets/4bed3eaa-56f8-4104-9d58-b4196adc97df" />

```

**Print 04 — Credenciais da API**
```
<img width="1532" height="726" alt="Credenciais" src="https://github.com/user-attachments/assets/05cc217b-6715-434f-b533-30175fa09e83" />

```

# Configuração do Postman

O Postman Desktop foi utilizado para realizar as requisições HTTP e verificar as respostas fornecidas pela API de autenticação do Supabase.

Inicialmente, foi criado um Workspace para organizar os recursos utilizados durante a atividade.

Em seguida, foi configurado um Environment contendo variáveis que permitem reutilizar as informações necessárias nas requisições, evitando a repetição de dados.
Variáveis configuradas:
Variável	Descrição
base_url	URL da API do Supabase
api_key	Chave de acesso da API

Essas variáveis são utilizadas para facilitar a configuração e execução dos diferentes cenários de teste.

# Evidências da configuração:

Print 05 — Workspace criado

<img width="1530" height="780" alt="postman Criado" src="https://github.com/user-attachments/assets/ee4d2d42-dc37-4c06-93e8-9fa4f0bfd29d" />



Print 06 — Environment criado

<img width="1090" height="546" alt="Environment Criado" src="https://github.com/user-attachments/assets/c1c795ef-ede4-430d-856b-948f6384e405" />


Print 07 — Variáveis configuradas

<img width="1530" height="780" alt="postman Criado" src="https://github.com/user-attachments/assets/44a95395-9843-408d-8018-120447a6fa67" />


# Configuração das Requisições

Para realizar os testes de autenticação, foi criada uma requisição HTTP utilizando o método POST.

O endpoint utilizado foi:

[{{base_url}}/auth/v1/token?grant_type=password](https://swvjnucxvavkstvyccjm.supabase.co/auth/v1/token?grant_type=password)

Esse endpoint permitiu realizar a autenticação de um usuário utilizando e-mail e senha.

Método HTTP: POST

Body JSON:

A requisição utiliza o formato raw com a opção JSON selecionada.

{
  "email": "{{email}}",
  "password": "{{password}}"
}

A finalidade da requisição é verificar se as credenciais fornecidas correspondem a um usuário cadastrado no ambiente de autenticação do Supabase.

Evidências da configuração:


Print 08 — Headers configurados

<img width="1086" height="546" alt="Headers config" src="https://github.com/user-attachments/assets/e8733525-b315-4c94-979b-89a3f132a5a1" />



Print 09 — Body JSON configurado

<img width="1534" height="774" alt="Config body postman" src="https://github.com/user-attachments/assets/1b259a82-12dd-46dd-b481-5e8c85cf6dd2" />


# Execução dos Testes

Os testes foram realizados utilizando a API de autenticação do Supabase por meio do Postman.

Foram definidos cinco cenários para verificar o comportamento do sistema diante de diferentes condições de entrada.

A abordagem de caixa cinza permite analisar o funcionamento da autenticação considerando informações como endpoint, método HTTP, headers, corpo da requisição e respostas retornadas pela API.

# Cenários de teste:
ID	Cenário	Entrada utilizada	Resultado esperado
01	Login válido	E-mail e senha corretos	Status 200 e retorno de access token
02	Senha incorreta	E-mail correto e senha incorreta	Erro de autenticação
03	Usuário inexistente	E-mail não cadastrado	Acesso negado
04	Campos vazios	E-mail e senha vazios	Erro de validação
05	Credenciais inválidas	E-mail e senha incorretos	Mensagem de erro

# Resultados obtidos:
| ID | Requisito | Comentário do Cliente | Status | Riscos / Ações |
| :---: | :--- | :--- | :---: | :--- |
| **1** | Login Válido | Resultado 200, e-mail e senha validados com sucesso | OK | Vazamento de e-mail e senha |
| **2** | Senha Incorreta | Credenciais inválidas e erro 400 | OK | Indicar se o e-mail está correto |
| **3** | Usuário Inexistente | Credenciais inválidas e erro 400 | OK | Indicar se o e-mail existe |
| **4** | Campos Vazios | Erro 400, validação falha e mensagem indicando falta de e-mail | OK | Indicar se o e-mail existe |
| **5** | Credenciais Inválidas | Credenciais inválidas e erro 400 | OK | Permitir usuário entrar sem criar a conta |

Durante a execução, foram observados os seguintes elementos:

    Código de status HTTP.

    Conteúdo das respostas JSON.

    Mensagens de erro retornadas.

    Presença do access token no login válido.

    Comportamento da API diante de credenciais inválidas.

# Evidências da execução:

Print 10 — Login válido

<img width="1533" height="712" alt="01-login valido postman" src="https://github.com/user-attachments/assets/9fa010c0-6ccc-42d7-a830-417d89ddd8b2" />



Print 11 — Senha incorreta

<img width="1533" height="718" alt="02 - Senha Incorreta Postman" src="https://github.com/user-attachments/assets/8fff0202-ebbc-4396-b8de-c3ac53b4c874" />



Print 13 — Usuário inexistente

<img width="1534" height="778" alt="03 - Usuario Inexistente" src="https://github.com/user-attachments/assets/b88a89ec-9273-4f80-aefd-b2f6b84a7d2a" />



Print 14 — Campos vazios

<img width="1534" height="777" alt="04 - Campos Vazios" src="https://github.com/user-attachments/assets/902da9ee-8073-46f2-8566-1bfec5c4baef" />



Print 15 — Credenciais inválidas

<img width="1532" height="770" alt="05 - Credenciais Inválidas" src="https://github.com/user-attachments/assets/bc502cf1-afd8-4f0b-b95f-abf6c6f81df4" />



# Registro dos Testes

Os testes foram documentados em uma planilha disponibilizada pelo professor da disciplina, contendo informações sobre os cenários executados, entradas utilizadas, resultados esperados e resultados obtidos.

A planilha foi organizada para permitir a identificação de cada teste e facilitar a análise dos resultados.

Evidência do registro:

Print 16 — Planilha de testes preenchida

<img width="1480" height="170" alt="Planilha 1" src="https://github.com/user-attachments/assets/d9cf178b-013e-4b02-a914-bc492d54913a" />


# Conclusão

A atividade possibilitou compreender na prática o funcionamento de uma API de autenticação e a importância da realização de testes funcionais utilizando a abordagem de caixa cinza.

Por meio da integração entre Supabase e Postman, foi possível estruturar requisições HTTP, configurar headers, utilizar variáveis de ambiente e analisar as respostas retornadas pelo serviço de autenticação.

Os diferentes cenários permitem verificar tanto o comportamento esperado diante de credenciais válidas quanto a capacidade do sistema de impedir acessos não autorizados.

A documentação dos testes também demonstra a importância de manter registros organizados, facilitando a identificação de falhas e a validação do funcionamento do sistema.

Conclui-se que os testes de caixa cinza são importantes para verificar a confiabilidade de APIs, pois permitem analisar as entradas, os processos conhecidos e as respostas do sistema, contribuindo para a identificação de problemas antes da utilização em um ambiente de produção.
Estrutura do Repositório
