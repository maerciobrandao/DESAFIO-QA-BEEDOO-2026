# DESAFIO-QA-BEEDOO-2026
Repositório dedicado ao Desafio Técnico para Analista de Qualidade Jr (QA) na Beedoo

## 1. Análise Inicial da Aplicação.
**Qual o objetivo da aplicação?**

  A aplicação tem como objetivo ser um sistema simples de gestão de conteúdo, funcionando como um CRUD (Create, Read, Update, Delete) focado na entidade "Cursos", permitindo que o usuário cadastre novos treinamentos e visualize o catálogo existente.

**Quais os principais fluxos disponíveis?**

Através da navegação na barra de menu, identifiquei dois fluxos principais:
1. Cadastro de novos cursos (inserção de dados).
2. Listagem de cursos (leitura e exibição dos dados cadastrados).

**Quais pontos do sistema considero mais críticos para teste?**
- Integração Front-end vs Back-end (Armazenamento): Garantir que um curso cadastrado na tela de formulário seja persistido corretamente e retornado na tela de listagem.
- Validação de Campos (Formulário): Como é uma tela de entrada de dados, o ponto mais crítico é garantir que o sistema valide corretamente as informações, impedindo o cadastro de cursos sem nome, dados inválidos ou caracteres maliciosos que possam quebrar a listagem.

## 2. Decisões tomadas para criação dos testes
Durante a exploração do sistema, optei por focar na Análise de Valor Limite e em Testes Negativos (Caminhos de Exceção) aplicados ao formulário de cadastro. A decisão de priorizar essas técnicas baseou-se no fato de que o formulário é a principal porta de entrada de dados da aplicação.

**Concentrei os cenários de teste nos seguintes pontos:**
* Comportamento de campos numéricos (aceitação de valores negativos ou nulos).
* Máscaras e validações de formatação (limite de dígitos em datas e obrigatoriedade de formato URL em links).
* Testes de estresse de caracteres em campos de texto livre (Nome, Descrição e Instrutor) para prever quebras de layout na tela de listagem.
* Validação das regras de negócio dinâmicas (exibição do campo "Endereço" vs "Link de Inscrição" conforme o tipo de curso).

## 3. Explicação do raciocínio durante a análise
O meu raciocínio partiu da premissa de que dados não validados no Front-end geram lixo no Back-end e quebram a visualização do usuário.

Ao realizar os testes exploratórios, notei que a aplicação confiava excessivamente na entrada do usuário sem impor restrições sistêmicas. O cadastro de um curso com "-7 vagas" ou com o ano "266666" é um erro crítico de regra de negócio que corrompe a confiabilidade da listagem. Portanto, a estratégia de documentação focou em mapear a ausência dessas validações essenciais para garantir a robustez futura do software.

## 4. Sugestões de Melhoria (UX/UI e Produto)
Além dos bugs relatados na planilha de execução, identifiquei oportunidades de melhoria focadas na experiência do usuário e padronização dos dados:

* Upload de Imagem: Substituir (ou adicionar como alternativa) o campo "URL da imagem de capa" por um botão de Upload local, facilitando a vida do usuário que não tem a imagem hospedada na web.

* Padronização de Texto (Uppercase/Capitalize): Implementar uma máscara no Front-end ou tratamento no Back-end para que o "Nome do Curso" e o "Nome do Instrutor" sejam sempre salvos com a primeira letra maiúscula, mantendo o padrão visual da listagem limpo e organizado.

* Sinalização de Obrigatoriedade: Adicionar o asterisco (*) visual indicando quais campos são obrigatórios na tela de cadastro, orientando o usuário antes da tentativa de envio.

## 5. Links de Entrega (Planilha e Evidências)
Todo o mapeamento técnico, detalhamento dos casos de teste (escritos em Gherkin) e o relatório de bugs com as respectivas severidades foram documentados e estão disponíveis nos links abaixo:

📊 [Clique aqui para acessar a Planilha de Casos de Teste e Bugs](https://docs.google.com/spreadsheets/d/1Xw58kZt-w4lFlyd0YOFKwso17S0dcakAYrVp8feBeWE/edit?usp=sharing)

📁 [Clique aqui para acessar a Pasta de Evidências (Prints)](https://drive.google.com/drive/folders/1IaYLOrb0pYOmZqadfUSlWUYDRyvzwe-t?usp=sharing)
