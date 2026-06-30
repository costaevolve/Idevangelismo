# Idevangelismo

Plataforma de evangelismo digital com autenticação, gestão de perfis e integração com Supabase.

## 🔗 Repositórios

- **Repositório Principal (Público):** https://github.com/costaevolve/Idevangelismo
- **Repositório de Desenvolvimento (Privado):** https://github.com/costaevolve/idevangelismo-9a46b118

## 🚀 Stack Tecnológico

- **Frontend:** TypeScript, React
- **Backend:** Node.js
- **Database:** Supabase (PostgreSQL)
- **Editor:** Lovable (lovable.dev)
- **Hospedagem:** idevangelismo.lovable.app

## 📋 Funcionalidades

- ✅ Autenticação de usuários
- ✅ Gestão de perfis
- ✅ Sistema de avatares
- ✅ Netflix da IA (Recomendações)

## 🔧 Setup Local

```bash
# Clone o repositório
git clone https://github.com/costaevolve/Idevangelismo.git
cd Idevangelismo

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env.local

# Inicie o desenvolvimento
npm run dev
```

## 📦 Variáveis de Ambiente Necessárias

```
VITE_SUPABASE_URL=https://[project].supabase.co
VITE_SUPABASE_ANON_KEY=[your-key]
VITE_API_URL=https://idevangelismo.lovable.app
```

## 🔗 Links Importantes

- **App em Produção:** https://idevangelismo.lovable.app
- **Dashboard Lovable:** https://lovable.dev
- **Supabase Project:** https://supabase.com/dashboard

## 📝 Status da Integração

**Última Atualização:** 2026-06-30

| Integração | Status | Notas |
|---|---|---|
| GitHub ↔ Lovable | ⚠️ Reconfigurar | Repositório privado está sendo usado |
| Lovable ↔ Supabase | ⚠️ Verificar | Credenciais precisam validação |
| Deploys Automáticos | ❌ Não Configurado | CI/CD pipeline necessário |

## 🚨 Problemas Conhecidos

- [ ] Sincronização GitHub: Repo pública vazia, código em repo privada
- [ ] Falta workflow de CI/CD
- [ ] Variáveis de ambiente não sincronizadas

## 📧 Suporte

Para questões sobre a integração, consulte a documentação:
- Lovable: https://lovable.dev/docs
- Supabase: https://supabase.com/docs
