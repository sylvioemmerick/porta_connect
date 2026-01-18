# Porta Connect (Laravel)

Este repositório contém a base do Laravel para o projeto Porta Connect.

## Deploy na Locaweb

A estrutura abaixo considera a aplicação em **/public_html/app** e a raiz pública em **/public_html/testapp**.

1. **Crie as pastas no servidor**:
   - `/public_html/app`
   - `/public_html/testapp`

2. **Envie os arquivos da aplicação**:
   - Faça upload de todo o projeto (exceto a pasta `public`) para `/public_html/app`.
   - Faça upload do conteúdo da pasta `public` para `/public_html/testapp`.

3. **Ajuste o `index.php` da pasta pública** (`/public_html/testapp/index.php`) para apontar para a aplicação:

   ```php
   require __DIR__ . '/../app/vendor/autoload.php';

   $app = require_once __DIR__ . '/../app/bootstrap/app.php';
   ```

4. **Crie o `.env`** (não versionado):

   ```bash
   cp /public_html/app/.env.example /public_html/app/.env
   php82 /public_html/app/artisan key:generate
   ```

   Ajuste as variáveis de ambiente (APP_URL, DB_*, etc.) conforme o ambiente.

5. **Instale dependências no servidor**:

   ```bash
   cd /public_html/app
   php82 composer install --no-dev --optimize-autoloader
   ```

6. **Permissões de escrita**:

   ```bash
   chmod -R 775 /public_html/app/storage /public_html/app/bootstrap/cache
   ```

7. **Migrações e storage link** (se necessário):

   ```bash
   php82 /public_html/app/artisan migrate --force
   php82 /public_html/app/artisan storage:link
   ```

### Observações

- O arquivo `.env` **não** deve ser versionado. Use `.env.example` como base.
- O `.htaccess` padrão do Laravel já está em `public/.htaccess` para roteamento correto.
