# 🚀 Desafio de Infraestrutura Automatizada com AWS CloudFormation

Este projeto documenta a implementação de uma infraestrutura automatizada na AWS usando **CloudFormation**. O objetivo principal foi aplicar conceitos de Infraestrutura como Código (**IaC**) e criar um material de estudo estruturado para futuras implementações, servindo como um repositório de **insights e anotações** adquiridos na prática.

---

## 🎯 Objetivos de Aprendizagem

1.  **Aplicação Prática:** Desenvolver, validar e orquestrar um *template* CloudFormation para provisionar recursos.
2.  **IaC:** Automatizar a criação de componentes de rede e computação (VPC, EC2, Security Groups, etc.).
3.  **Documentação:** Criar um material de apoio estruturado, focado nos **processos técnicos e aprendizados**.

---

## 🏗️ 1. Arquitetura Implementada

O template do CloudFormation (`templates/<nome_do_template.yaml>`) foi utilizado para construir uma arquitetura que incluiu os seguintes recursos AWS:

| Recurso | Função Principal |
| :--- | :--- |
| **AWS::EC2::VPC** | Base de rede isolada. |
| **AWS::EC2::Subnet** | <Descreva quantas e quais tipos de subnets você criou. Ex: 1 Pública.> |
| **AWS::EC2::SecurityGroup** | Controle de tráfego, permitindo portas <Ex: 80 e 22>. |
| **AWS::EC2::Instance** | Instância <Ex: T2.Micro com Amazon Linux 2> configurada como <Ex: Web Server>. |

---

## ✨ 2. Anotações e Insights Adquiridos

Esta seção detalha os principais aprendizados, desafios e *insights* adquiridos durante o desenvolvimento e implementação da *stack*, focando nas funcionalidades do CloudFormation.

### A. O Valor da Automação e Consistência

| Conceito | Insight Adquirido |
| :--- | :--- |
| **Infraestrutura como Código (IaC)** | O principal ganho é a **reprodutibilidade e consistência**. A infraestrutura pode ser recriada exatamente igual em qualquer ambiente. A codificação da infraestrutura facilita a revisão por pares (code review) e a segurança. |
| **Gerenciamento de Estado** | O CloudFormation gerencia o estado da *stack*, o que me permite realizar *updates* e *rollbacks* de forma segura. A capacidade de **reverter automaticamente** em caso de falha (`ROLLBACK`) é um recurso crucial. |
| **Clean-up** | A remoção de toda a infraestrutura com um único comando (`Delete Stack`) me mostrou a eficiência em gerenciar ambientes de teste ou desenvolvimento, garantindo que não restem recursos órfãos (e custos desnecessários). |

### B. Técnicas Essenciais de Template (YAML)

| Seção/Função | Exemplo e Principal Aprendizado |
| :--- | :--- |
| **`Parameters`** | A chave para a **reutilização**. Utilize Parameters para campos que mudam entre ambientes (como `InstanceType` ou `KeyName`). Aprendi a usar a propriedade `AllowedValues` para controle de input. |
| **`Resources`** | Aprendi que a ordem de declaração não importa. O CloudFormation infere as dependências automaticamente (ex: a Subnet depende da VPC). Usei a propriedade `DependsOn` apenas para dependências que não são óbvias (ex: <Cite um exemplo específico, se tiver usado>). |
| **Função `!Sub` (Substituição)** | Foi essencial para a criação dinâmica de nomes e tags. <Cite um exemplo de uso. Ex: `Name: !Sub "${AWS::StackName}-Web-SG"`> |
| **Função `!Ref` (Referência)** | A função mais usada. É a cola que conecta os recursos, garantindo que a ID da VPC recém-criada seja passada corretamente para as Subnets e Security Groups. |
| **Seção `Outputs`** | É o painel de controle da Stack. Usei-a para exibir informações importantes, como o **Nome DNS Público** ou o **ID da Instância**, facilitando o acesso após o *deploy*. |

---

## 🔗 Recursos Úteis

* **Documentação Oficial da AWS - CloudFormation:** [https://docs.aws.amazon.com/cloudformation/](https://docs.aws.amazon.com/cloudformation/)
