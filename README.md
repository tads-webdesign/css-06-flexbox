# Tutorial Completo: Layout Responsivo com Flexbox

## Índice
1. [Conceito de Flexbox e quando usar](#1-conceito-de-flexbox-e-quando-usar)
2. [Container Flex](#2-container-flex)
3. [Items Flex](#3-items-flex)
4. [Alinhamento e Distribuição de Espaço](#alinhamento-e-distribuicao-de-espaco)
5. [Casos de Uso Práticos](#casos-de-uso-praticos)
6. [Exemplo Completo](#exemplo-completo)
7. [Links e Conteúdos Avançados](#links-e-conteudos-avancados)

---

## 1. Conceito de Flexbox e quando usar

### 1.1. O que é Flexbox?

Flexbox (Flexible Box Layout) é um módulo CSS3 que facilita o design de estruturas de layout flexíveis e responsivas sem usar float ou position.
Ele permite distribuir espaço entre itens de um container e alinhá-los de forma eficiente, mesmo quando seus tamanhos são desconhecidos ou dinâmicos.

### 1.2. Quando usar Flexbox?

Use Flexbox quando você precisar:
- Alinhar elementos em uma única dimensão (linha ou coluna)
- Centralizar elementos vertical e horizontalmente
- Distribuir espaço entre itens automaticamente
- Criar layouts responsivos sem media queries complexas
- Ordenar elementos visualmente sem alterar o HTML
- Criar componentes como navbars, cards, footers, formulários

### 1.3. Exemplo básico

[Exemplo de código](exemplos/1-1-flex-basico.html)

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flexbox Básico</title>
    <style>
        .container {
            display: flex;
            background-color: #f0f0f0;
            padding: 10px;
        }
        
        .item {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            margin: 5px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="item">Item 1</div>
        <div class="item">Item 2</div>
        <div class="item">Item 3</div>
    </div>
</body>
</html>
```

```css
.container {
    display: flex; /* Transforma o elemento em um flex container */
}
```

---

## 2. Container Flex

O container flex é o elemento pai que controla o layout de seus filhos (flex items). 
Para criar um container flex, use `display: flex` ou `display: inline-flex`.

### 2.1. `display: flex`

Transforma um elemento em um flex container, fazendo com que seus filhos diretos se tornem flex items.

[Exemplo de código](exemplos/2-1-flex-container.html)

```html
<div class="flex-container">
    <div>Item 1</div>
    <div>Item 2</div>
    <div>Item 3</div>
</div>

<div class="flex-container-inline">
    <div>Item 1</div>
    <div>Item 2</div>
    <div>Item 3</div>
</div>
```

```css
.flex-container {
    display: flex; /* Container em bloco */
}

/* ou */

.flex-container-inline {
    display: inline-flex; /* Container inline */
}
```

### 2.2. `flex-direction`

Define a direção principal em que os flex items são colocados no container.

[exemplo de código](exemplos/2-2-flex-direction.html)

```html
<div class="container-row">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
</div>

<div class="container-column">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
</div>
```

```css
.container-row {
    display: flex;
    flex-direction: row; /* Padrão: da esquerda para direita */
}

.container-row-reverse {
    display: flex;
    flex-direction: row-reverse; /* Da direita para esquerda */
}

.container-column {
    display: flex;
    flex-direction: column; /* De cima para baixo */
}

.container-column-reverse {
    display: flex;
    flex-direction: column-reverse; /* De baixo para cima */
}

.box {
    padding: 20px;
    background-color: #3498db;
    color: white;
    margin: 5px;
}
```

### 2.3. `justify-content`

Alinha os flex items ao longo do eixo principal (horizontal se flex-direction: row).

[Exemplo de código](exemplos/2-3-flex-justify-content.html)

```html
<div class="container-center">
    <div class="item">A</div>
    <div class="item">B</div>
    <div class="item">C</div>
</div>
```

```css
.container-center {
    display: flex;
    justify-content: flex-start; /* Início do container (padrão) */
}

.container-end {
    display: flex;
    justify-content: flex-end; /* Final do container */
}

.container-center-justified {
    display: flex;
    justify-content: center; /* Centralizado */
}

.container-space-between {
    display: flex;
    justify-content: space-between; /* Espaço entre os itens */
}

.container-space-around {
    display: flex;
    justify-content: space-around; /* Espaço ao redor dos itens */
}

.container-space-evenly {
    display: flex;
    justify-content: space-evenly; /* Espaço uniforme */
}
```

### 2.4. `align-items`

Alinha os flex items ao longo do eixo transversal (vertical se flex-direction: row).

[Exemplo de código](exemplos/2-4-flex-align-items.html)

```html
<div class="container-align">
    <div class="item small">Pequeno</div>
    <div class="item medium">Médio</div>
    <div class="item large">Grande</div>
</div>
```

```css
.container-align {
    display: flex;
    height: 200px;
    align-items: stretch; /* Estica os itens (padrão) */
}

.container-align-start {
    display: flex;
    height: 200px;
    align-items: flex-start; /* Topo do container */
}

.container-align-end {
    display: flex;
    height: 200px;
    align-items: flex-end; /* Base do container */
}

.container-align-center {
    display: flex;
    height: 200px;
    align-items: center; /* Centro vertical */
}

.container-align-baseline {
    display: flex;
    height: 200px;
    align-items: baseline; /* Linha base do texto */
}

.small { height: 50px; }
.medium { height: 80px; }
.large { height: 120px; }
```

### 2.5. Outras propriedades importantes do container

```css
.container-completo {
    display: flex;
    flex-wrap: wrap; /* Permite quebra de linha */
    align-content: center; /* Alinha linhas múltiplas */
    gap: 10px; /* Espaçamento entre itens */
}
```

---

## 3. Items Flex

Os items flex são os filhos diretos de um container flex. Você pode controlar como eles crescem, encolhem e seu tamanho base.

### 3.1. `flex-grow`

Define a capacidade de um item crescer, se necessário. O valor padrão é 0 (não cresce).

[Exemplo de código](exemplos/3-1-flex-grow.html)

```html
<div class="container">
    <div class="item grow-1">flex-grow: 1</div>
    <div class="item grow-2">flex-grow: 2</div>
    <div class="item grow-1">flex-grow: 1</div>
</div>
```

```css
.container {
    display: flex;
}

.grow-1 {
    flex-grow: 1; /* Cresce 1 unidade */
    background-color: #3498db;
}

.grow-2 {
    flex-grow: 2; /* Cresce 2 unidades (ocupa o dobro) */
    background-color: #e74c3c;
}
```

### 3.2. `flex-shrink`

Define a capacidade de um item encolher, se necessário. O valor padrão é 1 (pode encolher).

[Exemplo de código](exemplos/3-2-flex-shrink.html)

```html
<div class="container-narrow">
    <div class="item shrink-0">Não encolhe</div>
    <div class="item shrink-1">Pode encolher</div>
    <div class="item shrink-2">Encolhe mais</div>
</div>
```

```css
.container-narrow {
    display: flex;
    width: 400px;
}

.shrink-0 {
    flex-shrink: 0; /* Não encolhe */
    width: 200px;
}

.shrink-1 {
    flex-shrink: 1; /* Encolhe normalmente */
    width: 200px;
}

.shrink-2 {
    flex-shrink: 2; /* Encolhe duas vezes mais rápido */
    width: 200px;
}
```

### 3.3. `flex-basis`

Define o tamanho inicial de um item antes do espaço restante ser distribuído.

[Exemplo de código](exemplos/3-3-flex-basis.html)

```html
<div class="container">
    <div class="item basis-auto">auto</div>
    <div class="item basis-200">200px</div>
    <div class="item basis-30">30%</div>
</div>
```

```css
.basis-auto {
    flex-basis: auto; /* Baseado no conteúdo (padrão) */
}

.basis-200 {
    flex-basis: 200px; /* Tamanho inicial de 200px */
}

.basis-30 {
    flex-basis: 30%; /* Tamanho inicial de 30% */
}

.basis-0 {
    flex-basis: 0; /* Ignora o tamanho do conteúdo */
}
```

### 3.4. `flex` (shorthand)

A propriedade `flex` é uma forma abreviada de definir `flex-grow`, `flex-shrink` e `flex-basis`.

[Exemplo de código](exemplos/3-4-flex-shorthand.html)

```html
<div class="container">
    <div class="item flex-1">flex: 1</div>
    <div class="item flex-2">flex: 2</div>
    <div class="item flex-custom">flex: 1 2 200px</div>
</div>
```

```css
.flex-1 {
    flex: 1; /* flex-grow: 1, flex-shrink: 1, flex-basis: 0% */
}

.flex-2 {
    flex: 2; /* flex-grow: 2, flex-shrink: 1, flex-basis: 0% */
}

.flex-custom {
    flex: 1 2 200px; /* grow: 1, shrink: 2, basis: 200px */
}

.flex-none {
    flex: none; /* 0 0 auto - não cresce nem encolhe */
}

.flex-auto {
    flex: auto; /* 1 1 auto - flexível baseado no conteúdo */
}
```

### 3.5. Outras propriedades importantes dos items

```css
.item-especial {
    align-self: center; /* Sobrescreve align-items do container */
    order: -1; /* Muda a ordem visual (padrão: 0) */
}
```

---

## 4. Alinhamento e Distribuição de Espaço

### 4.1. Centralização Perfeita

Um dos usos mais comuns do Flexbox é centralizar elementos vertical e horizontalmente.

[Exemplo de código](exemplos/4-1-flex-center.html)

```html
<div class="center-container">
    <div class="center-content">
        <h2>Perfeitamente Centralizado!</h2>
        <p>Vertical e horizontalmente</p>
    </div>
</div>
```

```css
.center-container {
    display: flex;
    justify-content: center; /* Centraliza horizontalmente */
    align-items: center; /* Centraliza verticalmente */
    height: 100vh; /* Altura total da viewport */
    background-color: #ecf0f1;
}

.center-content {
    background-color: white;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}
```

### 4.2. Distribuição de Espaço com Gap

[Exemplo de código](exemplos/4-2-gap.html)
```html
<div class="spaced-container">
    <div class="card">Card 1</div>
    <div class="card">Card 2</div>
    <div class="card">Card 3</div>
</div>
```

```css
.spaced-container {
    display: flex;
    gap: 20px; /* Espaço entre todos os itens */
    padding: 20px;
}

/* Gaps específicos */
.container-with-gaps {
    display: flex;
    row-gap: 20px; /* Espaço vertical */
    column-gap: 10px; /* Espaço horizontal */
    flex-wrap: wrap;
}
```

### 4.3. Combinações Práticas

[Exemplo de código](exemplos/4-3-combinacoes-praticas.html)

```css
/* Layout com sidebar e conteúdo principal */
.layout {
    display: flex;
    min-height: 100vh;
}

.sidebar {
    flex: 0 0 250px; /* Não cresce, não encolhe, 250px fixo */
    background-color: #2c3e50;
}

.main-content {
    flex: 1; /* Ocupa todo o espaço restante */
    padding: 20px;
}

/* Grid responsivo */
.grid {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.grid-item {
    flex: 1 1 300px; /* Cresce, encolhe, mínimo 300px */
}
```

---

## 5. Casos de Uso Práticos

### 1. Navbar Responsiva

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Navbar com Flexbox</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #2c3e50;
            padding: 1rem 2rem;
            color: white;
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .nav-links a:hover {
            color: #3498db;
        }
        
        .nav-button {
            background-color: #3498db;
            padding: 0.5rem 1.5rem;
            border: none;
            border-radius: 5px;
            color: white;
            cursor: pointer;
        }
        
        @media (max-width: 768px) {
            .navbar {
                flex-direction: column;
                gap: 1rem;
            }
            
            .nav-links {
                flex-direction: column;
                text-align: center;
                gap: 0.5rem;
            }
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="logo">MeuSite</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#sobre">Sobre</a></li>
            <li><a href="#servicos">Serviços</a></li>
            <li><a href="#contato">Contato</a></li>
        </ul>
        <button class="nav-button">Login</button>
    </nav>
</body>
</html>
```

### 2. Cards Responsivos

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cards com Flexbox</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 2rem;
            background-color: #f5f5f5;
        }
        
        .cards-container {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
            justify-content: center;
        }
        
        .card {
            flex: 1 1 300px;
            max-width: 350px;
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
        }
        
        .card-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2rem;
        }
        
        .card-content {
            padding: 1.5rem;
        }
        
        .card-title {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
            color: #2c3e50;
        }
        
        .card-description {
            color: #7f8c8d;
            line-height: 1.6;
            margin-bottom: 1rem;
        }
        
        .card-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .card-button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 5px;
            cursor: pointer;
        }
        
        .card-price {
            font-size: 1.25rem;
            font-weight: bold;
            color: #27ae60;
        }
    </style>
</head>
<body>
    <div class="cards-container">
        <div class="card">
            <div class="card-image">📱</div>
            <div class="card-content">
                <h3 class="card-title">Plano Básico</h3>
                <p class="card-description">
                    Perfeito para iniciantes que querem começar com recursos essenciais.
                </p>
                <div class="card-footer">
                    <span class="card-price">R$ 29,90</span>
                    <button class="card-button">Escolher</button>
                </div>
            </div>
        </div>
        
        <div class="card">
            <div class="card-image">💼</div>
            <div class="card-content">
                <h3 class="card-title">Plano Pro</h3>
                <p class="card-description">
                    Para profissionais que precisam de recursos avançados e suporte prioritário.
                </p>
                <div class="card-footer">
                    <span class="card-price">R$ 79,90</span>
                    <button class="card-button">Escolher</button>
                </div>
            </div>
        </div>
        
        <div class="card">
            <div class="card-image">🚀</div>
            <div class="card-content">
                <h3 class="card-title">Plano Enterprise</h3>
                <p class="card-description">
                    Solução completa para empresas com necessidades específicas e customização.
                </p>
                <div class="card-footer">
                    <span class="card-price">R$ 199,90</span>
                    <button class="card-button">Escolher</button>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

### 3. Footer Responsivo

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Footer com Flexbox</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }
        
        .content {
            flex: 1;
            padding: 2rem;
        }
        
        .footer {
            background-color: #2c3e50;
            color: white;
            padding: 3rem 2rem 1rem;
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
            margin-bottom: 2rem;
        }
        
        .footer-section {
            flex: 1 1 250px;
        }
        
        .footer-section h3 {
            margin-bottom: 1rem;
            color: #3498db;
        }
        
        .footer-section ul {
            list-style: none;
        }
        
        .footer-section ul li {
            margin-bottom: 0.5rem;
        }
        
        .footer-section a {
            color: #bdc3c7;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-section a:hover {
            color: #3498db;
        }
        
        .footer-social {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .social-icon {
            width: 40px;
            height: 40px;
            background-color: #34495e;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            color: white;
            transition: background-color 0.3s;
        }
        
        .social-icon:hover {
            background-color: #3498db;
        }
        
        .footer-bottom {
            border-top: 1px solid #34495e;
            padding-top: 1rem;
            text-align: center;
            color: #95a5a6;
        }
        
        @media (max-width: 768px) {
            .footer-content {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="content">
        <h1>Conteúdo Principal</h1>
        <p>O footer ficará sempre no final da página.</p>
    </div>
    
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-section">
                <h3>Sobre Nós</h3>
                <p>Somos uma empresa dedicada a criar soluções incríveis para nossos clientes.</p>
                <div class="footer-social">
                    <a href="#" class="social-icon">f</a>
                    <a href="#" class="social-icon">t</a>
                    <a href="#" class="social-icon">in</a>
                    <a href="#" class="social-icon">ig</a>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Links Rápidos</h3>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#servicos">Serviços</a></li>
                    <li><a href="#portfolio">Portfólio</a></li>
                    <li><a href="#blog">Blog</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Recursos</h3>
                <ul>
                    <li><a href="#documentacao">Documentação</a></li>
                    <li><a href="#suporte">Suporte</a></li>
                    <li><a href="#faq">FAQ</a></li>
                    <li><a href="#api">API</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Contato</h3>
                <ul>
                    <li>📧 contato@exemplo.com</li>
                    <li>📱 (11) 99999-9999</li>
                    <li>📍 São Paulo, SP</li>
                </ul>
            </div>
        </div>
        
        <div class="footer-bottom">
            <p>&copy; 2024 MeuSite. Todos os direitos reservados.</p>
        </div>
    </footer>
</body>
</html>
```

---

## Exemplo Completo

Aqui está um exemplo completo de uma página web responsiva usando todos os conceitos de Flexbox apresentados:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Landing Page Completa - Flexbox</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
        }
        
        /* NAVBAR */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #2c3e50;
            padding: 1rem 5%;
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #3498db;
        }
        
        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
            font-weight: 500;
        }
        
        .nav-links a:hover {
            color: #3498db;
        }
        
        .nav-cta {
            background-color: #3498db;
            color: white;
            padding: 0.7rem 1.5rem;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s;
        }
        
        .nav-cta:hover {
            background-color: #2980b9;
        }
        
        /* HERO SECTION */
        .hero {
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 80vh;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 2rem 5%;
        }
        
        .hero-content {
            display: flex;
            align-items: center;
            gap: 4rem;
            max-width: 1200px;
            flex-wrap: wrap;
        }
        
        .hero-text {
            flex: 1 1 400px;
        }
        
        .hero-text h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            line-height: 1.2;
        }
        
        .hero-text p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }
        
        .hero-buttons {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }
        
        .btn-primary, .btn-secondary {
            padding: 1rem 2rem;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .btn-primary {
            background-color: white;
            color: #667eea;
            font-weight: bold;
        }
        
        .btn-secondary {
            background-color: transparent;
            color: white;
            border: 2px solid white;
        }
        
        .btn-primary:hover, .btn-secondary:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
        
        .hero-image {
            flex: 1 1 400px;
            display: flex;
            justify-content: center;
        }
        
        .placeholder-image {
            width: 100%;
            max-width: 500px;
            height: 400px;
            background-color: rgba(255,255,255,0.1);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
        }
        
        /* FEATURES SECTION */
        .features {
            padding: 5rem 5%;
            background-color: #f8f9fa;
        }
        
        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #2c3e50;
        }
        
        .section-subtitle {
            text-align: center;
            font-size: 1.2rem;
            color: #7f8c8d;
            margin-bottom: 3rem;
        }
        
        .features-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .feature-card {
            flex: 1 1 300px;
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }
        
        .feature-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }
        
        .feature-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #2c3e50;
        }
        
        .feature-card p {
            color: #7f8c8d;
            line-height: 1.6;
        }
        
        /* PRICING SECTION */
        .pricing {
            padding: 5rem 5%;
            background-color: white;
        }
        
        .pricing-cards {
            display: flex;
            justify-content: center;
            gap: 2rem;
            flex-wrap: wrap;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .pricing-card {
            flex: 1 1 280px;
            max-width: 350px;
            background-color: white;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            padding: 2rem;
            text-align: center;
            transition: transform 0.3s, border-color 0.3s;
        }
        
        .pricing-card:hover {
            transform: scale(1.05);
            border-color: #3498db;
        }
        
        .pricing-card.featured {
            border-color: #3498db;
            box-shadow: 0 5px 25px rgba(52, 152, 219, 0.3);
        }
        
        .pricing-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #2c3e50;
        }
        
        .price {
            font-size: 3rem;
            font-weight: bold;
            color: #3498db;
            margin-bottom: 0.5rem;
        }
        
        .price-period {
            color: #7f8c8d;
            margin-bottom: 2rem;
        }
        
        .pricing-features {
            list-style: none;
            margin-bottom: 2rem;
        }
        
        .pricing-features li {
            padding: 0.5rem 0;
            border-bottom: 1px solid #f0f0f0;
        }
        
        .pricing-button {
            width: 100%;
            padding: 1rem;
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .pricing-button:hover {
            background-color: #2980b9;
        }
        
        /* FOOTER */
        .footer {
            background-color: #2c3e50;
            color: white;
            padding: 3rem 5% 1rem;
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto 2rem;
        }
        
        .footer-section {
            flex: 1 1 250px;
        }
        
        .footer-section h3 {
            margin-bottom: 1rem;
            color: #3498db;
        }
        
        .footer-section ul {
            list-style: none;
        }
        
        .footer-section ul li {
            margin-bottom: 0.5rem;
        }
        
        .footer-section a {
            color: #bdc3c7;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-section a:hover {
            color: #3498db;
        }
        
        .footer-social {
            display: flex;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .social-icon {
            width: 40px;
            height: 40px;
            background-color: #34495e;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
            color: white;
            transition: background-color 0.3s;
        }
        
        .social-icon:hover {
            background-color: #3498db;
        }
        
        .footer-bottom {
            border-top: 1px solid #34495e;
            padding-top: 1rem;
            text-align: center;
            color: #95a5a6;
        }
        
        /* RESPONSIVE */
        @media (max-width: 768px) {
            .navbar {
                flex-direction: column;
                gap: 1rem;
                padding: 1rem;
            }
            
            .nav-links {
                flex-direction: column;
                text-align: center;
                gap: 0.5rem;
            }
            
            .hero-text h1 {
                font-size: 2rem;
            }
            
            .hero-content {
                flex-direction: column;
                text-align: center;
            }
            
            .hero-buttons {
                justify-content: center;
            }
            
            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- NAVBAR -->
    <nav class="navbar">
        <div class="logo">FlexSite</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#features">Recursos</a></li>
            <li><a href="#pricing">Preços</a></li>
            <li><a href="#contact">Contato</a></li>
        </ul>
        <button class="nav-cta">Começar Grátis</button>
    </nav>
    
    <!-- HERO SECTION -->
    <section class="hero" id="home">
        <div class="hero-content">
            <div class="hero-text">
                <h1>Construa Sites Incríveis com Flexbox</h1>
                <p>Aprenda a criar layouts modernos, responsivos e elegantes usando o poder do CSS Flexbox.</p>
                <div class="hero-buttons">
                    <button class="btn-primary">Começar Agora</button>
                    <button class="btn-secondary">Ver Demo</button>
                </div>
            </div>
            <div class="hero-image">
                <div class="placeholder-image">🚀</div>
            </div>
        </div>
    </section>
    
    <!-- FEATURES SECTION -->
    <section class="features" id="features">
        <h2 class="section-title">Recursos Principais</h2>
        <p class="section-subtitle">Tudo que você precisa para criar layouts profissionais</p>
        
        <div class="features-grid">
            <div class="feature-card">
                <div class="feature-icon">⚡</div>
                <h3>Rápido e Eficiente</h3>
                <p>Crie layouts complexos com poucas linhas de código CSS.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">📱</div>
                <h3>Totalmente Responsivo</h3>
                <p>Seus layouts se adaptam perfeitamente a qualquer tamanho de tela.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🎨</div>
                <h3>Flexível e Poderoso</h3>
                <p>Controle total sobre alinhamento e distribuição de espaço.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🔧</div>
                <h3>Fácil de Usar</h3>
                <p>API intuitiva que facilita o aprendizado e desenvolvimento.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">🌐</div>
                <h3>Suporte Universal</h3>
                <p>Compatível com todos os navegadores modernos.</p>
            </div>
            
            <div class="feature-card">
                <div class="feature-icon">💡</div>
                <h3>Documentação Completa</h3>
                <p>Tutoriais e exemplos para todos os níveis de experiência.</p>
            </div>
        </div>
    </section>
    
    <!-- PRICING SECTION -->
    <section class="pricing" id="pricing">
        <h2 class="section-title">Escolha Seu Plano</h2>
        <p class="section-subtitle">Planos flexíveis para todas as necessidades</p>
        
        <div class="pricing-cards">
            <div class="pricing-card">
                <h3>Básico</h3>
                <div class="price">R$ 29</div>
                <div class="price-period">por mês</div>
                <ul class="pricing-features">
                    <li>✓ 5 Projetos</li>
                    <li>✓ Suporte por Email</li>
                    <li>✓ Documentação</li>
                    <li>✓ Atualizações</li>
                </ul>
                <button class="pricing-button">Escolher Plano</button>
            </div>
            
            <div class="pricing-card featured">
                <h3>Profissional</h3>
                <div class="price">R$ 79</div>
                <div class="price-period">por mês</div>
                <ul class="pricing-features">
                    <li>✓ Projetos Ilimitados</li>
                    <li>✓ Suporte Prioritário</li>
                    <li>✓ Templates Premium</li>
                    <li>✓ Recursos Avançados</li>
                </ul>
                <button class="pricing-button">Escolher Plano</button>
            </div>
            
            <div class="pricing-card">
                <h3>Enterprise</h3>
                <div class="price">R$ 199</div>
                <div class="price-period">por mês</div>
                <ul class="pricing-features">
                    <li>✓ Tudo do Pro</li>
                    <li>✓ Suporte 24/7</li>
                    <li>✓ Customização</li>
                    <li>✓ Treinamento Dedicado</li>
                </ul>
                <button class="pricing-button">Escolher Plano</button>
            </div>
        </div>
    </section>
    
    <!-- FOOTER -->
    <footer class="footer" id="contact">
        <div class="footer-content">
            <div class="footer-section">
                <h3>FlexSite</h3>
                <p>Construindo o futuro da web com tecnologias modernas e acessíveis.</p>
                <div class="footer-social">
                    <a href="#" class="social-icon">f</a>
                    <a href="#" class="social-icon">t</a>
                    <a href="#" class="social-icon">in</a>
                    <a href="#" class="social-icon">ig</a>
                </div>
            </div>
            
            <div class="footer-section">
                <h3>Produto</h3>
                <ul>
                    <li><a href="#features">Recursos</a></li>
                    <li><a href="#pricing">Preços</a></li>
                    <li><a href="#">Casos de Uso</a></li>
                    <li><a href="#">Atualizações</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Recursos</h3>
                <ul>
                    <li><a href="#">Documentação</a></li>
                    <li><a href="#">Tutoriais</a></li>
                    <li><a href="#">Blog</a></li>
                    <li><a href="#">Comunidade</a></li>
                </ul>
            </div>
            
            <div class="footer-section">
                <h3>Empresa</h3>
                <ul>
                    <li><a href="#">Sobre Nós</a></li>
                    <li><a href="#">Carreiras</a></li>
                    <li><a href="#">Contato</a></li>
                    <li><a href="#">Parceiros</a></li>
                </ul>
            </div>
        </div>
        
        <div class="footer-bottom">
            <p>&copy; 2024 FlexSite. Todos os direitos reservados.</p>
        </div>
    </footer>
</body>
</html>
```

---

## Links e Conteúdos Avançados

### Documentação Oficial

1. **MDN Web Docs - Flexbox**
   - https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Flexible_Box_Layout
   - Documentação completa e detalhada sobre Flexbox

2. **CSS-Tricks - A Complete Guide to Flexbox**
   - https://css-tricks.com/snippets/css/a-guide-to-flexbox/
   - Guia visual e interativo (em inglês)

3. **W3C Specification**
   - https://www.w3.org/TR/css-flexbox-1/
   - Especificação oficial do W3C

### Ferramentas Interativas

4. **Flexbox Froggy**
   - https://flexboxfroggy.com/
   - Jogo interativo para aprender Flexbox

5. **Flexbox Defense**
   - http://www.flexboxdefense.com/
   - Aprenda Flexbox jogando Tower Defense

6. **Flexbox Playground**
   - https://codepen.io/enxaneta/full/adLPwv
   - Experimente propriedades do Flexbox em tempo real

### Tutoriais em Vídeo

7. **Curso Web Moderno com JavaScript (Cod3r)**
   - Seção sobre CSS Flexbox

8. **Traversy Media - Flexbox Crash Course**
   - https://www.youtube.com/watch?v=3YW65K6LcIA
   - Tutorial completo em inglês

9. **Rocketseat - Flexbox**
   - Conteúdos gratuitos sobre Flexbox

### Artigos e Recursos Avançados

10. **Flexbox Patterns**
    - https://www.flexboxpatterns.com/
    - Padrões comuns de layout com Flexbox

11. **Smashing Magazine - Flexbox Articles**
    - https://www.smashingmagazine.com/tag/flexbox/
    - Artigos avançados sobre Flexbox

12. **Can I Use - Flexbox**
    - https://caniuse.com/flexbox
    - Compatibilidade do Flexbox com navegadores

### Ferramentas de Desenvolvimento

13. **Flexbox Cheatsheet**
    - https://yoksel.github.io/flex-cheatsheet/
    - Referência rápida visual

14. **Flexy Boxes**
    - https://the-echoplex.net/flexyboxes/
    - Gerador de código Flexbox

15. **CSS Grid vs Flexbox**
    - https://ishadeed.com/article/grid-layout-flexbox-components/
    - Quando usar Grid ou Flexbox

### Comunidades e Fóruns

16. **Stack Overflow - Flexbox Tag**
    - https://stackoverflow.com/questions/tagged/flexbox
    - Perguntas e respostas da comunidade

17. **Reddit - r/css**
    - https://www.reddit.com/r/css/
    - Comunidade sobre CSS

### Livros Recomendados

18. **"CSS: The Definitive Guide" - Eric Meyer**
    - Capítulos dedicados ao Flexbox

19. **"CSS Secrets" - Lea Verou**
    - Técnicas avançadas de CSS incluindo Flexbox

### Próximos Passos

Após dominar o Flexbox, considere aprender:
- **CSS Grid**: Para layouts bidimensionais mais complexos
- **CSS Custom Properties**: Variáveis CSS para maior flexibilidade
- **Responsive Design**: Media queries e design mobile-first
- **CSS Animations**: Transições e animações
- **Sass/SCSS**: Pré-processadores CSS para código mais organizado

---

## Exercícios Práticos

Para consolidar seu aprendizado, tente criar:
1. Uma página de perfil de usuário com foto, informações e cards
2. Um dashboard com sidebar fixa e área de conteúdo
3. Uma galeria de fotos responsiva
4. Um formulário de login centralizado
5. Uma página de e-commerce com filtros e grid de produtos

**Boa sorte no seu aprendizado de Flexbox! 🚀**
