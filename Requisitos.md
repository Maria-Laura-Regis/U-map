
## 1.📋 Introdução ao Contexto do Projeto

**🎯 Objetivo**: Criar uma plataforma digital colaborativa onde:
- Estudantes possam se localizar
- Alunos novos possam conhacer o campus com facilidade
- Membros da faculdade possam divulgar eventos futuros em um Mural Virtual

**Desafios Técnicos Envolvidos**:
- Processar dados geográficos com precisão
- Garantir que a interface seja usável por estudantes da Universidade 

## 2. Fundamentos sobre Requisitos de Software

### O que é o Levantamento de Requisitos?
- Condição necessária para a obtenção de certo objetivo ou para preenchimento de certo fim.
- É o ato de definir as funções e restrições que o produto a ser desenvolvido deve possuir.



**Requisitos Funcionais**: 
- Diretamente ligado com as funcionalidades do software, como o sistema deve reagir a entradas espeíficas, aquilo que o cliente "pede".

**Requisitos Não Funcionais**:
-Não dizem respeito diretamente as funcionalidades do software, mas deve estar incluso naquele produto, como segurança, confiabilidade e velocidade de resposta.


## 3.🔍Levantamento dos Requisitos

### ✅ 3. Requisitos Funcionais (RF)

| Código | Requisito Funcional                    | Descrição                                                                 |
|--------|----------------------------------------|---------------------------------------------------------------------------|
| RF01   | Cadastro de usuário (opcional)                   | Permitir registro com nome, e-mail e senha.                               |
| RF02   | Login/Logout                           | Autenticar usuários e encerrar sessão.                                    |
| RF03   | Recuperação de senha                   | Enviar e-mail para redefinir senha.                                       |
| RF04   | Cadastro de local acessível            | Inserir nome, tipo, endereço, acessibilidades, fotos e descrição.         |
| RF05   | Edição de local                        | Permitir que usuários editem informações que cadastraram.                 |
| RF06   | Visualização em mapa                   | Exibir locais cadastrados em mapa interativo.                             |
| RF08   | Busca por região ou tipo de atividade  | Pesquisa por sala, prédio, etc                                            |
| RF09   | Avaliação de acessibilidade            | Usuários podem avaliar e comentar os locais.                              |
| RF10   | Geolocalização                         | Marcar local automaticamente ou via mapa.                                 |
| RF11   | Upload de fotos    (apenas usuário cadastrado)                    | Enviar imagens do local e suas condições.                                 |
| RF12   | Cadastro de eventos acessíveis         | Organizações podem divulgar eventos temporários.                          |
| RF13   | Moderação de conteúdo                  | Aprovação, rejeição ou exclusão de cadastros.                             |
| RF14   | Notificações                           | Enviar alertas sobre comentários ou novos locais.                         |
| RF15   | Interface acessível                    | Plataforma compatível com tecnologias assistivas.                         |

### 🚫 4. Requisitos Não Funcionais (RNF)

| Código | Requisito Não Funcional    | Descrição                                                                |
|--------|----------------------------|---------------------------------------------------------------------------|
| RNF01  | Responsividade             | Interface adaptável a dispositivos móveis.                                |
| RNF02  | Acessibilidade digital     | Compatível com leitores de tela, teclados, contraste adequado, etc.       |
| RNF03  | Desempenho                 | Página deve carregar em até 3 segundos.                                   |
| RNF04  | Escalabilidade             | Suportar aumento de usuários e volume de dados sem perda de desempenho.   |
| RNF05  | Segurança                  | Criptografia de senhas, proteção contra injeção de dados e CSRF.          |
| RNF06  | Código Aberto              | Repositório público e documentado (ex: GitHub).                           |
| RNF07  | Backup de dados            | Manter cópias regulares do banco de dados para recuperação.               |

### Serverless (Sem Servidor)
**Conceito**:
- Executa código apenas quando necessário
- Gerenciado por provedores cloud (AWS, Google)

**Caso de Uso Ideal**:
- Funções esporádicas como envio de e-mails

**Economia**:
- Paga-se apenas pelo tempo de execução real

