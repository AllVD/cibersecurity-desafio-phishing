# Laboratório de Engenharia Social - Captura de Credenciais com SET

## 🎯 Objetivo do Exercício
Este laboratório prático foi desenvolvido como parte do treinamento de Cybersecurity na plataforma DIO.
O objetivo principal foi demonstrar os mecanismos de funcionamento de um ataque de Engenharia Social (Phishing) 
utilizando o **Social-Engineer Toolkit (SET)** no Kali Linux para clonagem de interface e interceptação de credenciais em ambiente controlado.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Sistema Operacional Atacante:** Kali Linux v2026
* **Sistema Operacional Alvo:** Windows 11
* **Ferramenta de Ataque:** Social-Engineer Toolkit (SEToolkit) v8.5+
* **Módulo Utilizado:** `Credential Harvester Attack Method` (via Custom Import)
* **Servidor Web Integrado:** Python/Apache local na porta 80

## 🚀 Passo a Passo da Execução

### 1. Preparação do Template HTML
* Captura da estrutura da página de login utilizando técnicas de espelhamento e organização de assets locais.
* Modificação manual da tag "<form>" no arquivo "index.html" para habilitar a interceptação correta dos parâmetros de entrada pelo backend do SET:
    ```html
    <form id="login_form" method="POST" action="index.php">
    ```
### 2. Configuração do Social-Engineer Toolkit
O utilitário foi iniciado via terminal como "root" usando o comando "sudo su" seguindo a árvore de opções:
1.  **1)** Social-Engineering Attacks
2.  **2)** Website Attack Vectors
3.  **3)** Credential Harvester Attack Method
4.  **3)** Custom Import

### 3. Validação do Ataque e Captura
A partir da máquina alvo (Windows), o endereço de IP do servidor Kali foi acessado. Ao submeter os dados de teste no formulário, 
os parâmetros foram capturados em tempo claro pelo console do SET:

* **Identificador de Sucesso:** `[+] WE GOT A HIT! Printing the output:`
* **Campos Interceptados:** `POSSIBLE USERNAME FIELD FOUND` e `POSSIBLE PASSWORD FIELD FOUND`

## 🛡️ Desafios Técnicos e Diagnósticos do laborátorio

Durante a execução do laboratório, foram identificados e analisados os comportamentos de segurança das aplicações web modernas
que impedem a replicação visual idêntica por ferramentas legadas de automação (como o Site Cloner nativo do SET).

### 🔍 Análise de Erros 404 e Bloqueios Visuais
1.  **Políticas de CORS e CSP (Content Security Policy):** Os navegadores modernos (Chrome/Edge/Firefox) bloqueiam o carregamento de folhas de estilo (CSS) e scripts dinâmicos quando a origem da requisição não corresponde aos servidores autenticados da aplicação real, resultando em renderização de texto puro ou layout fragmentado.
2.  **Arquitetura Dinâmica:** Plataformas modernas utilizam Shadow DOM e geração de classes em tempo real, tornando a clonagem estática obsoleta sem o uso de estruturas de **Proxy Reverso** (como *Evilginx* ou *GoPhish*), que são os padrões de mercado atuais para operações avançadas desse tipo.

## 📊 Resultados e Conclusão
O laboratório atingiu o seu objetivo principal com sucesso, uma vez que a camada de aplicação e o script de backend do SET conseguiram interceptar e registrar com precisão os dados trafegados, validando a lógica de um ataque de roubo de credenciais em auditorias de segurança.

## 🖼️ Captura de Tela - Interceptação de Credenciais bem-sucedida (SET)
Abaixo está a comprovação visual do recebimento dos pacotes de dados e parâmetros de formulário diretamente
no terminal do Kali Linux usado para o ataque:

<img width="1599" height="899" alt="kali_linux_setoolkit_print" src="https://github.com/user-attachments/assets/9d4c15ec-1b6f-43a4-9a3b-2866fddcd27b" />

Nota: Este projeto possui finalidade estritamente didática e educacional, realizada em ambiente de rede isolado e controlado.
