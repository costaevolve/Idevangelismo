# Instruções de Setup - Idevangelismo

## 🚀 Início Rápido

### Pré-requisitos

- Node.js 18+
- npm ou yarn
- Conta Supabase
- Conta GitHub

### Instalação Local

```bash
# Clone o repositório
git clone https://github.com/costaevolve/Idevangelismo.git
cd Idevangelismo

# Instale dependências
npm install

# Configure variáveis de ambiente
cp .env.example .env.local

# Inicie o servidor de desenvolvimento
npm run dev
```

### Configurar Supabase

1. Acesse https://supabase.com/dashboard
2. Crie um novo projeto ou use existente
3. Copie URL e Anon Key
4. Adicione em `.env.local`:

```env
VITE_SUPABASE_URL=https://[seu-id].supabase.co
VITE_SUPABASE_ANON_KEY=[sua-chave]
VITE_API_URL=https://idevangelismo.lovable.app
```

### Executar Testes

```bash
# Testes unitários
npm test

# Build de produção
npm run build

# Preview da build
npm run preview
```

---

## 🔐 Segurança

### Nunca commitar:

- `.env.local` ou credenciais
- Chaves privadas
- Tokens de acesso pessoais

### Sempre usar:

- `.env.example` como template
- GitHub Secrets para CI/CD
- Variáveis de ambiente para configuração

---

## 🐛 Troubleshooting

### "Cannot find module"

```bash
rm -rf node_modules package-lock.json
npm install
```

### "Supabase connection failed"

1. Verifique `.env.local`
2. Confirme credenciais em supabase.com
3. Teste conexão: `npm run dev`

### "Port 5173 already in use"

```bash
# Use porta diferente
npm run dev -- --port 3000
```

---

## 📚 Documentação

- [README.md](./README.md) - Visão geral do projeto
- [SYNC_GUIDE.md](./SYNC_GUIDE.md) - Sincronização de repositórios
- [INTEGRATION_STATUS.md](./INTEGRATION_STATUS.md) - Status das integrações
- [.env.example](./.env.example) - Variáveis de ambiente

---

## 📞 Suporte

Para dúvidas:
- Lovable: https://lovable.dev/support
- Supabase: https://supabase.com/docs
- GitHub: https://github.com/costaevolve/Idevangelismo/issues