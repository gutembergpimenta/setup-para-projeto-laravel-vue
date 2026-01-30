# Instalação do PHP + COMPOSER + LARAVEL INSTALLER
- [php.new](https://www.php.new)
---

---
# Instalação Laravel
- Instalação limpa padrão sem start kits.
```
laravel new [project-name]
```
---
-  instalação do sail
```
php artisan sail:install
```
---
- Adicionar algumas config. em App/Providers/AppServiceProvider.php (DENTRO DO METHOD boot())
```
   //Ativar modo estrito
   Model::shouldBeStrict(!$this->app->isProduction());
```
```
   //Proibir uso de comandos destrutivos em produção
   DB::prohibitDestructiveCommands($this->app->isProduction());
```
```
   //Carregamento forçado/agressivo 
   Vite::useAggressivePrefetching();
```
```
   //Força uso do HTTPS em produção 
   URL::forceHttps($this->app->isProduction());
```
```
   //Padrão de senha em produção 
   Password::defaults(fn (): ?Password : $this->app->isProduction()? Password::min(12)->max(255)->uncompramised() : null);
```
---

---
# Instalação do pacote de tradução PT-BR

-link do [repositorio](https://github.com/lucascudo/laravel-pt-BR-localization)
    
# Instalação do InertiaJS #
SSR (CONFORME DOCUMENTAÇÃO) 

CSS (CONFORME DOCUMENTAÇÃO) <br>

`Instalar pacote @vitejs/plugin-vue` <br>
conforme [documentação](https://laravel.com/docs/12.x/vite#vue)<br>
`Configurar plugig laravel vite` <br>
conforme [documentação](https://laravel.com/docs/12.x/vite#inertia)
---

---

# Instalação do TypeScript
```
npm install -D typescript
```
```
npx -p typescript tsc --init
```
```
criar/substiuir o arquivos `src/tsconfig.json` para raiz do projeto laravel
```
---

---
# Instalação do Prettier
```
//Comando para instalação do Prettier: 

npm install prettier prettier-plugin-organize-imports prettier-plugin-classnames prettier-plugin-merge prettier-plugin-tailwindcss -D   
```

```
//Instalação de recursos do TailwindCSS:

npm install tailwind-merge clsx class-variance-authority tw-animate-css -D
```

```
//Comandos do package.json:

"prettier:analyse": "prettier --check resources/"
"prettier:execute": "prettier --write resources/"
```

```
criar o arquivos `src/.prettierrc` para raiz do projeto laravel
```
---

---
# Instalação do Eslint
```
//Comando para instalação do Eslint: 

npm install -D eslint @eslint/js eslint-config-prettier eslint-plugin-vue @vue/eslint-config-typescript typescript-eslint   
```

```
//Comandos do package.json:

"lint": "eslint . --fix"

```

```
criar/colar o arquivos `src/eslint.config.ts` para raiz do projeto laravel
```
---

---
# Instalação do WayFinder

- Instalação conforme [documentação](https://github.com/laravel/wayfinder)
- Apos instalação do WayFinder, instale e configure o Vite Plugin Wayfinder também conforme [documentação](https://github.com/laravel/vite-plugin-wayfinder)
---

---
# Instalação do Ziggy

- Instalação conforme [documentação](https://github.com/tighten/ziggy)

```
//adicionar no tsconfig.ts
"compilerOptions": {
    "paths": {
        // ...
        "ziggy-js": ["./vendor/tightenco/ziggy"],
    },
        
    "types": [
        // ...
        "./vendor/tightenco/ziggy/src/js/index.d.ts"
    ]
}
```
---

---
# Instalação do Laravel Rector (OPCIONAL)

- Instalação conforme [documentação](https://github.com/rectorphp/rector)
- instalação do pacote rector-laravel conforme [documentação](https://github.com/driftingly/rector-laravel)

```
criar/colar o arquivo `src/rector.php` na raiz do projeto
```
---

---
# Instalação do Laravel Pint (OPCIONAL)

- Instalação conforme [documentação](https://laravel.com/docs/12.x/pint)

```
criar/colar o arquivo `src/pint.php` na raiz do projeto
```
---

---
# Instalação do Laravel LaraStan (OPCIONAL)

- Instalação conforme [documentação](https://github.com/larastan/larastan)
- Documentação sobre os níveis [documentação](https://phpstan.org/user-guide/rule-levels)

```
criar/colar o arquivo `src/phpstan.neon` na raiz do projeto
```
```
// comando para Executação:
./vendor/bin/phpstan analyse --memory-limit=2G
```
# Script de QA (composer.json)

```
//Scripts Individuais de Análise:

"rector:analyse": [
    "vendor/bin/rector process --dry-run || true"
],
"pint:analyse": [
    "vendor/bin/pint --test || true"
],
"larastan": [
    "vendor/bin/phpstan analyse --memory-limit=2G"
]
```
```
// Scripts Individuais de Execução:

"rector:execute": [
    "vendor/bin/rector process || true"
],
"pint:execute": [
    "vendor/bin/pint || true"
]
```
```
// Script de QA:

"analyse": [
    "@rector:analyse",
    "@pint:analyse",
    "@larastan"
],
"qa": [
    "@rector:execute",
    "@pint:execute"
]
```
