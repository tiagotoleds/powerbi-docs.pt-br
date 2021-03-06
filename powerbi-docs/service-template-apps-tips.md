---
title: Dicas para a criação de aplicativos de modelo no Power BI (versão prévia)
description: Dicas sobre a criação de consultas, modelos de dados, relatórios e dashboards para criar ótimos aplicativos de modelo
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/05/2019
ms.author: maggies
ms.openlocfilehash: 282638c7c1c8a60ee93292602766d63fd0fe436e
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249506"
---
# <a name="tips-for-authoring-template-apps-in-power-bi-preview"></a>Dicas para a criação de aplicativos de modelo no Power BI (versão prévia)

Quando você estiver [criando o aplicativo de modelo](service-template-apps-create.md) no Power BI, uma parte dele será a logística de criação, teste e produção do workspace. Porém, a outra parte importante é, obviamente, a criação do relatório e do dashboard. Podemos dividir o processo de criação em quatro componentes principais. O trabalho nesses componentes ajuda você a criar o melhor aplicativo de modelo possível:

* Com as **consultas**, você [conecta](desktop-connect-to-data.md) e [transforma](desktop-query-overview.md) os dados e define [parâmetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/). 
* No **modelo de dados**, você cria [relações](desktop-create-and-manage-relationships.md), [medidas](desktop-measures.md) e melhorias da P e R.  
* As **[páginas de relatório](desktop-report-view.md)** incluem visuais e filtros para fornecer insights sobre seus dados.  
* Os **[dashboards](consumer/end-user-dashboards.md)** e os [blocos](service-dashboard-create.md) oferecem uma visão geral dos insights incluídos.  

Talvez você esteja familiarizado com cada uma das partes como recursos existentes no Power BI. Ao criar um aplicativo de modelo, há considerações adicionais a serem feitas para cada parte. Veja cada seção abaixo para obter mais detalhes.

<a name="queries"></a>

## <a name="queries"></a>Consultas
Para aplicativos de modelo, as consultas desenvolvidas no Power BI Desktop são usadas para se conectar à fonte de dados e importar os dados. Essas consultas são necessárias para retornar um esquema consistente e são compatíveis com a atualização de Dados Agendada (não há suporte para o DirectQuery).

### <a name="connect-to-your-api"></a>Conectar-se à sua API
Para começar, você precisará se conectar à sua API por meio do Power BI Desktop para iniciar a criação das consultas.

Você pode usar os Conectores de Dados que estão prontos para uso no Power BI Desktop para conectar-se à sua API. Você pode usar o Conector de Dados da Web (Obter Dados -> Web) para conectar-se ao seu conector da API REST ou do OData (Obter Dados -> Feed OData) para conectar-se ao seu feed OData. Esses conectores prontos para uso só funcionarão se a API der suporte à Autenticação Básica.

