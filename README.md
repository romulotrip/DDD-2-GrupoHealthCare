# 📚 Design Estratégico do Projeto

## 📌 Aula 1: Introdução ao Domain-Driven Design (DDD)

### **1️⃣ Revisão da Aula**
- O que é **Domain-Driven Design (DDD)**?
- Diferença entre **Complexidade Essencial vs. Complexidade Acidental**.
- **Subdomínios**: Core Domain, Supporting Subdomains e Generic Subdomains.
- **Bounded Contexts**: Separando conceitos e linguagens dentro do domínio.

### **2️⃣ Identificação dos Subdomínios**
| **Subdomínio** | **Descrição** | **Tipo** |
| :--- | :--- | :--- |
| Gamificação e Jornada | Gerencia os desafios, o progresso (pontuação, ranking, conquistas) e o fluxo da jornada de bem-estar do colaborador. É o diferencial competitivo do negócio. | Core Domain |
| Gestão de Conteúdo/Missões | Criação, gestão e fornecimento dos materiais educativos, missões e micro-intervenções que alimentam os desafios de bem-estar. | Supporting |
| Comunidade e Feed | Gerencia a interação social entre os colaboradores (feed de notícias, publicações de conquistas, comentários e curtidas). | Supporting |
| Cadastro de Colaboradores/Empresas | Gerencia o ciclo de vida das contas corporativas e os perfis detalhados dos colaboradores. | Supporting |
| Análise de Impacto/Dashboards | Processa os dados de engajamento e saúde para gerar relatórios e KPIs consolidados para os gestores da empresa. | Supporting |
| Autenticação e Autorização | Gerencia o login, a segurança de senhas e os níveis de permissão dos diferentes tipos de usuários. | Generic |
| Pagamentos (B2B) | Processa a cobrança e gestão de faturas das empresas clientes (B2B) pela utilização da plataforma. | Generic 

---

## 📌 Aula 2: Mapeamento de Contextos (Context Mapping)

### **1️⃣ Objetivo da Aula**
Nesta aula, vamos:
✅ Explorar como **Bounded Contexts** se relacionam entre si.  
✅ Aplicar **Context Mapping** para visualizar dependências entre contextos.  
✅ Criar um **diagrama de Context Mapping** para um projeto.  

---

### **2️⃣ Atividade Prática: Context Mapping no Projeto**

📌 **Objetivo:**  
Identifique os **Bounded Contexts** do projeto e criar um **Context Map**, definindo as relações entre eles.

📌 **Instruções:**  
1️⃣ **Escolha um projeto** (real ou fictício). Ou utilize o seu projeto da aula 1. Pode ser um e-commerce, um sistema de saúde, um banco digital. 
2️⃣ **Liste os Bounded Contexts** que fazem parte do sistema.  
3️⃣ **Defina os relacionamentos** entre os contextos usando os padrões do Context Mapping (**Customer-Supplier, Shared Kernel, Anticorruption Layer, etc.**).  
4️⃣ **Crie um diagrama** representando o Context Map.  
5️⃣ **Justifique suas escolhas** (por que cada relacionamento foi modelado dessa forma?).  


| **Origem**               | **Destino**              | **Tipo de Relacionamento**       | **Explicação** |
|--------------------------|-------------------------|--------------------------------|---------------|
| Contexto de Identidade   | Contexto de Jornada do Colaborador  | **Anticorruption Layer (ACL)**          |Para proteger o Contexto da Jornada, uma camada traduz os dados do Acesso, passando apenas informações relevantes como o status "ativo" do usuário e a qual empresa ele pertence, evitando expor o modelo interno de Acesso. |
| Contexto de Conteúdo     | Contexto de Jornada do Colaborador  | **Customer-Supplier (Cliente-Fornecedor)**              | O Contexto de Jornada (cliente) depende diretamente do Contexto de Conteúdo (fornecedor). A jornada só se torna dinâmica e completa com os materiais fornecidos, ficando incompleta sem eles. |
| Contexto de Jornada do Colaborador  | Contexto de Comunidade   | **Customer-Supplier**                 | O Contexto de Comunidade (cliente) depende e consome as informações geradas pelo Contexto de Jornada (fornecedor), como as conquistas e os desafios que foram completados pelos usuários, para poder funcionar. |
| Contexto de Jornada do Colaborador   | Contexto de Análise Corporativa   | **Anticorruption Layer (ACL)** | O Contexto de Análise atua como um adaptador, utilizando uma camada de tradução (ACL) para converter a alta gama de dados brutos da Jornada em KPIs e resultados consolidados para os dashboards das empresas. |

📌 **Formato de Entrega:**  
- O trabalho pode ser entregue em **Markdown (.md), PDF ou apresentação (PPT)**.  
- O diagrama pode ser anexado como **imagem** ou **link para uma ferramenta online**.  
- Entrega via **repositório Git** ou outra plataforma definida pelo professor.  

DIAGRAMA > https://miro.com/app/board/uXjVJDEnjn4=/


📌 **Ferramentas para Criar o Diagrama:**  
- [Miro](https://miro.com/)  
- [Lucidchart](https://www.lucidchart.com/)  
- [Figma](https://www.figma.com/)  

## 📌 Aula 3: Próximos Passos  
Na próxima aula, vamos explorar **Design Tático**, abordando:  
🔹 **Entidades vs. Value Objects** – Como diferenciar e modelar corretamente.  
🔹 **Agregados** – Como definir o agregado raiz e garantir consistência.  
🔹 **Repositórios** – Como separar persistência da lógica de domínio.  

📌 **Prepare-se!** Tente aplicar **Context Mapping** no seu projeto antes da próxima aula.  

---

**📢 Bom trabalho! Nos vemos na próxima aula! 🚀**  
