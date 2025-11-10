# Prova-14.11

Isso recria o banco e roda o servidor.
/api
dotnet restore
dotnet ef database update
dotnet run

options.UseSqlite("Data Source=app.db");

# Comandos Importntes 

Instalar dependências	npm i	Baixa tudo que está no package.json

Rodar o projeto	npm start

Corrigir dependências quebradas	npm audit fix	Corrige falhas leves

Remover módulos e reinstalar	rmdir /s /q node_modules && del package-lock.json && npm i


# Models de Porduto generio front

export default interface Produto{
   id? : string;
   nome : string;
   descricao : string;
   quantidade : number;
   preco : number;
   criadoEm? : string; 
}


na pasta prova/
npx create-react-app front --template typescript
cd front
npm install axios react-router-dom
npm i react-router-dom
CRUD GENERICO
// src/pages/Cadastro.tsx
import { useState } from "react";
import { api } from "../api";

export function Cadastro() {
  const [nome, setNome] = useState("");
  const [valor, setValor] = useState("");

  const salvar = async () => {
    try {
      await api.post("/produtos", { nome, valor });
      alert("Cadastrado!");
    } catch (error) {
      alert("Erro ao salvar");
      console.error(error);
    }
  };

  return (
    <div>
      <h1>Cadastrar Produto</h1>
      <input value={nome} onChange={e => setNome(e.target.value)} placeholder="Nome" />
      <input value={valor} onChange={e => setValor(e.target.value)} placeholder="Valor" />
      <button onClick={salvar}>Salvar</button>
    </div>
  );
}
