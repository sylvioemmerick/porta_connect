# Porta Connect - Laravel 11

Este repositório contém o esqueleto do Laravel 11 (PHP 8.2) para o Porta Connect.

## Requisitos

- PHP 8.2 (CLI `php82` na Locaweb)
- Composer

## Instalação local

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan serve
```

## Locaweb

### Homologação

- Diretório: `/public_html/testapp`
- PHP CLI: `php82`

Exemplo:

```bash
cd /public_html/testapp
php82 artisan key:generate
```

### Produção

- Diretório: `/public_html/app`
- PHP CLI: `php82`

Exemplo:

```bash
cd /public_html/app
php82 artisan key:generate
```

## Deploy

Os workflows existentes em `.github/workflows` são responsáveis pelo deploy. Caso sejam ajustados, as mudanças devem ser documentadas neste README.
