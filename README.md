# Documentação de Requisitos: Plataforma E-commerce NitroGear

Este documento serve como a especificação formal de requisitos para o desenvolvimento da plataforma web da **NitroGear**, uma empresa focada no comércio eletrônico de hardware de alta performance e soluções integradas de logística de distribuição. 

A plataforma deve ser dividida em dois grandes módulos independentes, porém integrados por uma base de dados relacional robusta: o **Storefront** (público, focado na experiência do cliente e alta conversão) e o **Backoffice** (privado, focado no controle operacional e gerenciamento de estoque).

---

## 1. Diretrizes de Design e Interface

### 1.1 Identidade Visual e Estética
* **Tema Principal:** Obrigatoriamente *Dark Mode* nativo, utilizando uma paleta de cores premium baseada em tons de grafite, cinza escuro e preto, com acentos sutis e desaturados para destacar o design das peças de hardware.
* **Abordagem Visual:** Design minimalista, limpo e profissional. Estão expressamente proibidas estéticas retrô, carregadas ou extravagantes. O foco deve ser a clareza das informações e o apelo visual dos produtos.

### 1.2 Responsividade e Layout
* **Arquitetura de Layout:** Todo o posicionamento estrutural da interface deve ser desenvolvido utilizando **Flexbox** para garantir flexibilidade absoluta, alinhamento fluido e adaptabilidade perfeita entre diferentes tamanhos de tela (desde monitores Ultrawide até smartphones de baixa resolução).
* **Framework:** Compatibilidade total com Tailwind CSS para a estilização ágil através de classes utilitárias, facilitando a manutenção e a consistência dos componentes.

---

## 2. Especificação do Módulo Storefront (Área do Cliente)

O Storefront compreende todas as telas acessíveis pelo usuário final, estruturadas de forma linear para otimizar o funil de vendas.

### 2.1 Header Global (Cabeçalho)
* **Logo Corporativa:** Posicionada no canto superior esquerdo, atuando como link de retorno para a página inicial.
* **Barra de Busca Inteligente:** Centralizada. Deve possuir funcionalidade de preenchimento automático (*auto-complete*) e sugestão de produtos em tempo real à medida que o usuário digita.
* **Menu de Navegação:** Links diretos para as categorias principais da loja: *Placas de Vídeo*, *Monitores*, *Periféricos* e *Promoções*.
* **Menu do Usuário:** Link para controle de sessão ("Login / Cadastre-se") que se transforma em "Minha Conta" após a autenticação.
* **Ícone do Carrinho:** Exibição dinâmica da quantidade de itens adicionados. Suporte a *mini-cart* expansível em formato de popover ao passar o mouse (*hover*).

### 2.2 Homepage (Página Inicial)
* **Hero Banner:** Seção de destaque no topo com transição fluida, exibindo campanhas de lançamentos da loja (ex: "A Nova Era da Performance Chegou!").
* **Vitrine de Destaques:** Carrossel ou grade de produtos focada em custo-benefício, exibindo itens selecionados como:
  * Placa de Vídeo NitroForce GTX 1650 4GB
  * Placa de Vídeo Nitro Radeon RX 550 Ti 4GB
  * Monitor Gamer NitroVision 21.5" Full HD
* **Cards de Produto:** Cada item na grade deve exibir: imagem em alta definição, título oficial, preço anterior, preço promocional atual com destaque, etiquetas de status ("Mais Vendido", "Promoção") e um botão de ação rápida "Adicionar ao Carrinho".
* **Navegação por Categoria:** Blocos visuais simplificados na parte inferior para direcionamento rápido do usuário.

### 2.3 Página de Categorias e Busca
* **Filtros Avançados (Faceted Search):** Painel lateral permitindo filtragem combinada por:
  * Faixa de preço (controle deslizante ou inputs numéricos).
  * Marca / Fabricante.
  * Atributos técnicos específicos (ex: quantidade de VRAM para placas de vídeo, taxa de atualização ou tamanho para monitores).
* **Ordenação Dinâmica:** Seletor para organizar os resultados por menor preço, maior preço, mais vendidos ou lançamentos.
* **Grade de Resultados:** Renderização responsiva com suporte a paginação estruturada ou carregamento contínuo sob demanda ("Lazy Loading").

