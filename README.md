# Documento de requisitos

## Propósito

O propósito dessa aplicação web é ajudar o usuário a calcular a quantidade de tinta para pintar uma sala. A aplicação permite que o usuário escolha de forma dinâmica as dimensões das paredes e adicione portas e janelas para calcular de forma dinâmica a quantidade de tinta necessária (em latas de tinta).

## Escopo

O projeto é composto é separado por duas aplicações (Backend e Frontend).

## Iniciar a aplicação

### Requisitos (aplicação inteira)

- docker
- docker-compose

### Requisitos (aplicação individualmente)

- node 14+
- mongodb

### Iniciar aplicação inteira

```bash
git submodule update --init --recursive
docker-compose up --build
```

## Iniciar backend e/ou frontend

Para cada frente o read mostra como iniciar:

- https://github.com/MuriloGon/dr-backend
- https://github.com/MuriloGon/dr-frontend

## Requisitos Funcionais

- Frontend
  - [x] Página Principal
    - [x] Calculadora de tinta
    - [x] Visualização dinâmica da sala a ser pintada
    - [ ] Opção de compartilhamento para as redes sociais
  - [x] Página de listagem de calculos feitos pelos usuários
  - [ ] Página admin para gerenciar com um CRUD a aplicação
- Backend
  - [x] API de apoio ao frontend
    - [x] Rotas de acesso de dados
    - [x] Rotas de autenticação

## Requisitos não-funcionais

- [x] UI/UX
- [ ] Programação Orientada a Objetos
- [x] Typescript
- [ ] Postgres (Typeorm)
- [ ] SEO

## Modelagem do banco de dados

```tsx
// Latas de tintas
enum CanSize {
  "0.5L" = 0.5,
  "2.5L" = 2.5,
  "3.6L" = 3.6,
  "18L" = 18,
}

interface Wall {
  width: number;
  height: number;
  doors: number;
  windows: number;
}

interface InkComputation {
  _id: ObjectId;
  createdAt: Date;
  canSize: CanSize;
  "wall-a": Wall;
  "wall-b": Wall;
  "wall-c": Wall;
  "wall-d": Wall;
}
```

```tsx
// usuários de acesso à página de admin
{
  email: string;
  password: string;
  role: root | normal;
}
```

## Ferramentas

### Geral

- Notion
- Git-Github
- Vscode

### Frontend

- Styled Component
- ~~Three.JS~~
- Eslint
- Typescript
- React Testing Library

### Backend

- Express
- Typescript
- MongoDB
- Typeorm
- Mocha
- Chai
- Sinon

## Endpoints

`POST` /login

`GET` /inks

`POST` /inks/

`GET` /inks/{id}

`PUT` /inks/{id}

`DELETE` /inks/{id}
