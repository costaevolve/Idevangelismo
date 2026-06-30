# Guia de Sincronização: idevangelismo-9a46b118 → Idevangelismo

**Objetivo:** Sincronizar código do repositório privado com a fork pública

---

## 📌 Situação Atual

| Componente | Status | Detalhes |
|---|---|---|
| **Lovable Project** | ✅ Ativo | Conectado com `idevangelismo-9a46b118` |
| **Repo Pública** | ❌ Vazia | `Idevangelismo` sem código |
| **Repo Privada** | ✅ Com código | `idevangelismo-9a46b118` com ~25 commits |
| **Sincronização** | ❌ Quebrada | Dois repositórios desconectados |

---

## 🔄 Passo 1: Clonar a Repo Privada

```bash
# Clone o repositório privado
git clone https://github.com/costaevolve/idevangelismo-9a46b118.git
cd idevangelismo-9a46b118

# Verifique o histórico
git log --oneline | head -10
```

**Esperado:** Ver ~25 commits com mudanças como:
- "Added auth, profiles & avatars"
- "Criou sistema Netflix da IA"
- "Update site info for publish"

---

## 🔄 Passo 2: Adicionar a Repo Pública como Remote

```bash
# Adicione o repositório público como novo remote
git remote add public https://github.com/costaevolve/Idevangelismo.git

# Verifique os remotes
git remote -v
```

---

## 🔄 Passo 3: Push para a Repo Pública

```bash
# Push de todos os branches
git push public main

# Ou force push se houver conflitos
git push -u public main --force
```

---

## 🔐 Passo 4: Configurar Lovable para Usar a Repo Pública

1. Acesse: **https://lovable.dev/dashboard**
2. Vá para: **Settings → Integrations → GitHub**
3. **Desconecte** `idevangelismo-9a46b118`
4. **Conecte** `Idevangelismo` (repo pública)
5. Confirme as permissões

---

## ⚙️ Passo 5: Configurar GitHub Secrets

```
Repository Settings → Secrets and variables → Actions
```

Adicione:
```
SUPABASE_URL         = https://[seu-projeto].supabase.co
SUPABASE_ANON_KEY    = [sua-chave-anonima]
```

---

## 🧪 Testes de Validação

### Teste 1: Verificar Histórico de Commits

```bash
git log --oneline --graph | head -20
```

### Teste 2: Testar Build Local

```bash
npm install
npm run build
```

### Teste 3: Conectar ao Supabase

```bash
cp .env.example .env.local
# Adicione credenciais reais
npm run dev
```

---

## 📋 Checklist Final

- [ ] Repositório privado clonado localmente
- [ ] Remote público adicionado
- [ ] Código pushado para repo pública
- [ ] Verificado histórico na repo pública
- [ ] Lovable reconectado à repo pública
- [ ] GitHub Secrets configurados
- [ ] Build local testado
- [ ] Supabase conectado localmente

---

**Tempo estimado:** 15-30 minutos  
**Complexidade:** ⭐⭐ Médio