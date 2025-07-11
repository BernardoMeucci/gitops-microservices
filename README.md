# 🚀 Projeto: GitOps na Prática com Kubernetes e ArgoCD

![Status](https://img.shields.io/badge/status-concluído-green)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?logo=argo&logoColor=white)
![GitOps](https://img.shields.io/badge/GitOps-Declarativo-blueviolet)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)

Este repositório contém os manifestos Kubernetes para a aplicação de microserviços **Online Boutique**, implantada e gerenciada através de uma esteira de GitOps.

O projeto foi desenvolvido como parte do **Programa de Bolsas - DevSecOps da Compass UOL** e demonstra na prática como as empresas modernas operam em ambientes cloud-native para realizar entregas rápidas, seguras e escaláveis.

---

## 🎯 Objetivo do Projeto

Executar o conjunto de microserviços **Online Boutique** em um cluster Kubernetes local, controlado por práticas de GitOps com **ArgoCD**, a partir deste repositório público no GitHub.

---

## 🛠️ Tecnologias e Conceitos

| Tecnologia / Conceito | Propósito no Projeto |
| :-------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------- |
| **Kubernetes** | Plataforma de orquestração de contêineres que serviu como base para rodar a aplicação em um ambiente local via **Docker Desktop**.                  |
| **GitOps** | Metodologia de operações onde o repositório Git é a **fonte única da verdade**, garantindo um processo de deploy auditável e previsível.        |
| **ArgoCD** | Ferramenta de GitOps que atua como um operador no cluster, garantindo que o estado da aplicação seja um reflexo fiel do que está definido no Git. |
| **Microserviços** | Arquitetura da aplicação de exemplo ("Online Boutique"), dividida em múltiplos serviços independentes e conteinerizados.                       |
| **Docker** | Utilizado como o motor de contêineres que executa as imagens da aplicação dentro dos pods do Kubernetes.                                       |

---

## ✅ Resumo da Execução

<details>
<summary><strong>Clique para ver o passo a passo da execução do projeto</strong></summary>

1.  **Configuração do Ambiente:**
    - Um cluster Kubernetes foi inicializado localmente utilizando o **Docker Desktop**.
    - O `kubectl` foi configurado para se comunicar com o cluster.

2.  **Criação da Fonte da Verdade:**
    - Este repositório Git foi criado para hospedar os manifestos da aplicação.
    - O manifesto da aplicação "Online Boutique" foi adicionado à pasta `k8s/`.

3.  **Instalação do ArgoCD:**
    - O ArgoCD foi instalado no cluster através do comando `kubectl apply`.
    - O acesso à sua interface gráfica foi liberado localmente via `port-forward`.

4.  **Deploy Automatizado via GitOps:**
    - Um "App" foi criado no ArgoCD, conectando este repositório ao cluster local.
    - Ao estabelecer a conexão, o ArgoCD iniciou a sincronização automática, lendo o manifesto `online-boutique.yaml` e comandando o Kubernetes para criar todos os microserviços da aplicação.

5.  **Escalabilidade (Etapa Opcional):**
    - O `Deployment` do `frontend` foi customizado e escalado para **3 réplicas**.
    - A mudança foi feita no arquivo YAML, enviada ao Git, e o ArgoCD automaticamente ajustou o número de pods no cluster.

</details>

---

## 🖼️ Telas do Projeto

| ArgoCD: Tela de Login | ArgoCD: Aplicação Sincronizada |
| :---: | :---: |
| [cite_start]![Tela de Login do ArgoCD](docs/images/argocd-login.jpg) [cite: 3] | ![Aplicação Sincronizada no ArgoCD](docs/images/argocd-app-synced.png) |
| **ArgoCD: Visão das 3 Réplicas** | **Aplicação Online Boutique em Execução** |
| [cite_start]![Réplicas do Frontend no ArgoCD](docs/images/argocd-replicas-view.png) [cite: 2] | [cite_start]![Frontend da Loja Online](docs/images/online-boutique-frontend.jpg) [cite: 1] |

---

## 🖥️ Como Visualizar o Resultado

Com o ambiente em execução, a aplicação pode ser acessada da seguinte forma:

1.  **Ativar o túnel de acesso para a aplicação:**
    ```bash
    kubectl port-forward svc/frontend-external -n default 8081:80
    ```

2.  **Acessar a loja online no navegador:**
    - URL: `http://localhost:8081`