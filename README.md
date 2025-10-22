# 🧩 MÓDULO 1: ESTOQUE

📂 Caminho completo:

frontend/
└── src/
    └── pages/
        └── Estoque/
            ├── index.js
            ├── ProdutosList.jsx
            ├── Movimentacoes.jsx
            └── EstoqueResumo.jsx

🔹 index.js (arquivo principal do módulo)
import React from "react";
import ProdutosList from "./ProdutosList";
import Movimentacoes from "./Movimentacoes";
import EstoqueResumo from "./EstoqueResumo";

export default function Estoque() {
  return (
    <div className="page-container">
      <h1>📦 Estoque e Produção</h1>
      <p>Gerencie produtos, entradas, saídas e controle de custo médio.</p>

      <EstoqueResumo />
      <hr style={{ margin: "20px 0" }} />
      <ProdutosList />
      <hr style={{ margin: "20px 0" }} />
      <Movimentacoes />
    </div>
  );
}

🔹 ProdutosList.jsx
import React from "react";

export default function ProdutosList() {
  const produtos = [
    { id: 1, nome: "Camiseta Azul", estoque: 24, custo: 39.9 },
    { id: 2, nome: "Tênis Corrida", estoque: 12, custo: 199.0 },
    { id: 3, nome: "Boné Preto", estoque: 8, custo: 29.9 },
  ];

  return (
    <section>
      <h2>📋 Produtos Cadastrados</h2>
      <table style={{ width: "100%", marginTop: 10, borderCollapse: "collapse" }}>
        <thead>
          <tr style={{ background: "#eee" }}>
            <th>Produto</th>
            <th>Estoque</th>
            <th>Custo Médio (R$)</th>
          </tr>
        </thead>
        <tbody>
          {produtos.map((p) => (
            <tr key={p.id} style={{ textAlign: "center", borderBottom: "1px solid #ddd" }}>
              <td>{p.nome}</td>
              <td>{p.estoque}</td>
              <td>{p.custo.toFixed(2)}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </section>
  );
}

🔹 Movimentacoes.jsx
import React from "react";

export default function Movimentacoes() {
  const movimentacoes = [
    { id: 1, tipo: "Entrada", produto: "Camiseta Azul", qtd: 10, data: "2025-10-15" },
    { id: 2, tipo: "Saída", produto: "Tênis Corrida", qtd: 2, data: "2025-10-18" },
  ];

  return (
    <section>
      <h2>🔄 Movimentações Recentes</h2>
      <table style={{ width: "100%", marginTop: 10, borderCollapse: "collapse" }}>
        <thead>
          <tr style={{ background: "#eee" }}>
            <th>Tipo</th>
            <th>Produto</th>
            <th>Quantidade</th>
            <th>Data</th>
          </tr>
        </thead>
        <tbody>
          {movimentacoes.map((m) => (
            <tr key={m.id} style={{ textAlign: "center", borderBottom: "1px solid #ddd" }}>
              <td>{m.tipo}</td>
              <td>{m.produto}</td>
              <td>{m.qtd}</td>
              <td>{m.data}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </section>
  );
}

🔹 EstoqueResumo.jsx
import React from "react";

export default function EstoqueResumo() {
  return (
    <section>
      <h2>📊 Resumo do Estoque</h2>
      <div style={{ display: "flex", gap: 20, marginTop: 10 }}>
        <div style={boxStyle}>
          <h3>Total de Produtos</h3>
          <p><strong>44</strong></p>
        </div>
        <div style={boxStyle}>
          <h3>Itens em Falta</h3>
          <p><strong>3</strong></p>
        </div>
        <div style={boxStyle}>
          <h3>Valor Total</h3>
          <p><strong>R$ 5.920,00</strong></p>
        </div>
      </div>
    </section>
  );
}

const boxStyle = {
  background: "#f8f8f8",
  padding: 15,
  borderRadius: 6,
  textAlign: "center",
  flex: 1,
  boxShadow: "0 1px 4px rgba(0,0,0,0.1)",
};

🔹 Atualização no Sidebar

Verifique se no seu Sidebar.js já tem o link para o Estoque:

<li><Link to="/estoque">📦 Estoque</Link></li>


Se não tiver, adicione.

🔹 Atualização nas rotas (App.js)

No App.js, adicione:

import Estoque from "./pages/Estoque";


E nas rotas:

<Route path="/estoque" element={<Estoque />} />


✅ Pronto, o módulo Estoque estará funcionando e isolado.
