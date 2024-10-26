# Nexus

A palavra **nexus** origina-se do _latim_, com o significado de vínculo ou laço, sendo utilizada para descrever algo que une, 
conecta ou integra diversas partes.

Esse nome captura de forma precisa a essência de um sistema versátil, capaz de realizar múltiplas funções e se conectar 
com qualquer plataforma. Seu papel é ser o ponto central de integração e interação entre diferentes sistemas e soluções,
de forma concisa e marcante, transmitindo a ideia de união, eficiência, simplicidade de uso e robustez em sua operação.
___
## 🚀 Visão Geral do Projeto
Este projeto envolve o desenvolvimento de uma aplicação web para gerenciamento de estoque. O sistema permitirá que os 
usuários gerenciem inventários, acompanhem níveis de estoque, gerem relatórios e controlem a movimentação de produtos 
em diferentes locais. A aplicação será construída com uma arquitetura modular, facilitando a manutenção e a escalabilidade futura.
___
## Tipos de Usuários
Antes de explicar cada módulo e como os usuários interagem entre si e com os módulos, é fundamental conhecer os diferentes
tipos de usuários.

Existem dois tipos de usuários: o time de suporte (super administradores) e os clientes. Com base nessa estrutura,
os usuários são organizados da seguinte forma:
- **Super Administradores:** possuem acesso total ao sistema e são responsáveis por oferecer suporte aos usuários,
  garantindo o uso pleno da plataforma;