> [!NOTE]
> Se a API usar qualquer outro tipo de autenticação, como OAuth 2.0 ou Chave de API Web, você precisará desenvolver seu próprio Conector de Dados para permitir que o Power BI Desktop se conecte à API e se autentique nela com êxito. Para obter detalhes de como desenvolver seu próprio Conector de Dados para o aplicativo de modelo, confira a [documentação dos Conectores de Dados](https://aka.ms/DataConnectors). 
>
>

### <a name="consider-the-source"></a>Considere o código-fonte
As consultas definem os dados que serão incluídos no modelo de dados. Dependendo do tamanho do seu sistema, essas consultas também devem incluir filtros para garantir que seus clientes estejam lidando com um tamanho gerenciável adequado ao seu cenário de negócios.

Os aplicativos de modelo do Power BI podem executar várias consultas em paralelo e para vários usuários simultaneamente.  Planeje sua estratégia de limitação e simultaneidade com certa antecedência e fale conosco para saber como transformar seu aplicativo de modelo em um aplicativo de tolerância a falhas.

### <a name="schema-enforcement"></a>Imposição do esquema
Verifique se as consultas são resistentes a alterações em seu sistema, alterações no esquema após atualizações podem interromper o modelo. Se a fonte puder retornar resultados de esquema nulo ou ausente para algumas consultas, considere o retorno de uma tabela vazia ou de uma mensagem de erro personalizada relevante.

### <a name="parameters"></a>Parâmetros
Os [parâmetros](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) no Power BI Desktop permitem que os usuários forneçam valores de entrada que personalizam os dados recuperados pelo usuário. Pense antecipadamente nos parâmetros para evitar retrabalho depois de investir tempo para criar consultas ou relatórios detalhados.

> [!NOTE]
> Os aplicativos de modelo dão suporte a todos os parâmetros, exceto Qualquer e Binário.
>

### <a name="additional-query-tips"></a>Dicas de consulta adicionais

* Verifique se todas as colunas foram tipadas corretamente.
* As colunas têm nomes informativos (confira [P e R](#qa)).  
* Para a lógica compartilhada, considere o uso de funções ou consultas.  
* Atualmente, não há suporte para os níveis de privacidade no serviço. Se você receber um prompt sobre os níveis de privacidade, talvez você precise reescrever a consulta para usar caminhos relativos.  

## <a name="data-models"></a>Modelo de dados

Um modelo de dados bem definido garante que os clientes possam interagir de forma fácil e intuitiva com o aplicativo de modelo. Crie o modelo de dados no Power BI Desktop.

> [!NOTE]
> Você deverá realizar grande parte da modelagem básica (definição de tipos, nomes de coluna) nas [consultas](#queries).
>


### <a name="qa"></a>P e R
A modelagem também afeta a eficiência da P e R em fornecer resultados para os clientes. Adicione sinônimos para as colunas mais usadas e nomeie as colunas apropriadamente nas [consultas](#queries).

### <a name="additional-data-model-tips"></a>Dicas adicionais sobre modelos de dados

Verifique se você:
* Aplicou a formatação a todas as colunas de valor. Aplicou os tipos na consulta.  
* Aplicou a formatação a todas as medidas. 
* Definiu o resumo padrão. Especialmente "Não Resumir", quando aplicável (para valores exclusivos, por exemplo).  
* Definiu a categoria de dados, quando aplicável.  
* Definiu relações, conforme necessário.  

## <a name="reports"></a>Relatórios
As páginas de relatório oferecem insights adicionais sobre os dados incluídos no aplicativo de modelo. Use as páginas do relatório para responder às principais questões de negócios que o aplicativo de modelo está tentando solucionar. Crie o relatório usando o Power BI Desktop.

> [!NOTE]
> Como você só pode incluir um relatório em um aplicativo de modelo, aproveite as diferentes páginas para destacar seções específicas do cenário.
>
>

### <a name="additional-report-tips"></a>Dicas adicionais sobre relatórios

* Use mais de um visual por página para a filtragem cruzada.  
* Alinhe os visuais cuidadosamente (sem sobreposição).  
* O layout da página é definido como "4:3" ou "16:9".  
* Todas as agregações apresentadas fazem sentido em termos numéricos (médias, valores exclusivos).  
* A divisão gera resultados racionais.  
* O logotipo está presente, pelo menos, no relatório principal.  
* Os elementos estão no esquema de cores do cliente na medida do possível.  

<a name="dashboard"></a>

## <a name="dashboards"></a>Dashboards
O dashboard é o principal ponto de interação com o aplicativo de modelo para seus clientes. Ele deve incluir uma visão geral do conteúdo incluído, especialmente as métricas importantes para seu cenário de negócios.

Para criar um dashboard para o aplicativo de modelo, basta carregar o PBIX por meio de Obter Dados > Arquivos ou publicá-lo diretamente por meio do Power BI Desktop.

> [!NOTE]
> Atualmente, os aplicativos de modelo exigem um único relatório e conjunto de dados por aplicativo de modelo. Não fixe o conteúdo de vários relatórios/conjuntos de dados no dashboard usado no aplicativo de modelo.
>
>

### <a name="additional-dashboard-tips"></a>Dicas adicionais sobre painéis

* Mantenha o mesmo tema ao fixar o conteúdo, de modo que os blocos no dashboard sejam consistentes.  
* Fixe um logotipo no tema para que os consumidores saibam qual é a origem do pacote.  
* O layout sugerido para trabalhar com a maioria das resoluções de tela tem uma largura de 5 a 6 blocos pequenos.  
* Todos os blocos de dashboard devem ter títulos/subtítulos apropriados.  
* Considere a possibilidade de agrupamentos no dashboard para diferentes cenários, vertical ou horizontalmente.  

## <a name="known-limitations"></a>Limitações conhecidas

| Recurso | Limitações conhecidas |
|---------|---------|
|Conteúdo:  Conjuntos de dados   | É necessário que exatamente um conjunto de dados esteja presente. Apenas conjuntos de dados criados no Power BI Desktop (arquivos .pbix) são permitidos. <br>Sem suporte: Conjuntos de dados de outros aplicativos de modelo, conjuntos de dados entre workspaces, relatórios paginados (arquivos .rdl) e pastas de trabalho do Excel |
|Conteúdo: Relatórios     | Até um relatório    |
| Conteúdo: Dashboards | Até um dashboard não vazio <br>Sem suporte: Blocos em tempo real (em outras palavras, não há suporte para PushDataset ou PubNub) |
| Conteúdo: Fluxos de dados | Sem suporte: Fluxos de dados |
| Conteúdo de arquivos | Apenas arquivos PBIX são permitidos. <br>Sem suporte: arquivos .rdl (relatórios paginados) e pastas de trabalho do Excel   |
| Fontes de dados | Fontes de dados compatíveis com a atualização de Dados Agendada na nuvem são permitidas. <br>Sem suporte: <br>DirectQuery <br>Conexões dinâmicas (sem o Azure AS) <br>Fontes de dados locais (não há suporte para gateways pessoais e empresariais) <br>Em tempo real (não há suporte para PushDataset) <br>Modelos compostos |
| Conjunto de dados: entre workspaces | Conjuntos de dados entre workspaces não são permitidos  |
| Conteúdo: Dashboards | Blocos em tempo real não são permitidos (em outras palavras, não há suporte para PushDataset ou PubNub) |
| Parâmetros de consulta | Sem suporte: Parâmetros do tipo "Qualquer" ou "Binário" bloqueiam a operação de atualização do conjunto de dados |
| Visuais personalizados | Somente há suporte para visuais personalizados disponíveis publicamente. Não há suporte para [visuais personalizados organizacionais](power-bi-custom-visuals-organization.md) |

## <a name="next-steps"></a>Próximas etapas

[O que são os aplicativos de modelo do Power BI? (versão prévia)](service-template-apps-overview.md)
