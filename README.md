# Grocerio - Lista de Compras com Histórico Mensal

Grocerio é um aplicativo de **lista de compras** em uma única página (HTML + CSS + JS) pensado para rodar direto no **GitHub Pages**. Ele salva tudo no **localStorage** do seu navegador - sem servidor - e mantém **histórico por mês**, com totais e agrupamento por categoria.

## Destaques
- Lista atual com itens, quantidade, unidade, preço, categoria, marcação de concluído e notas.
- KPIs em tempo real: total estimado, itens e marcados.
- Salvar a compra do dia no histórico do mês com um clique.
- Histórico mensal com:
  - Total do mês, contagem de compras e itens.
  - Agrupamento por categoria.
  - Lista de compras do mês, com subtotal de cada compra.
  - Recarregar uma compra passada para a lista atual.
  - Excluir compras do histórico.
  - Exportar CSV do mês.
- Backup/restore: exportar JSON completo e importar depois.
- Busca rápida na lista.
- Layout responsivo (desktop e mobile) e tema claro.

## Como usar
1. Abra o `index.html` em um navegador moderno ou publique no GitHub Pages.
2. Adicione itens na **Lista atual** (nome, quantidade, unidade, preço e categoria).
3. Use a busca para filtrar itens rapidamente.
4. Clique em **Salvar compra** para registrar a lista do dia no histórico do mês atual (YYYY-MM).
5. Acesse o painel à direita, selecione um mês e visualize:
   - Totais do mês e por categoria.
   - Compras individuais com data/hora, quantidade de itens e subtotal.
   - Ações: **Recarregar para lista** (reaproveitar) e **Excluir**.
6. Exporte o mês atual em **CSV** ou o banco completo em **JSON**. Também é possível **importar** um JSON previamente exportado.
7. O botão **Zerar tudo** apaga a lista e todo o histórico.

## Publicando no GitHub Pages
1. Crie um repositório novo no GitHub (por exemplo, `grocerio`).
2. Envie estes arquivos: `index.html`, `README.md`, `LICENSE`.
3. Vá em **Settings → Pages** e selecione deploy a partir da branch `main` (pasta root).
4. Acesse a URL informada pelo GitHub Pages para usar o aplicativo.

## Estrutura de dados (localStorage)
- `grocerio.v2.items`: array de itens da **lista atual**. Cada item:  
  ```json
  { "id": "uuid", "name": "Arroz 5kg", "qty": 1, "unit": "un", "price": 22.90, "category": "Geral", "checked": false, "note": "" }
  ```
- `grocerio.v2.history`: objeto mapeando `YYYY-MM` → array de compras. Cada compra:  
  ```json
  { "date": "2025-09-20T14:22:00.000Z", "items": [ /* mesma estrutura dos itens */ ] }
  ```

## Privacidade
Todos os dados ficam **apenas no seu navegador**. Não há coleta remota nem backend.

## Acessibilidade e compatibilidade
- Controle por teclado nos campos do formulário e ações por botões claramente rotulados.
- Requer um navegador moderno com suporte a `localStorage` e `crypto.randomUUID()`.

## Limitações e roadmap
- O histórico é local ao dispositivo/navegador. Para sincronizar entre dispositivos, utilize **Exportar/Importar**.
- Não há categorias personalizadas dinâmicas. Isso pode ser estendido no futuro.
- Possível evolução: orçamentos mensais, gráficos de evolução, múltiplas listas, multiusuário via backend opcional.

## Licença
Distribuído sob a **MIT License**. Veja `LICENSE`.
