# Controle de Férias — Zukkin · GitHub + Firebase · falta só isso

O código já está pronto e publicado no GitHub Pages. Falta só ligar o banco de dados
(Firebase/Firestore) — sem isso o painel abre, mas nada que os gestores digitarem fica
salvo. É o mesmo processo já feito pro painel de Banco de Horas.

## 1. Criar o projeto no Firebase

1. Acesse [console.firebase.google.com](https://console.firebase.google.com) → **Adicionar projeto**.
2. Nome sugerido: `zukkin-controle-ferias`. Plano gratuito **Spark** é suficiente.
3. **Compilação → Authentication** → **Vamos começar** → habilite o provedor **Anônimo**
   ("Anonymous"). É só pra regra do Firestore funcionar — ninguém vê tela de login do
   Firebase (o painel já tem a própria tela de entrada por time + senha).
4. **Compilação → Firestore Database** → **Criar banco de dados** → região
   `southamerica-east1` (ou a mesma do banco de horas) → **modo de produção**.

## 2. Pegar as credenciais do app

1. ⚙️ **Configurações do projeto** → em **Seus apps**, clique no ícone `</>` (Web) pra
   registrar um app (não precisa marcar Hosting).
2. Copie o objeto `firebaseConfig` mostrado na tela e me envie aqui no chat — eu
   preencho o `index.html` e faço o push. (Se preferir editar você mesmo: é o bloco
   perto do fim do arquivo, `const firebaseConfig = {...}`.)

## 3. Publicar as regras do Firestore

Mais rápido pela própria interface: **Firestore Database → Regras**, cole o conteúdo de
`firestore.rules` (já está neste repositório) e clique em **Publicar**.

(Alternativa via linha de comando, se preferir: `npm install -g firebase-tools`,
`firebase login`, `firebase use --add`, `firebase deploy --only firestore:rules`.)

## 4. Carregar os colaboradores no banco

Depois que o projeto estiver criado e eu tiver o `firebaseConfig`, eu mesmo carrego os
64 colaboradores da planilha original no Firestore — não precisa fazer nada manual
aqui.

## 5. Testar

1. Acesse https://zukkinrh.github.io/controle-ferias/
2. Entre com o time "RH — administração" e a senha de administração.
3. Confira se os colaboradores aparecem e se dá pra marcar um período como enviado.
4. Abra o mesmo link de outro computador (ou peça pra outra pessoa) e confirme que a
   mudança aparece lá também — é o sinal de que o Firestore está funcionando como banco
   compartilhado de verdade.

---

Senhas de acesso por time (troque quando quiser, estão em `PIN_MAP` no `index.html`):

| Time | Senha |
|---|---|
| Operações | zukkinop |
| Zpromo | zukkinpromo |
| Projetos | zukkinpj |
| Qualidade | zukkinql |
| Desenvolvimento | 8036 |
| Zrobot | zukkinrobot |
| RH (administração — vê tudo, marca "Enviado") | zukkinrh |
