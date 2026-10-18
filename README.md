# 🥗 TabNutri - Tabela Nutricional Para Fácil Visualização

> Aplicativo que mostra quantos gramas de cada nutriente você consome e permite guardar receitas, mantê-las privadas ou compartilhá-las com outras pessoas.

---

## 📌 1. Sobre o Projeto

O **TabNutri** ajuda quem quer saber o que está comendo sem decifrar tabelas enormes. Você diz o que comeu e quantos **gramas**, e o app devolve calorias, carboidratos, proteínas, gorduras e fibras num **rótulo nutricional** parecido com o das embalagens.

Também dá para **cadastrar receitas**: o app soma os nutrientes dos ingredientes e mostra o valor **por porção**. Cada receita pode ser **privada** (só o dono vê) ou **pública**. Na aba **Explorar**, o usuário encontra receitas de outras pessoas e pode **importá-las**: ele recebe uma cópia privada, que pode editar sem mexer na original.

> O arquivo `prototipo/tabnutri.html` é um protótipo para testar o layout e o fluxo de uso. Nele, o login e as receitas de outras pessoas são **simulados** e nada vai para a internet. O app final será conectado em rede.

**Problemas que o projeto resolve:**
- Tabelas nutricionais são grandes e difíceis de consultar.
- Quem cozinha em casa não sabe quanto de cada nutriente tem na própria receita.
- Boas receitas ficam espalhadas e sem informação nutricional confiável.

**Principais funcionalidades:**
- Cadastro e login de usuários
- Registro do consumo do dia em gramas, com rótulo nutricional
- Cadastro de alimentos
- Receitas com ingredientes, porções e modo de preparo
- Privacidade por receita: privada ou pública
- Explorar receitas públicas e importar para o próprio celular
- Uso offline das receitas salvas, com sincronização quando a internet voltar

---

## 🛠️ 2. Tecnologias, Ferramentas e Infraestrutura