### Alternativas Stack Backend

## 4. Banco de Dados para Dados Geoespaciais

### PostgreSQL com PostGIS
**O que é**:
- Banco relacional com extensão para dados geográficos
- Permite consultas por proximidade geográfica

**Recursos Chave**:
ST_DWithin() -- Calcula distâncias entre coordenadas

## 4. Alternativas Consideradas

### Firebase Firestore
- **Gerenciamento**: Plataforma do Google (Cloud)
- **Melhor Caso de Uso**: 
  - Aplicações simples e rápidas
  - Prototipagem
- **Considerações**:
  - Custo escala com uso
  - Limitações em consultas geoespaciais

---

## 5. Serviços de Mapeamento

### Mapbox GL JS
**Características Principais**:
- Biblioteca JavaScript para mapas interativos
- Tecnologia de renderização vetorial
  - Carregamento rápido
  - Alta customização

**Recursos de Acessibilidade**:
- Navegação completa via teclado
- Compatibilidade com leitores de tela
- Temas de alto contraste para visibilidade

**Exemplo de Implementação**:
```javascript
map.addLayer({
  id: 'accessible-places',
  type: 'circle',
  paint: {
    'circle-color': '#00AA00',
    'circle-radius': 8
  }
});
```
## . Comparativo de Stack Backend

### Node.js vs. Django vs. Flask

| Critério         | Node.js + Express         | Django (Python)           | Flask (Python)            |
|------------------|---------------------------|---------------------------|---------------------------|
| **Velocidade**   | Rápido (motor V8)         | Moderado (Python)         | Leve (microframework)     |
| **Ecossistema**  | Ideal para APIs REST/GraphQL | ORM poderoso (PostgreSQL) | Flexível (menos "baterias incluídas") |
| **Integração com Mapas** | SDKs nativos (Mapbox/Google Maps) | Geodjango (PostGIS nativo) | Requer bibliotecas externas (GeoAlchemy) |
| **Autenticação** | JWT/Firebase Auth simplificada | Sistema de usuários built-in | Implementação manual necessária (Flask-JWT) |



**Node.js + Express**:
- Prioridade em velocidade de desenvolvimento
- Stack JavaScript full (front + back)
- Integração com serviços modernos (Firebase, Mapbox)


## 6. Autenticação de Usuários

### Firebase Authentication

#### Funcionalidades
- **Múltiplos métodos de login**:
  - Redes sociais (Google, Facebook)
  - E-mail/senha
  - Números de telefone
- **SDKs disponíveis** para:
  - Web
  - Mobile (Android/iOS)
  - Backend

#### Segurança
- **Proteções automáticas**:
  - Contra ataques de força bruta
  - Tentativas de phishing
- **Criptografia**:
  - Ponta a ponta para dados sensíveis
  - Tokens JWT assinados

#### Fluxo Básico
1. Usuário clica em "Entrar com Google"
2. Firebase gerencia processo OAuth 2.0
3. Sistema recebe token JWT seguro
4. Token é validado em cada requisição

## 7. Justificativa da Stack Escolhida

### Cenários de Uso Demonstrativos

#### Evento Comunitário Massivo
- **500+ usuários simultâneos**:
  - Microsserviço de mapas escala horizontalmente
  - Funções serverless para autenticação
  - Balanceamento de carga automático

#### Uso Diário
- **Performance**:
  - Consultas geoespaciais em <500ms
  - Cache de resultados frequentes
- **Acessibilidade**:
  - Interface responsiva
  - Suporte a tecnologias assistivas

### Vantagens Estratégicas
| Benefício         | Descrição                                  |
|-------------------|--------------------------------------------|
| **Custo**         | Free tiers suficientes para MVP            |
| **Escalabilidade**| Arquitetura modular para crescimento       |
| **Manutenção**    | Componentes independentes                  |


### Recursos Educativos
- [Documentação Oficial PostGIS](https://postgis.net/docs/)
- [Guia de Acessibilidade Mapbox](https://docs.mapbox.com/help/tutorials/accessible-maps/)
- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
