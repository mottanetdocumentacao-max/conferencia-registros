# 📡 Conferência de Registros – Instalações e Mudanças

Sistema de conferência em tempo real hospedado no GitHub Pages com banco de dados Firebase.

---

## 📁 Estrutura dos arquivos

```
conferencia-site/
├── index.html          ← aplicação principal
├── firebase-config.js  ← suas credenciais do Firebase (você preenche)
├── data.js             ← os 1.504 registros (não editar)
└── README.md           ← este arquivo
```

---

## 🚀 Passo a passo completo

### PARTE 1 — Criar o banco de dados Firebase (5 minutos)

1. Acesse **https://console.firebase.google.com**
2. Clique em **"Adicionar projeto"**
3. Dê um nome (ex: `conferencia-provedor`) → clique em Continuar
4. Desative o Google Analytics (não precisa) → clique em **"Criar projeto"**
5. Quando carregar, no menu lateral esquerdo clique em **"Realtime Database"**
6. Clique em **"Criar banco de dados"**
7. Escolha a localização **"us-central1"** → clique em Próxima
8. Selecione **"Iniciar no modo de teste"** → clique em **Ativar**

> ⚠️ O modo de teste permite leitura/escrita por 30 dias. Depois disso você precisará configurar as regras (veja PARTE 4).

---

### PARTE 2 — Pegar as credenciais do Firebase

1. No painel do projeto Firebase, clique na engrenagem ⚙️ ao lado de "Visão geral do projeto"
2. Clique em **"Configurações do projeto"**
3. Role a página até **"Seus aplicativos"**
4. Clique no ícone **`</>`** (Web)
5. Dê um apelido (ex: `conferencia-web`) → clique em **"Registrar app"**
6. Você verá um bloco assim:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "conferencia-provedor.firebaseapp.com",
  databaseURL: "https://conferencia-provedor-default-rtdb.firebaseio.com",
  projectId: "conferencia-provedor",
  storageBucket: "conferencia-provedor.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

7. **Copie esses valores** e cole no arquivo `firebase-config.js` substituindo os `"COLE_AQUI"`

---

### PARTE 3 — Publicar no GitHub Pages

1. Acesse **https://github.com** e faça login
2. Clique em **"New repository"** (botão verde)
3. Nome do repositório: `conferencia-registros` (ou qualquer nome)
4. Deixe como **Public** → clique em **"Create repository"**
5. Na tela seguinte, clique em **"uploading an existing file"**
6. Arraste os 4 arquivos da pasta (`index.html`, `firebase-config.js`, `data.js`, `README.md`)
7. Clique em **"Commit changes"**
8. Vá em **Settings** → **Pages** (menu lateral)
9. Em "Branch", selecione **main** → pasta **/ (root)** → clique em **Save**
10. Aguarde ~1 minuto e o site estará disponível em:
    ```
    https://SEU_USUARIO.github.io/conferencia-registros/
    ```

---

### PARTE 4 — Regras de segurança do Firebase (após 30 dias)

Quando o modo de teste expirar, vá em **Realtime Database → Regras** e cole:

```json
{
  "rules": {
    "conferencias": {
      ".read": true,
      ".write": true
    }
  }
}
```

> Para mais segurança no futuro, é possível restringir por autenticação. Me avise se quiser configurar isso.

---

### PARTE 5 — Ver os dados salvos

Você pode ver e editar os dados diretamente no Firebase:

1. Acesse o console do projeto
2. Clique em **Realtime Database**
3. Todos os registros conferidos aparecem ali organizados por número de protocolo
4. Dá para exportar como JSON clicando nos **3 pontinhos (⋮)** → "Exportar JSON"

---

## 👥 Compartilhar com a equipe

Depois de publicar, basta enviar o link para João, Millena e Jair:
```
https://SEU_USUARIO.github.io/conferencia-registros/
```
Todos verão os dados em **tempo real** — quando um aprovar, os outros veem na hora.

---

## ❓ Problemas comuns

| Problema | Solução |
|---|---|
| Tela de loading não sai | Verifique se o `firebase-config.js` está preenchido corretamente |
| "Erro ao conectar" | Verifique se o Realtime Database foi criado e está no modo teste |
| Site mostra 404 | Aguarde alguns minutos após ativar o GitHub Pages |
| Dados não salvam depois de 30 dias | Configure as regras conforme a PARTE 4 |
