# PRD — Jogo Casual de Adivinhação de Palavras (Wordle-style PT-BR)

**Versão:** 0.1 (rascunho)
**Data:** 2026-10-14
**Owner:** (a definir)
**Status:** Rascunho para revisão

---

## 1. Visão e Objetivo

Jogo casual **web, gratuito e sem conta/login** de adivinhação de palavra diária em **5 letras**, inspirado em Wordle/Termo, com foco em **simplicidade, acessibilidade e experiência sem distrações** (sem anúncios). Objetivo: criar hábito diário e oferecer uma alternativa leve e inclusiva em Português (BR).

## 2. Público-alvo

Jogadores casuais brasileiros (adultos e jovens) que buscam desafios de vocabulário rápidos (1–3 min/sessão), em desktop ou mobile.

## 3. Plataforma e tecnologia

- **Web no navegador** (HTML/CSS/JS; sem build step; hospedagem estática).
- **Sem backend no MVP**: daily word derivada de data; validação por **lista estática embarcada** de palavras PT-BR.
- **Online-only no MVP** (sem cache/offline).
- Progresso salvo localmente via `localStorage` (estado do daily em andamento, stats, streak).

## 4. Mecânica principal (configuração clássica)

- Palavra secreta de **5 letras**, **6 tentativas**.
- Apenas palavras válidas do PT-BR podem ser submetidas (validação pela lista estática).
- Feedback por tentativa:
  - 🟩 verde: letra certa no lugar certo;
  - 🟨 amarelo: letra na palavra, lugar errado;
  - ⬛ cinza: letra não está na palavra.
- Regra de letras repetidas idêntica ao Wordle original (duas passadas).
- **Daily único**: palavra determinada por data (seed determinístico), igual para todos.
- **Sem modo ilimitado no MVP.**

## 5. Funcionalidades por prioridade (MoSCoW)

### Must (MVP)

1. Tabuleiro 5×6 com feedback colorido e animações (flip/shake).
2. Teclado virtual on-screen + suporte a teclado físico.
3. Validação de palavras (lista estática PT-BR) com aviso "palavra não encontrada".
4. Desafio diário único (palavra por data) + contagem regressiva até o próximo.
5. Streak diário (dias consecutivos jogando; reinicia ao perder um dia).
6. Estatísticas básicas: partidas jogadas, taxa de vitória, distribuição de tentativas, current/best streak.
7. Persistência local (`localStorage`).
8. Tema claro/escuro (persistido).
9. **Modo daltônico** (padrões/ícones além de cores).
10. Share (copiar grade de emojis para clipboard).
11. Responsividade (mobile e desktop).

### Should (se sobrar esforço)

- Definição/significado da palavra ao final da partida (educativo).
- Página "Como jogar" / tutorial.
- Estatísticas isoladas por modo (preparação para futuros modos).

### Could (pós-MVP, alto valor)

- Modo ilimitado ("redemption arc").
- Archive de puzzles anteriores.
- Multi-board (Double/Quad).
- Pacotes temáticos de palavras.
- Tamanho de palavra selecionável (4/6 letras, 8 tentativas).
- "Send a game" (enviar puzzle customizado a amigo).
- Rush mode.
- Leaderboards.
- Mais idiomas (EN, ES).
- Modo offline (Service Worker + cache).

### Won't (fora do escopo inicial)

- Monetização/ads e compras in-app (decisão de jogo gratuito).
- Backend/servidor e contas de usuário.
- Multiplayer em tempo real.

## 6. UX/Acessibilidade (essenciais no MVP)

- Teclado virtual com status "melhor pista por letra" (evitar letras descartadas).
- Áreas de toque ≥ 44px.
- Validação visual (shake em palpite inválido, flip animado).
- Feedback "palavra não encontrada na lista" via toast.
- Suporte a leitores de tela onde razoável (`aria-label`).
- Dark + Light theme persistidos.
- Modo daltônico com padrões (bordas/ícones) além de cor.
- Teclado virtual não deve cobrir o tabuleiro no mobile.

## 7. Métricas de sucesso (casual)

- DAU/WAU e taxa de retorno D1/D7/D30.
- % de usuários que completam o daily.
- Taxa de vitória e distribuição de tentativas (meta: 70–80% de vitória sem hints).
- Streaks médios (proxy de retenção D7).
- Compartilhamentos por daily (coeficiente viral).
- Tempo médio de sessão (meta 2–5 min).

## 8. Riscos e atenções

- Lista estática pode ficar grande; filtrar termos ofensivos e slang obscuro (palavras raras frustram, ex.: "TOMOZ").
- Palavra diária deve evitar duplicatas consecutivas e palavras muito raras.
- Online-only: UX deve degradar bem se a fonte de data falhar (mensagem clara).
- Sem backend = sem sincronização entre dispositivos (aceitável para MVP).
- Responsividade: teclado virtual não pode cobrir o tabuleiro no mobile.

## 9. Pesquisa de mercado (resumo)

- **Dedução estilo Wordle** (5 letras, 6 tentativas) é o padrão reconhecido; clones BR como **Termo** dominam; evitar conflito de nome.
- Outros tipos relevantes: Forca (Hangman), charadas com imagens (4 Fotos 1 Palavra), semântica (Contexto), híbridos (Wordy).
- Padrões de engajamento vencedores: daily único, modo ilimitado, streaks diários, estatísticas, share spoiler-free, archive, multi-board, rush mode.
- Monetização predominante: freemium com ads removíveis. **Anúncios frequentes/abruptos são a queixa #1 em reviews** — importante manter a decisão de "totalmente gratuito" ou ser muito criterioso.
- Acessibilidade elogiada: modo daltônico, dark/light, teclado físico+virtual, VoiceOver, offline, múltiplos idiomas.

## 10. Sugestões de nome (PT-BR)

Ideias alinhadas com o produto (verificar disponibilidade de domínio/handle):

- Letra a Letra
- Cinco Letras
- Palavra do Dia
- Adivinha
- Palavraria
- Palavra Mágica
- Verbo
- Pista
- Descubra
- Palavra5 / 5Palavras

Recomendação: nome curto, memorável, sem conflito (evitar "Termo", muito associado ao clone BR). Se quiser, posso gerar variações por estilo (técnico, poético, gaming).

## 11. Decisões tomadas

| Decisão            | Valor                                               |
| ------------------ | --------------------------------------------------- |
| Mecânica           | Wordle-style (dedução colorida)                     |
| Configuração       | 5 letras, 6 tentativas                               |
| Plataforma         | Web navegador                                       |
| Idioma             | Português (BR)                                      |
| Monetização        | Totalmente gratuito (sem ads/compras)               |
| Escopo MVP         | Mínimo                                              |
| Daily único        | Sim                                                 |
| Streaks diários    | Sim                                                 |
| Modo ilimitado     | Não no MVP                                          |
| Acessibilidade     | Essenciais (dark/light, daltônico, teclado físico+virtual) |
| Extras MVP         | Teclado virtual on-screen                           |
| Offline            | Apenas online no MVP                                |
| Validação          | Lista estática embarcada                            |
| Contas/login       | Não (localStorage)                                 |

## 12. Próximos passos

1. Aprovar/ajustar este PRD (v0.1 → v1.0).
2. Escolher nome definitivo.
3. Montar lista estática de palavras PT-BR (filtrar ofensivas e raras).
4. Implementar diária determinística por data + persistência local.
5. Implementar acessibilidade essencial.
6. Testes de usabilidade em mobile (teclado não cobrir tabuleiro).
7. Publicar como site estático.
