---
title: Análise integrada com o Power BI
description: O Power BI oferece APIs para usar análises integradas para seus dashboards e relatórios nos aplicativos. Saiba mais sobre a integração com o Power BI em ambientes de PaaS e SaaS usando software de análise integrada, ferramentas de análise integrada ou ferramentas de business intelligence inseridas.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 02/05/2019
ms.openlocfilehash: 0a4b43bd02697472a0bbdf16171ba655fc014dbc
ms.sourcegitcommit: 3a05f34dbeabac62ea8c35c12a045284271971bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872698"
---
# <a name="embedded-analytics-with-power-bi"></a>Análise integrada com o Power BI

O serviço do Power BI (SaaS) e o serviço do Power BI Embedded no Azure (PaaS) têm APIs para inserir seus painéis e seus relatórios. Esse recurso significa que você tem um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como painéis, gateways e espaço de trabalhos de aplicativo, ao inserir seu conteúdo.

É possível acessar a [Ferramenta de configuração de inserção](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo.

Escolha a solução certa para você:

* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Execute a solução [Inserir para a organização](https://aka.ms/embedsetup/UserOwnsData).
* A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Execute a solução [Inserir para clientes](https://aka.ms/embedsetup/AppOwnsData).

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>Usando APIs

Há dois cenários principais ao inserir conteúdo do Power BI. Inserir para usuários em sua organização (que têm licenças para o Power BI) e inserir para seus usuários e clientes sem que eles precisem ter licenças do Power BI. A API REST do Power BI permite os dois cenários.

Para clientes e usuários sem licenças do Power BI, você pode inserir painéis e relatórios em seu aplicativo personalizado, usando a mesma API para atender a organização ou os clientes. Os clientes veem os dados que são gerenciados pelo aplicativo. Além disso, para usuários do Power BI em sua organização, eles têm as opções adicionais para exibir *seus dados* diretamente no Power BI ou no contexto do aplicativo inserido. Você pode se beneficiar das APIs REST e do JavaScript para suas necessidades de inserção.

Para exibir uma amostra de como a inserção funciona, consulte a [amostra de inserção do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserção para a organização

A **inserção para a organização** permite que você estenda o serviço do Power BI. A inserção para a organização requer que os usuários do aplicativo entrem no serviço do Power BI quando eles desejarem exibir o conteúdo. Depois que alguém na organização se conectar, esse usuário só terá acesso aos dashboards e relatórios dos quais ele é proprietário ou que alguém compartilhou com ele no serviço do Power BI.

*Os exemplos de inserção para a organização incluem aplicativos internos, como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [integração do Microsoft Teams](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) (é necessário ter direitos de administrador) e [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).*

Para inserir para a organização, consulte o seguinte:

* [Integrar um relatório em um aplicativo](embed-sample-for-your-organization.md)

Recursos de autoatendimento, como editar, salvar e muito mais, estão disponíveis por meio de [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) ao inserir para usuários do Power BI.

Você pode examinar a [Ferramenta de experiência de inserção](https://aka.ms/embedsetup/UserOwnsData) para inserção para a sua organização para iniciar e baixar um aplicativo de exemplo que explica como integrar um relatório para a organização.

## <a name="embedding-for-your-customers"></a>Inserção para os clientes

A **inserção para clientes** permite que você insira os dashboards e relatórios para usuários que não têm uma conta do Power BI. A inserção para clientes também é conhecida como **Power BI Embedded**.

O [Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) é um serviço do **Microsoft Azure** que permite que ISVs (fornecedores de software independentes) e desenvolvedores insiram rapidamente visuais, relatórios e dashboards em um aplicativo por meio de um modelo medido em horas com base em capacidade.

![Fluxo de inserção ao inserir para os clientes](media/embedding/powerbi-embed-flow.png)

O Power BI Embedded fornece benefícios para um ISV, seus desenvolvedores e clientes. Por exemplo, um ISV pode começar a criar elementos visuais gratuitamente com o Power BI Desktop. Os ISVs podem obter tempo de lançamento mais rápido minimizando os esforços de desenvolvimento de análise visual e se destacando em relação à concorrência com experiências de dados diferenciadas. Os ISVs também podem optar por cobrar uma taxa para o valor adicional criado com a análise integrada.

Com o Power BI Embedded, seus clientes não precisam saber nada sobre o Power BI. Você pode usar dois métodos diferentes para criar um aplicativo inserido. Uma opção é usar uma conta do Power BI Pro. Outra opção é usar a entidade de serviço. 

A conta do Power BI Pro funciona como uma conta mestre do seu aplicativo (pense nessa conta mestre como uma conta de proxy). A conta do Power BI Pro permite a geração de tokens de inserção que fornecem acesso a dashboards e relatórios no serviço do Power BI que são de propriedade e gerenciados pelo seu aplicativo.

[Entidade de serviço](embed-service-principal.md) pode inserir o conteúdo do Power BI em um aplicativo usando um token **somente de aplicativo**. A entidade de serviço permite que você gere tokens inseridos que dão acesso a dashboards e relatórios no serviço do Power BI que são de propriedade e gerenciados pelo seu aplicativo.

Os desenvolvedores que usam o Power BI Embedded podem passar o tempo concentrados na criação da competência principal do seu aplicativo, em vez de gastar tempo desenvolvendo visuais e análise. Os desenvolvedores podem atender rapidamente as demandas de dashboard e relatório do cliente e podem inserir facilmente com APIs e SDKs totalmente documentadas. Ao habilitar a exploração de dados fácil de navegar em aplicativos, os ISVs permitem que seus clientes tomem decisões rápidas e direcionadas a dados no contexto em qualquer dispositivo.

> [!IMPORTANT]
> Embora a inserção seja dependente do serviço do Power BI, não há uma dependência do Power BI para os clientes. Eles não precisa inscrever-se no Power BI para exibir o conteúdo inserido em seu aplicativo.

Quando você estiver pronto para passar para a produção, seu espaço de trabalho do aplicativo deverá ser atribuído a uma capacidade dedicada. O Power BI Embedded no Microsoft Azure oferece [capacidades dedicadas](azure-pbie-create-capacity.md) a serem usadas com seus aplicativos.

Para obter detalhes sobre como inserir, veja [Como inserir conteúdo do Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Próximas etapas

Agora você pode tentar inserir o conteúdo do Power BI em um aplicativo ou tentar inserir o conteúdo do Power BI para seus clientes.

> [!div class="nextstepaction"]
> [Inserir para a organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [O que é o Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
