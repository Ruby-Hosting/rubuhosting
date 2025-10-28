 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
index 6456fedaa43eb0d2802c1f90322ffe0c5ede3339..2f7010171eb1aa598c7a83b28a668f5675e0b926 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,121 @@
-# rubuhosting
\ No newline at end of file
+# Tema Ruby Hosting para Paymenter
+
+Este repositório contém um tema exclusivo e moderno para o painel [Paymenter](https://paymenter.org/) inspirado na identidade visual da Ruby Hosting. O pacote inclui layout completo para as páginas internas do cliente, telas de autenticação e componentes personalizados que reforçam o branding da empresa.
+
+## Recursos principais
+
+- **Paleta rubra personalizada** com gradientes e sombras sutis que remetem à Ruby Hosting.
+- **Layouts Blade** (`app` e `auth`) prontos para integração com o Paymenter.
+- **Componentes reutilizáveis** (`<x-theme-layout>` e `<x-theme-auth-layout>`) para montar telas rapidamente.
+- **CSS modular** com variáveis para ajuste de cores, espaçamentos e tipografia.
+- **Ativos visuais** (logos em SVG, cartões KPI, hero section) compatíveis com modo escuro.
+- **JS leve** para toggles da sidebar e pílulas de status.
+
+## Estrutura de pastas
+
+```
+themes/
+└── ruby-hosting/
+    ├── theme.json
+    ├── assets/
+    │   ├── css/app.css
+    │   ├── js/app.js
+    │   └── images/logo-*.svg
+    ├── layouts/
+    │   ├── app.blade.php
+    │   └── auth.blade.php
+    ├── components/
+    │   ├── hero.blade.php
+    │   ├── logo.blade.php
+    │   ├── theme-auth-layout.blade.php
+    │   └── theme-layout.blade.php
+    ├── auth/
+    │   ├── login.blade.php
+    │   └── register.blade.php
+    └── dashboard.blade.php
+```
+
+## Instalação no Paymenter
+
+1. Copie a pasta `themes/ruby-hosting` para `resources/views/themes/` dentro da sua instalação do Paymenter.
+2. Limpe o cache de views com:
+
+   ```bash
+   php artisan view:clear
+   ```
+
+3. Ajuste o arquivo `config/paymenter.php` (ou o local equivalente) para definir `theme` como `ruby-hosting`.
+4. Publique ou compile seus assets, caso utilize o mix/webpack padrão:
+
+   ```bash
+   php artisan vendor:publish --tag=paymenter-themes --force
+   npm run build
+   ```
+
+5. Atualize seus layouts ou rotas para utilizar as views Blade fornecidas:
+
+   ```php
+   return view('themes.ruby-hosting.dashboard', [
+       'activeServices' => 8,
+       'pendingInvoices' => 2,
+       'openTickets' => 1,
+   ]);
+   ```
+
+## Personalização
+
+- Ajuste as variáveis CSS em `assets/css/app.css` para alterar cores, espaçamentos e sombras.
+- Substitua as logos SVG em `assets/images` pelos arquivos oficiais da Ruby Hosting.
+- Expanda os componentes Blade para abranger páginas adicionais (faturas, tickets, serviços, etc.).
+
+## Como enviar o tema para o seu repositório no GitHub
+
+1. Crie um repositório vazio no GitHub e copie a URL `git@github.com:usuario/repositorio.git` (ou a URL HTTPS, se preferir).
+2. Configure seu nome e e-mail, caso ainda não tenha feito:
+
+   ```bash
+   git config --global user.name "Seu Nome"
+   git config --global user.email "seu-email@exemplo.com"
+   ```
+
+3. Verifique o status das alterações localmente:
+
+   ```bash
+   git status
+   ```
+
+4. Adicione os arquivos modificados e crie um commit:
+
+   ```bash
+   git add .
+   git commit -m "feat: adicionar tema Ruby Hosting"
+   ```
+
+5. Caso ainda não exista um repositório remoto configurado, adicione o do GitHub:
+
+   ```bash
+   git remote add origin git@github.com:usuario/repositorio.git
+   ```
+
+6. Envie o histórico local para o GitHub:
+
+   ```bash
+   git push -u origin main
+   ```
+
+   > Substitua `main` pelo nome da sua branch principal, caso utilize outro padrão (por exemplo, `master`).
+
+7. Ao trabalhar em novas alterações, crie branches de feature e abra Pull Requests para facilitar revisões e deploys controlados:
+
+   ```bash
+   git checkout -b feat/nome-da-feature
+   git push -u origin feat/nome-da-feature
+   ```
+
+8. No GitHub, abra um Pull Request a partir da branch publicada, descreva as alterações e, após aprovação, faça o merge na branch principal.
+
+Com isso, o tema ficará versionado e sincronizado com o repositório remoto da Ruby Hosting.
+
+## Licença
+
+Distribuição reservada à Ruby Hosting. Consulte o time jurídico antes de redistribuir ou comercializar este tema.
 
EOF
)
