# Hackaton-Project-2025
United Generations - solving the loneliness of the eldery and the lack of housing for students in a simple match
## Contexto
Esta aplicação foi desenvolvida em grupo, trabalho de 4 pessoas no âmbito do evento [Hackaton/Buildaton](https://luma.com/wfas10a0) proporcionado pela entidade AlgarveEvolution no [UAlg Tec Campus](https://algarvetechhub.com/facility/ualg-tec-campus).
Nesta Buildaton o principal objetivo foi desenvolver uma aplicação, utilizando como principal recurso a Inteligência Artificial,para combater desafios regionais do Algarve ou Portugal.
Todo o código, inclusive o restante do readme com exceção a esta parte contextual, foi gerado com recurso à Inteligência Artificial [Bolt.new](https://bolt.new/).
Foi também desenvolvido um vídeo para evidenciar as funcionalidades do MVP desenvolvido. O vídeo da app a funcionar pode ser consultado [aqui](/docs/pitchVideo.mp4).

## Introdução
Aplicação web/móvel para conectar idosos com quartos disponíveis e estudantes universitários que procuram alojamento em Portugal.

## 🎯 Objetivo

Combater a solidão dos idosos e facilitar a habitação dos estudantes deslocados (nacionais, internacionais ou Erasmus).

## ✨ Funcionalidades Implementadas

### Autenticação
- ✅ Registo de utilizadores (idosos e estudantes)
- ✅ Login com email/password via Supabase Auth
- ✅ Perfis diferenciados por tipo de utilizador

### Perfis de Utilizador

**Perfil de Idoso:**
- Nome, idade, sexo
- Localidade
- Biografia
- Fotos dos quartos

**Perfil de Estudante:**
- Nome, idade
- Universidade (lista de universidades portuguesas)
- Curso
- Tipo: Nacional, Internacional ou Erasmus
- Biografia

### Gestão de Quartos
- ✅ Idosos podem criar múltiplos anúncios de quartos
- ✅ Informações: título, descrição, tipo, preço mensal, localidade, morada
- ✅ Upload de fotos via URLs (Pexels ou outras fontes)

### Pesquisa e Filtros
- ✅ Estudantes podem procurar quartos
- ✅ Filtro por localidade
- ✅ Pesquisa por texto livre

### Sistema de Candidaturas
- ✅ Estudantes podem candidatar-se a quartos
- ✅ Mensagem opcional na candidatura
- ✅ Idosos podem aceitar ou recusar candidaturas
- ✅ Listagem de candidaturas para cada quarto

### Sistema de Mensagens
- ✅ Chat em tempo real entre idosos e estudantes aceites
- ✅ Histórico de mensagens
- ✅ Notificações de mensagens não lidas

### Favoritos
- ✅ Estudantes podem guardar quartos favoritos
- ✅ Lista de favoritos acessível no perfil

### Avaliações
- ✅ Estudantes podem avaliar quartos (1 a 5 estrelas)
- ✅ Comentários opcionais
- ✅ Apenas estudantes que alugaram podem avaliar
- ✅ Média de avaliações visível

### Base de Dados
- ✅ Schema completo no Supabase (PostgreSQL)
- ✅ Row Level Security (RLS) em todas as tabelas
- ✅ Políticas restritivas por defeito
- ✅ Relações e constraints bem definidas

## 🚧 Funcionalidades Pendentes

### Pagamentos
- ⚠️ **Estrutura de dados preparada mas integração Stripe não implementada**
- Tabelas `rentals` e `payments` criadas
- Cálculo automático da taxa de 5% preparado
- Consultar `STRIPE_SETUP.md` para instruções de implementação

## 🏗️ Arquitetura

### Frontend
- **Framework:** React Native (Expo)
- **Navegação:** Expo Router (file-based routing)
- **UI:** React Native (StyleSheet)
- **Compatibilidade:** Web e Mobile

### Backend
- **BaaS:** Supabase
- **Base de Dados:** PostgreSQL
- **Autenticação:** Supabase Auth
- **Real-time:** Supabase Realtime (mensagens)

## 📁 Estrutura do Projeto

```
app/
├── (tabs)/              # Navegação principal
│   ├── index.tsx        # Home (lista de quartos)
│   ├── search.tsx       # Pesquisa (estudantes)
│   ├── messages.tsx     # Lista de conversas
│   └── profile.tsx      # Perfil do utilizador
├── auth/                # Autenticação
│   ├── login.tsx
│   ├── register.tsx
│   └── complete-profile.tsx
├── rooms/               # Gestão de quartos
│   ├── create.tsx       # Criar anúncio
│   └── [id].tsx         # Detalhes do quarto
├── conversations/
│   └── [id].tsx         # Chat individual
├── room-applications/
│   └── [roomId].tsx     # Candidaturas (idosos)
├── reviews/
│   └── create.tsx       # Criar/editar avaliação
├── favorites.tsx        # Lista de favoritos
└── applications.tsx     # Candidaturas (estudantes)

contexts/
└── AuthContext.tsx      # Gestão de autenticação

lib/
└── supabase.ts          # Cliente Supabase

types/
└── database.ts          # Tipos TypeScript

constants/
└── universities.ts      # Universidades e cidades PT
```

## 🚀 Como Executar

### Requisitos
- Node.js 18+
- npm ou yarn

### Instalação

```bash
# Instalar dependências
npm install

# Iniciar em modo desenvolvimento
npm run dev
```

### Build para Web

```bash
npm run build:web
```

## 🔐 Variáveis de Ambiente

O projeto já está configurado com:

```env
EXPO_PUBLIC_SUPABASE_URL=https://ucyyewcprwpdkilvvgqv.supabase.co
EXPO_PUBLIC_SUPABASE_ANON_KEY=...
```

## 📊 Base de Dados

A base de dados foi criada com migration completa incluindo:

### Tabelas Principais
- `profiles` - Perfis base
- `elderly_profiles` - Info específica de idosos
- `student_profiles` - Info específica de estudantes
- `rooms` - Quartos disponíveis
- `room_photos` - Fotos dos quartos
- `room_applications` - Candidaturas
- `favorites` - Favoritos dos estudantes
- `conversations` - Conversas
- `messages` - Mensagens
- `reviews` - Avaliações
- `rentals` - Contratos de arrendamento
- `payments` - Pagamentos

### Segurança (RLS)
Todas as tabelas têm Row Level Security ativo com políticas que garantem:
- Utilizadores só acedem aos seus próprios dados
- Idosos só veem candidaturas dos seus quartos
- Estudantes só veem as suas candidaturas
- Mensagens apenas visíveis para participantes

## 🎨 Design

- Interface intuitiva adequada para todas as idades (RQ-1)
- Cores neutras e profissionais
- Tipografia clara e legível
- Navegação simples por tabs
- Feedback visual claro para todas as ações

## 📱 Compatibilidade

### Web
✅ Totalmente funcional em navegadores modernos

### Mobile
✅ Layout responsivo
✅ Suporte para iOS e Android via Expo
⚠️ Para testar em dispositivos físicos, use Expo Go ou crie um build de desenvolvimento

## 🔄 Próximos Passos

1. **Implementar Pagamentos Stripe**
   - Configurar chave secreta
   - Criar Edge Functions para checkout
   - Implementar webhooks
   - Testar fluxo completo

2. **Melhorias Futuras**
   - Upload de imagens (Supabase Storage)
   - Notificações push
   - Filtros avançados
   - Relatórios para idosos
   - Sistema de denúncias

3. **Deploy**
   - Web: Vercel, Netlify ou Supabase Hosting
   - Mobile: Build via EAS (Expo Application Services)

## 📄 Licença

Projeto académico desenvolvido para conectar gerações.

## 🤝 Suporte

Para questões sobre:
- **Supabase:** https://supabase.com/docs
- **Expo:** https://docs.expo.dev
