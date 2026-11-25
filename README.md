# Fale Conosco — OutSystems Reactive Web

Projeto prático de aplicação web **Fale Conosco** desenvolvido no **OutSystems Service Studio**, unindo arquitetura visual, validação lógica, modelagem de dados e boas práticas de responsabilidade digital.

## 1. O Contexto
Antes de abrir a IDE, o projeto foi planejado para evitar retrabalho e tomar decisões conscientes desde o início:
- **Planejamento prévio:** Desenhar a estrutura antes de programar reduziu erros de fluxo e de tipagem durante a implementação.
- **Uso responsável de dados (coleta mínima):** O formulário solicita apenas o essencial (`Nome`, `E-mail` e `Mensagem`), evitando pedir dados sensíveis ou desnecessários (como CPF ou endereço) para um simples contato.

## 2. A Arquitetura
A solução foi estruturada em três camadas integradas, desenhadas previamente no **Excalidraw**:
- **Interface (Tela `FaleConosco`):** Campos rotulados com clareza para orientar o usuário e apoiar a acessibilidade, além de feedback visual após o envio.
- **Lógica (Ação `EnviarMensagemOnClick`):** Valida se os campos obrigatórios estão preenchidos (`Nome <> "" and Email <> "" and Mensagem <> ""`), preenche o registro `NovoContato`, limpa os campos e exibe mensagens de alerta ou confirmação.
- **Dados (Entidade `Contato`):** Armazena os registros com atributos tipados (`Nome`, `Email`, `Mensagem` como `Text`, `DataEnvio` como `DateTime` e `Lida` como `Boolean`).

![Arquitetura do Projeto](./arquitetura-fale-conosco.png)

## 3. A Implementação
- **Modelagem de Dados:** Criação da entidade `Contato` na aba *Data* e da variável local `NovoContato` do tipo `Contato` na tela.
- **Fluxo e Validação:** Uso de condicional `If`, preenchimento via `Assign` (`Variable` / `Value`), persistência via `CreateContato` (com `Source = NovoContato`, `CurrDateTime()` e `Lida = False`), limpeza dos campos e `Message` de feedback.
- **Acessibilidade e Qualidade:** Atenção a rótulos identificáveis (`Label`), clareza nas mensagens de erro/sucesso e testes de fluxo vazio vs. preenchido no navegador.
