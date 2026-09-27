# WWallet

**Controle financeiro pessoal, em qualquer tela.** O WWallet reúne uma aplicação web e um aplicativo mobile para registrar receitas e despesas, acompanhar o saldo e entender os hábitos financeiros com históricos e gráficos.

[![Web: React + Vite](https://img.shields.io/badge/Web-React%20%2B%20Vite-646CFF?logo=vite&logoColor=white)](./Front)
[![Mobile: Expo](https://img.shields.io/badge/Mobile-Expo%20%2B%20React%20Native-000020?logo=expo&logoColor=white)](https://github.com/Lg-crypto/TCC-mobile)
[![Backend: Firebase](https://img.shields.io/badge/Backend-Firebase-FFCA28?logo=firebase&logoColor=black)](https://firebase.google.com/)

## Sobre o projeto

O WWallet nasceu como um projeto de conclusão de curso com uma proposta prática: tornar o controle das finanças pessoais simples e visual. Web e mobile compartilham o Firebase e o mesmo formato de lançamentos, para que os dados da conta sejam acessíveis nos dois clientes.

## Funcionalidades

- Cadastro e login com e-mail e senha.
- Login com Google na versão web.
- Registro de receitas e despesas com valor, categoria, data e comentário.
- Saldo e resumo financeiro com receitas, despesas e investimentos.
- Histórico pesquisável e filtrável por tipo e período.
- Dashboard web com gráficos de saldo, despesas por categoria e evolução mensal.
- Perfil da conta e configurações.
- Interface mobile para Android, iOS e web, com navegação adaptada a telas menores.

## Aplicações

| Cliente | Repositório | Tecnologias |
| --- | --- | --- |
| Web | Este repositório, pasta [`Front`](./Front) | React, TypeScript, Vite, React Router, Firebase, ApexCharts |
| Mobile | [TCC-mobile](https://github.com/Lg-crypto/TCC-mobile) | Expo SDK 57, React Native, TypeScript, Expo Router, Firebase |

O Firebase fornece autenticação, banco de dados Firestore e armazenamento de arquivos. Não há uma API REST separada neste momento.

## Como executar

### Web

Pré-requisitos: Node.js e npm.

```bash
cd Front
npm install
npm run dev
```

Para gerar e visualizar a versão de produção:

```bash
npm run build
npm run preview
```

### Mobile

Pré-requisitos: Node.js, npm e Expo Go ou um development build.

```bash
git clone https://github.com/Lg-crypto/TCC-mobile.git
cd TCC-mobile
npm install
npx expo start
```

Abra o QR code com o Expo Go ou inicie um emulador compatível. Algumas integrações de autenticação nativa podem exigir um development build e configuração OAuth da plataforma.

## Configuração do Firebase

Crie um projeto no Firebase, registre uma aplicação web e habilite **Authentication** e **Cloud Firestore**. Para usar fotos de perfil no mobile, habilite também o **Cloud Storage**.

Configure as variáveis de ambiente nos dois clientes:

- Web: copie [`Front/.env.example`](./Front/.env.example) para `Front/.env.local` e preencha as variáveis `VITE_FIREBASE_*`.
- Mobile: copie [`.env.example`](https://github.com/Lg-crypto/TCC-mobile/blob/main/.env.example) para `TCC-mobile/.env` e preencha as variáveis `EXPO_PUBLIC_FIREBASE_*`.
- Google: habilite o provedor no Firebase e configure os IDs OAuth de cada plataforma. Os nomes das variáveis estão no exemplo de ambiente do mobile.

Os lançamentos são salvos por usuário no caminho `users/{uid}/records` do Firestore, permitindo que os clientes web e mobile consultem os mesmos registros. Consulte as regras em [`Front/firestore.rules`](./Front/firestore.rules) e, para fotos de perfil, em [`storage.rules`](https://github.com/Lg-crypto/TCC-mobile/blob/main/storage.rules).

> Nunca publique arquivos `.env`, chaves privadas ou client secrets. As chaves de configuração do Firebase usadas pelo cliente identificam o projeto; o controle de acesso aos dados deve ser feito pelas regras do Firebase.

## Estrutura

```text
TCC/
├── Front/       # Aplicação web e regras do Firestore
├── Back/        # Diretório reservado para serviços de backend
└── README.md

TCC-mobile/      # Aplicativo Expo em repositório separado
```

## Feito por

Projeto acadêmico desenvolvido por estudantes do curso técnico em Desenvolvimento de Sistemas da ETEC de Hortolândia.

---

Se este projeto foi útil ou interessante, deixe uma ⭐ no repositório.