[//]: # (- **Time de Suporte:** usuários  com o objetivo de atender o suporte quando solicitado pelo cliente no módulo de suporte;)
- **Clientes:** São os usuários que adquirem o sistema para atender a uma demanda interna da empresa. Eles são subdivididos
  em três categorias: proprietário, administrador e colaborador.

**Nota**:
- As permissões de acesso de cada tipo de usuário podem ser consultadas em seus respectivos subtópicos, no item
  `Módulo :: Permissões do Usuário`.
___
## Módulos
A seguir, serão apresentados todos os módulos da plataforma, com uma descrição detalhada de suas funcionalidades e como 
cada tipo de usuário pode interagir com eles.
- [Módulo de Gestão de Usuários](#módulo-de-gestão-de-usuários)
- [Módulo de Gestão de Estoque](#módulo-de-controle-de-estoque)

### Módulo de Gestão de Usuários

#### Funcionalidades

Este módulo é composto pelas seguintes funcionalidades:
- **Gestão do usuário:** cadastrar, editar, exibir e arquivar
- **Gestão dos dados de perfil**: editar e habilitar 2FA e visualizar dados de pagamento.


<details>
  <summary><strong> Cadastrar </strong></summary>

O sistema permitirá o cadastro de novos usuários da seguinte forma:
- Para **usuários do tipo proprietário** por meio de um formulário, coletando os principais dados para o primeiro acesso do cliente.
- Os demais usuários descritos em [Tipos de Usuários](#tipos-de-usuários) poderão ser cadastrados via plataforma normalmente através da tela de cadastro.

Após o cadastro, todos os usuários receberão um e-mail contendo um link para a criação de sua senha. O link enviado por
e-mail terá uma validade de 5 minutos, e ao acessá-lo, o usuário será redirecionado para uma página onde poderá definir
sua senha de acesso. Após acessar o sistema, o cliente poderá ativar a autenticação em dois fatores (2FA) para aumentar a segurança.

</details>

<details>
  <summary><strong> Exibir </strong></summary>

O sistema permitirá a edição de todos os usuários através do caminho: `menu > usuários`.
</details>

<details>
  <summary><strong> Editar </strong></summary>

O sistema permitirá a edição de todos os usuários através do caminho: `menu > usuários > selecionar
um usuário clicando no nome > tela de edição`.
</details>

<details>
  <summary><strong> Excluir e Arquivar </strong></summary>

Na própria tela de edição haverá a opção via botão para o usuário excluir e arquivar o usuário. As regras de permissão 
estão descritas no tópico `Gestão de Usuário :: Permissões do Usuário`.
</details>

<details>
  <summary><strong> Perfil </strong></summary>

O perfil para todo usuário poderá ser acessado através do caminho: `foto do perfil no canto superior direito > perfil`.
Todos os usuários poderão editar os do próprio perfil, alterar senha e habilitação 2FA.
</details>

<details>
  <summary><strong> Autenticação em Dois Fatores (2FA) </strong></summary>

Todo novo cadastro vem com 2FA desativado e para ativar basta o usuário clicar foto do `foto no canto superior direito >
perfil > habilitar 2FA`.

Uma vez ativado, o usuário será solicitado a autenticar o acesso com um segundo fator, que será um código numérico
enviado por e-mail. O usuário deverá inserir esse código em uma tela específica para completar o processo de login.
O código de autenticação será temporário, com validade limitada de 5 minutos. Caso o código expire, haverá uma
funcionalidade para reenvio do código ao e-mail cadastrado.
</details>


#### Permissões do Usuário
As permissões dos usuários leva em consideração as 2 funcionalidades descritas em [Gestão do Usuário :: Funcionalidades](#gestão-do-usuário--funcionalidades) 
e ocorrerá da seguinte forma:
- Super Administrador: Acesso total às funcionalidades do módulo e verá todos os usuários de todas as contas cadastradas.
- Proprietário: Terá a visão e poderá acessar as funcionalidades somente dos usuários relacionados a sua própria conta 
dos perfil Administrador e Colaborador, além do seu próprio perfil
- Administrador: Terá a visão e poderá acessar as funcionalidades somente dos usuários Colaboradores relacionados a sua 
própria conta, além do seu próprio perfil
- Colaborador: Não terá a visão no módulo dos usuários, mas poderá acessar as funcionalidades somente do seu próprio perfil.

**Nota:**
- A funcionalidade excluir e arquivar usuários não estará disponível para usuários do tipo Colaboradores.
- Caso o usuário possua mais de um armazem ou estoque, os usuário do tipo proprietário poderão alternar entre eles
  na tela de perfil.
- Usuários proprietários são criados apenas por Super Admin
- Usuários colaboradores não têm acesso ao módulo de usuários
- Após o cadastro de um novo usuário, será enviado um e-mail com um link para que ele possa criar sua senha e ativar o 
- acesso à plataforma

### Módulo de Controle de Estoque
#### Funcionalidades
Este módulo oferece várias funcionalidades para a gestão de produtos e materiais no sistema. Antes de detalhar cada uma 
delas, faremos uma breve apresentação para facilitar a compreensão. As principais funcionalidades incluem:
- Cadastro de novos produtos
- Controle de movimentação de produtos
- Visualização do estoque atual
- Alertas de estoque baixo
- Auditorias de estoque
- Organização por localização
- Transferência entre estoques

<details>
  <summary><strong> Cadastrar Produto </strong></summary>

O sistema permitirá o cadastro de novos produtos de forma simples e eficiente. Para adicionar um novo produto ao estoque,
o usuário deverá acessar o módulo de controle de estoque, preencher um formulário com os seguintes dados:
* Nome do produto
* Descrição do produto
* Código de identificação
* Categoria do produto
* Nome do fornecedor ou fornecedores associados
* Preço de custo e preço de venda

Após o preenchimento, o sistema salva automaticamente as informações e o novo produto estará disponível no inventário,
sendo possível monitorar suas movimentações e níveis de estoque.
</details>

<details>
  <summary><strong> Movimentação de Produtos  </strong></summary>
O sistema permite o controle das entradas e saídas dos produtos através de um formulário simples de movimentação. A cada 
movimentação registrada, o sistema atualiza os níveis de estoque automaticamente, facilitando o acompanhamento de produtos 
em tempo real.

As principais ações incluem:
* **Entrada de produtos:** Para registrar a chegada de novos produtos ao estoque.
* **Saída de produtos:** Para registrar a retirada ou venda de produtos do estoque.
</details>

<details>
  <summary><strong> Visualização e Auditoria </strong></summary>

A auditoria e a visualização do estoque são funcionalidades cruciais para garantir a precisão do inventário. O sistema
disponibiliza uma visão geral dos produtos em estoque, permitindo ao usuário:

* Visualizar o total de produtos disponíveis.
* Filtrar os produtos por categorias, fornecedores ou locais de armazenamento.
* Realizar auditorias periódicas, comparando o inventário físico com o registrado no sistema, identificando e corrigindo
* discrepâncias.
</details>

<details>
  <summary><strong> Organização e Transferência </strong></summary>

O módulo de controle de estoque permite que os produtos sejam organizados em diferentes localizações, como armazéns ou
lojas, facilitando a gestão de inventários distribuídos. Além disso, o sistema oferece uma funcionalidade de transferência
de materiais entre estoques, permitindo que produtos sejam movidos de um local para outro conforme necessário.
</details>
