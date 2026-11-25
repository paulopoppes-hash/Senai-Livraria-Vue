<template>
  <div class="app">
    <header class="cabecalho">
      <h1>Senai - Livraria Vue</h1>
      <p class="subtitulo">Descubra ótimos livros para ler. Desenvolvido com Vue 3 + Vite.</p>
    </header>

    <div class="controles">
      <input
        v-model="filtro"
        type="text"
        placeholder="Buscar por título ou autor..."
        class="input-busca"
      />
      <button @click="selecionarLivro(null)" class="btn-limpar">Limpar seleção</button>
    </div>

    <div class="livros-grid">
      <div
        v-for="(livro, index) in livrosFiltrados"
        :key="index"
        class="card-livro"
        :class="{ selecionado: livroSelecionado === livro }"
        @click="selecionarLivro(livro)"
      >
        <div class="capa">{{ livro.iniciais }}</div>
        <h3 class="titulo">{{ livro.titulo }}</h3>
        <p class="autor">por {{ livro.autor }}</p>
        <p class="descricao">{{ livro.descricao }}</p>
      </div>
    </div>

    <div v-if="livroSelecionado" class="detalhe">
      <h2>Livro selecionado</h2>
      <p><strong>Título:</strong> {{ livroSelecionado.titulo }}</p>
      <p><strong>Autor:</strong> {{ livroSelecionado.autor }}</p>
      <p><strong>Descrição:</strong> {{ livroSelecionado.descricao }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface Livro {
  id: number
  titulo: string
  autor: string
  descricao: string
  iniciais: string
}

const livros = ref<Livro[]>([
  { id: 1, titulo: 'Clean Code', autor: 'Robert C. Martin', descricao: 'Guia de boas práticas de programação e desenvolvimento de software limpo.', iniciais: 'CC' },
  { id: 2, titulo: 'Design Patterns', autor: 'Gang of Four', descricao: 'Padrões de projeto de software reutilizáveis orientados a objetos.', iniciais: 'DP' },
  { id: 3, titulo: 'Você Não Sabe JS ainda', autor: 'Kyle Simpson', descricao: 'Aprofundamento nos mecanismos do JavaScript.', iniciais: 'YNJS' },
  { id: 4, titulo: 'Refatoração', autor: 'Martin Fowler', descricao: 'Melhoria do design de código existente sem alterar seu comportamento externo.', iniciais: 'R' },
  { id: 5, titulo: 'Arquitetura Limpa', autor: 'Robert C. Martin', descricao: 'Princípios de arquitetura de software para sistemas sustentáveis.', iniciais: 'AC' },
])

const filtro = ref('')
const livroSelecionado = ref<Livro | null>(null)

const livrosFiltrados = computed(() => {
  if (!filtro.value) return livros.value
  const termo = filtro.value.toLowerCase()
  return livros.value.filter(
    (l) => l.titulo.toLowerCase().includes(termo) || l.autor.toLowerCase().includes(termo)
  )
})

function selecionarLivro(livro: Livro | null) {
  livroSelecionado.value = livro
}
</script>

<style scoped>
.app {
  max-width: 1000px;
  margin: 0 auto;
  padding: 24px;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.cabecalho {
  text-align: center;
  margin-bottom: 32px;
}

.cabecalho h1 {
  color: #4fc08d;
  margin-bottom: 8px;
}

.subtitulo {
  color: #666;
  font-size: 1rem;
}

.controles {
  display: flex;
  gap: 12px;
  margin-bottom: 24px;
  flex-wrap: wrap;
}

.input-busca {
  flex: 1;
  min-width: 200px;
  padding: 10px 16px;
  border: 1px solid #ddd;
  border-radius: 6px;
  font-size: 0.95rem;
}

.btn-limpar {
  padding: 10px 18px;
  border: 1px solid #ddd;
  border-radius: 6px;
  background: #fff;
  cursor: pointer;
  font-size: 0.9rem;
}

.btn-limpar:hover {
  background: #f5f5f5;
}

.livros-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 16px;
}

.card-livro {
  background: #fff;
  border: 2px solid #ddd;
  border-radius: 10px;
  padding: 16px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
}

.card-livro:hover {
  border-color: #4fc08d;
  transform: translateY(-2px);
}

.card-livro.selecionado {
  border-color: #4fc08d;
  background: #f0fdf4;
}

.capa {
  width: 60px;
  height: 60px;
  background: #e5e7eb;
  border-radius: 8px;
  margin: 0 auto 12px auto;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 1.2rem;
  color: #666;
}

.titulo {
  margin: 0 0 6px 0;
  color: #333;
  font-size: 1.1rem;
}

.autor {
  margin: 0 0 8px 0;
  color: #666;
  font-size: 0.9rem;
  font-style: italic;
}

.descricao {
  margin: 0;
  color: #888;
  font-size: 0.85rem;
}

.detalhe {
  margin-top: 24px;
  padding: 16px;
  background: #f0fdf4;
  border: 1px solid #4fc08d;
  border-radius: 8px;
}

.detalhe h2 {
  margin-top: 0;
  color: #166534;
}
</style>
