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

**Esperado:**
```
origin    https://github.com/costaevolve/idevangelismo-9a46b118.git (fetch)
origin    https://github.com/costaevolve/idevangelismo-9a46b118.git (push)
public    https://github.com/costaevolve/Idevangelismo.git (fetch)
public    https://github.com/costaevolve/Idevangelismo.git (push)
```

---

## 🔄 Passo 3: Push para a Repo Pública

```bash
# Push de todos os branches
git push public main

# Ou force push se houver conflitos
git push -u public main --force
```

**O que acontece:**
- ✅ Todos os commits são copiados
- ✅ Todo o histórico é preservado
- ✅ Branches são sincronizados

---

## 🔄 Passo 4: Verificar Sincronização

```bash
# Acesse a repo pública
cd ../Idevangelismo
git clone https://github.com/costaevolve/Idevangelismo.git
cd Idevangelismo

# Verifique o histórico
git log --oneline | head -10
```

**Esperado:** Ver os mesmos ~25 commits

---

## 🔐 Passo 5: Configurar Lovable para Usar a Repo Pública

1. Acesse: **https://lovable.dev/dashboard**
2. Vá para: **Settings → Integrations → GitHub**
3. **Desconecte** `idevangelismo-9a46b118`
4. **Conecte** `Idevangelismo` (repo pública)
5. Confirme as permissões

**O que muda:**
- ✅ Lovable sincroniza com a repo pública
- ✅ Futuros commits aparecerão em `Idevangelismo`
- ✅ Código fica público para colaboração

---

## ⚙️ Passo 6: Configurar CI/CD (Opcional mas Recomendado)

### 6a. Adicionar GitHub Secrets

```
Repository Settings → Secrets and variables → Actions
```

Adicione:
```
SUPABASE_URL         = https://[seu-projeto].supabase.co
SUPABASE_ANON_KEY    = [sua-chave-anonima]
```

### 6b. Criar Workflow de Deploy

Crie: `.github/workflows/deploy.yml`

```yaml
name: Deploy to Lovable

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Notify Lovable
        run: |
          echo "Deployment trigger sent to Lovable"
          # Se Lovable tiver webhook configurado, envie notificação aqui
```

---

## 🧪 Testes de Validação

### Teste 1: Verificar Histórico de Commits

```bash
# Verifique que os commits estão lá
git log --oneline --graph | head -20
```

### Teste 2: Verificar Branches

```bash
# Liste todos os branches
git branch -a
```

### Teste 3: Testar Build Local

```bash
# Install dependencies
npm install

# Build
npm run build

# Test
npm test
```

### Teste 4: Conectar ao Supabase

```bash
# Copie .env.example para .env.local
cp .env.example .env.local

# Adicione credenciais reais:
# VITE_SUPABASE_URL=https://[seu-projeto].supabase.co
# VITE_SUPABASE_ANON_KEY=[sua-chave]

# Execute dev
npm run dev

# Tente acessar http://localhost:5173
```

---

## 🚨 Troubleshooting

### Problema: "fatal: no upstream configured for branch main"

```bash
# Solução:
git push -u public main
```

### Problema: "Permission denied (publickey)"

```bash
# Solução: Configure SSH key
ssh-keygen -t ed25519 -C "seu-email@example.com"
# Adicione a chave em: https://github.com/settings/keys
```

### Problema: Commits não aparecem no GitHub

```bash
# Verifique status
git status

# Se houver alterações não commitadas:
git add .
git commit -m "Sync changes"
git push public main
```

### Problema: Lovable não sincroniza

1. Desconecte em: https://lovable.dev/dashboard/settings
2. Reconecte o repositório `Idevangelismo`
3. Aguarde 2-3 minutos para a sincronização inicial
4. Faça uma pequena mudança no Lovable para testar

---

## 📋 Checklist Final

- [ ] Repositório privado clonado localmente
- [ ] Remote público adicionado (`git remote add public`)
- [ ] Código pushado para repo pública (`git push public main`)
- [ ] Verificado histórico na repo pública
- [ ] Lovable reconectado à repo pública
- [ ] GitHub Secrets configurados (se necessário)
- [ ] Build local testado (`npm run build`)
- [ ] Supabase conectado localmente (`npm run dev`)
- [ ] Teste de push: faça mudança em Lovable e veja commit em GitHub

---

## 🎯 Resultado Esperado

✅ **Repositório Público (`Idevangelismo`):**
- Contém todo o código
- Tem histórico completo de commits
- Está sincronizado com Lovable
- Acessível publicamente

✅ **Repositório Privado (`idevangelismo-9a46b118`):**
- Mantido como backup (opcional)
- Pode ser deletado se não for necessário

✅ **Lovable:**
- Sincronizando com `costaevolve/Idevangelismo`
- Novos commits aparecem em minutos

✅ **Supabase:**
- Conectado e validado
- Credenciais salvas em GitHub Secrets

---

**Tempo estimado:** 15-30 minutos  
**Complexidade:** ⭐⭐ Médio