| Camada | Tecnologia |
|---|---|
| Front-end web | ![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) ![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB) |
| Aplicativo Android | ![React Native](https://img.shields.io/badge/React%20Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB) ![Expo](https://img.shields.io/badge/Expo-000020?style=for-the-badge&logo=expo&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) |
| Dados no celular | ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)![offline](https://img.shields.io/badge/(offline)-gray?style=for-the-badge) ![IndexedDB](https://img.shields.io/badge/IndexedDB-1976D2?style=for-the-badge&logo=mdnwebdocs&logoColor=white)![web](https://img.shields.io/badge/(web)-gray?style=for-the-badge) |
| Back-end | ![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white) |
| Banco de dados | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white) ![Tabela TACO](https://img.shields.io/badge/Tabela_TACO-base_de_alimentos-2E7D32?style=for-the-badge&logo=googlesheets&logoColor=white&labelColor=1B5E20) |
| Autenticação | ![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white) ![bcrypt](https://img.shields.io/badge/bcrypt-hash_de_senhas-338033?style=for-the-badge&logo=gnuprivacyguard&logoColor=white&labelColor=1B1B1B) |
| Cloud | ![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white) (EC2 para a API, RDS para o banco, S3 para fotos) |
| Contêineres | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) |
| Gerar o APK | ![Expo EAS Build](https://img.shields.io/badge/Expo_EAS_Build-000020?style=for-the-badge&logo=expo&logoColor=white) |
| Testes e integração contínua | ![Jest](https://img.shields.io/badge/Jest-C21325?style=for-the-badge&logo=jest&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white) |
| Design das telas | ![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white) |
| Versionamento | ![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white) |

**Privacidade:** cada receita tem o campo `visibilidade` (`privada` ou `pública`) e a API só entrega receitas privadas ao próprio dono. Os dados seguem a LGPD e o usuário pode apagar a conta e as receitas.

---

## 📐 3. Metodologias Utilizadas

### Modelo de processo: Espiral

Escolhido o modoelo **Espiral** em vez do Cascata porque:

- os requisitos mudaram ao longo do projeto (começou como um layout simples e ganhou rede, compartilhamento e importação), e o Cascata pede tudo definido no início;
- existem riscos claros para vigiar a cada volta: privacidade (LGPD), receitas públicas com dados errados, qualidade da base nutricional e sincronização offline;
- cada volta entrega algo testável, como o protótipo HTML do primeiro ciclo.

| Ciclo | Objetivo | Entrega |
|---|---|---|
| 1 | Validar o layout | Protótipo HTML com consumo, receitas, explorar e importação simulados (concluído) |
| 2 | Contas e alimentos | Login, cadastro e base de alimentos (TACO) |
| 3 | Consumo e receitas | Registro de consumo, rótulo do dia, receitas e privacidade |
| 4 | Compartilhamento | Aba Explorar com busca e botão Importar |
| 5 | Offline e entrega | Sincronização, testes finais e APK |

Em cada ciclo: **planejamento → análise de riscos → desenvolvimento e testes → avaliação**.

### Uso do Git e GitHub

**Branches**

```mermaid
gitGraph
    commit id: "docs: cria README"
    branch develop
    checkout develop
    branch "feature/consumo"
    checkout "feature/consumo"
    commit id: "feat: registra consumo"
    checkout develop
    merge "feature/consumo"
    branch "feature/receitas"
    checkout "feature/receitas"
    commit id: "feat: cria receita"
    commit id: "feat: privacidade"
    checkout develop
    merge "feature/receitas"
    checkout main
    merge develop tag: "v0.1.0"
```

- `main`: versão estável, só recebe código revisado.
- `develop`: junta o que foi feito no ciclo.
- `feature/...` e `fix/...`: uma branch por tarefa ou correção, sempre criada a partir da `develop`.
- Tarefas viram **issues** em um quadro Kanban, e cada branch entra por **Pull Request** revisado por um colega. O **GitHub Actions** roda os testes antes do merge.
- No fim de cada ciclo, a `develop` vai para a `main` com uma **tag** de versão (`v0.1.0`, `v0.2.0`...).

**Commits**

Mensagens curtas, com um prefixo que diz o tipo da mudança:

```
feat(receitas): adiciona escolha de privacidade
fix(consumo): corrige soma ao remover um item
docs: atualiza diagrama de importação
test(importar): cobre receita já importada
chore: configura GitHub Actions
```

Usamos `feat` (novidade), `fix` (correção), `docs` (documentação), `test` (testes) e `chore` (configuração). Cada commit trata de uma coisa só, e senhas, arquivos `.env` e o APK ficam no `.gitignore`.

---

## 🎨 4. Projeto de Interface

As telas são capturas do protótipo em HTML. Todas têm **1080 × 2400 px** (proporção de um celular Android, 360 × 800 dp) e aparecem com a mesma largura.

<table>
<tr><td align="center"><img src="imagens/01-login.png" width="170" alt="Login"><br><sub><b>1. Login</b></sub></td><td align="center"><img src="imagens/02-consumo.png" width="170" alt="Consumo"><br><sub><b>2. Consumo</b></sub></td><td align="center"><img src="imagens/03-nova-receita.png" width="170" alt="Nova receita"><br><sub><b>3. Nova receita</b></sub></td><td align="center"><img src="imagens/04-minhas-receitas.png" width="170" alt="Minhas receitas"><br><sub><b>4. Minhas receitas</b></sub></td><td align="center"><img src="imagens/05-explorar.png" width="170" alt="Explorar"><br><sub><b>5. Explorar</b></sub></td></tr>
<tr><td align="center"><img src="imagens/06-explorar-detalhe.png" width="170" alt="Receita de outro usuário"><br><sub><b>6. Receita de outro usuário</b></sub></td><td align="center"><img src="imagens/07-importada.png" width="170" alt="Receita importada"><br><sub><b>7. Receita importada</b></sub></td><td align="center"><img src="imagens/08-receita-aberta.png" width="170" alt="Receita aberta"><br><sub><b>8. Receita aberta</b></sub></td><td align="center"><img src="imagens/09-offline.png" width="170" alt="Modo offline"><br><sub><b>9. Modo offline</b></sub></td><td align="center"><img src="imagens/10-alimentos.png" width="170" alt="Alimentos"><br><sub><b>10. Alimentos</b></sub></td></tr>
</table>

1. **Login:** entrada com e-mail e senha (no protótipo, qualquer dado funciona).
2. **Consumo:** escolha do dia, do alimento e da quantidade em gramas, com o rótulo nutricional do dia.
3. **Nova receita:** ingredientes, porções, modo de preparo e a opção **Privada** ou **Pública**.
4. **Minhas receitas:** lista com etiquetas Privada, Pública e Importada.
5. **Explorar:** receitas de outras pessoas, com busca por nome ou autor.
6. **Receita de outro usuário:** ingredientes, preparo e rótulo por porção antes de importar.
7. **Receita importada:** o botão vira "Já importada" e a cópia fica privada.
8. **Receita aberta:** permite adicionar 1 porção ao consumo, mudar a privacidade ou excluir.
9. **Modo offline:** Explorar pede internet, mas as receitas salvas continuam disponíveis.
10. **Alimentos:** cadastro de novos alimentos e tabela dos que já existem.

**Visual:** rótulo nutricional com bordas grossas, verde como cor principal, quatro abas no topo e um botão Online/Offline sempre visível. Os protótipos de alta fidelidade serão feitos no Figma.

---

## 📊 5. Diagramas

### Casos de uso

```mermaid
flowchart LR
    U(["👤 Usuário"])
    O(["👥 Outro usuário"])
    subgraph TN["TabNutri"]
        UC1("Entrar na conta")
        UC2("Cadastrar alimento")
        UC3("Registrar consumo")
        UC4("Criar receita")
        UC5("Escolher privacidade")
        UC6("Explorar receitas")
        UC7("Importar receita")
        UC8("Usar offline e sincronizar")
    end
    U --- UC1
    U --- UC2
    U --- UC3
    U --- UC4
    U --- UC5
    U --- UC6
    U --- UC7
    U --- UC8
    O -. "compartilha" .- UC5
    UC7 -. "inclui" .-> UC6
```

### Sequência: importar uma receita

```mermaid
sequenceDiagram
    actor U as Usuário
    participant App as App Android
    participant API as API Node.js
    participant BD as PostgreSQL

    U->>App: toca em Importar
    App->>API: POST /receitas/{id}/importar (JWT)
    API->>BD: confere se a receita é pública
    alt pública
        API->>BD: grava a cópia como privada
        API->>BD: adiciona alimentos que faltam
        API-->>App: 201 receita copiada
        App->>App: salva no SQLite do celular
        App-->>U: "Receita importada"
    else privada ou excluída
        API-->>App: 404
        App-->>U: avisa que não está mais disponível
    end
```

### Arquitetura

```mermaid
flowchart LR
    subgraph DISP["Celular Android"]
        APP["App React Native"]
        LOC[("SQLite local")]
        APP <--> LOC
    end
    subgraph NUVEM["Nuvem AWS"]
        API["API Node.js"]
        BD[("PostgreSQL")]
        S3[("S3: fotos")]
        API --> BD
        API --> S3
    end
    APP -- "HTTPS + JWT" --> API
```

### Modelo de dados

```mermaid
erDiagram
    USUARIO ||--o{ RECEITA : cria
    USUARIO ||--o{ CONSUMO : registra
    RECEITA ||--|{ INGREDIENTE : possui
    ALIMENTO ||--o{ INGREDIENTE : "entra em"
    ALIMENTO ||--o{ CONSUMO : "é consumido em"
    RECEITA |o--o{ RECEITA : "é importada de"

    USUARIO {
        int id PK
        string nome
        string email
    }
    ALIMENTO {
        int id PK
        string nome
        decimal kcal "por 100 g"
        decimal carboidratos_g
        decimal proteinas_g
        decimal gorduras_g
        decimal fibras_g
    }
    RECEITA {
        int id PK
        int usuario_id FK
        int origem_id FK
        string nome
        int porcoes
        string visibilidade "privada ou publica"
    }
    INGREDIENTE {
        int receita_id FK
        int alimento_id FK
        decimal gramas
    }
    CONSUMO {
        int id PK
        int usuario_id FK
        date dia
        decimal quantidade
    }
```

---

## ▶️ Como abrir o protótipo

1. Baixe o repositório (**Code → Download ZIP**) e extraia os arquivos.
2. Abra `prototipo/tabnutri.html` no navegador. No computador, estreite a janela para ver o layout de celular.
3. Entre com qualquer e-mail e senha.

## 👥 Equipe

| Nome |
|---|
| Marlon Oliveira Costa |

## 📄 Licença

Projeto acadêmico desenvolvido para a disciplina de Engenharia de Software 1 (Fatec).