### 2.4 Página de Detalhes do Produto (PDP)
* **Galeria de Mídias:** Exibição da imagem principal do hardware com suporte a zoom interativo e miniaturas navegáveis na lateral ou parte inferior.
* **Painel de Compra (Buy Box):** Exibição clara do título, marca, selo de disponibilidade em estoque, valor com desconto para pagamento à vista (Pix/Boleto) e opções de parcelamento no cartão. Botão de conversão "Comprar" em posição de destaque.
* **Simulador Logístico:** Campo de entrada para CEP com integração para cálculo instantâneo do valor do frete e estimativa de prazo de entrega.
* **Ficha Técnica Dinâmica:** Seção estruturada em tabelas HTML para exibir as especificações do produto de forma customizada, adaptando-se caso o produto seja um componente (VRAM, clock) ou um periférico (DPI, switches).
* **Módulo de Avaliações (Reviews):** Exibição de notas por estrelas e comentários de clientes que adquiriram o hardware.

### 2.5 Checkout e Finalização de Compra
* **Carrinho de Compras:** Tela de revisão detalhada com alteração de quantidades, remoção de itens e aplicação de cupons de desconto.
* **Fluxo de Checkout Unificado:**
  1. Identificação/Autenticação simplificada.
  2. Seleção de Endereço de Entrega (puxando dados cadastrados ou permitindo inserção rápida).
  3. Seleção do Método de Envio (opções econômicas e expressas).
  4. Tela de Pagamento segura integrada com gateways (Cartão de Crédito, Pix dinâmico com QR Code e Boleto Bancário).
* **Página de Confirmação:** Mensagem de sucesso, resumo da compra e o número do pedido gerado para rastreamento.

### 2.6 Painel da Área Logada (Minha Conta)
* **Histórico de Pedidos:** Listagem completa de compras anteriores.
* **Rastreamento de Pedido:** Linha do tempo interativa que reflete o status logístico exato do pacote (*Pedido Recebido -> Pagamento Aprovado -> Em Separação no Galpão -> Despachado -> Entregue*).
* **Gerenciador de Perfil:** Atualização de dados cadastrais, alteração de senhas e carteira de endereços salvos.

### 2.7 Atendimento ao Cliente (Chat ao Vivo)
* **Widget Flutuante:** Fixado no canto inferior direito do Storefront, permitindo comunicação direta em tempo real com a equipe de suporte para resolução de dúvidas técnicas de compatibilidade de hardware.

---

## 3. Especificação do Módulo Backoffice (Painel Administrativo)

O Backoffice é a aplicação restrita utilizada pela equipe interna da NitroGear para gerenciar toda a operação comercial e logística.

### 3.1 Painel de Controle (Dashboard)
* **Métricas em Tempo Real:** Exibição gráfica e numérica do faturamento diário, volume de pedidos aprovados, quantidade de chamados de suporte em aberto e alertas automáticos de estoque crítico (abaixo do limite mínimo).

### 3.2 Controle de Catálogo (Produtos)
* **Operações CRUD Completas:** Interface dedicada para criar, ler, atualizar e deletar registros de produtos no banco de dados.
* **Campos de Cadastro:** Armazenamento estruturado de SKU, código de barras, nome descritivo, especificações textuais, categorização hierárquica, upload de imagens e precificação (preço de custo vs. preço de venda).
* **Sincronização de Estoque:** Dedução automática de unidades do estoque físico assim que a confirmação de pagamento de um pedido é recebida do gateway.

### 3.3 Gestão Logística e Pedidos
* **Painel de Ordens:** Listagem centralizada de todas as transações, filtráveis por status do ciclo de vida do pedido.
* **Despacho Logístico:** Interface para alteração manual ou automatizada dos status do pedido. Inclui campo dedicado para inserção do código de rastreamento oficial emitido pela transportadora parceira.

### 3.4 Gestão de Clientes
* **Base de Dados:** Consulta detalhada dos clientes cadastrados, permitindo visualizar perfis de consumo, histórico de compras efetuadas e dados de contato diretos para suporte.

---

## 4. Requisitos Não-Funcionais e Restrições Técnicas

* **Segurança:** Toda a área do Backoffice e as rotas de checkout do Storefront devem exigir autenticação estrita. Senhas devem ser criptografadas antes do armazenamento.
* **Persistência:** Banco de dados relacional sólido para assegurar a integridade referencial entre produtos, estoques, clientes e pedidos.
* **Desempenho:** Carregamento rápido de imagens e componentes de interface para mitigar a taxa de rejeição no Storefront.