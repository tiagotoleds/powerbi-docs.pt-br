---
title: O que posso fazer com a API do Power BI
description: O que posso fazer com a API do Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 03/25/2019
ms.openlocfilehash: 443aa370ebb4122d0f979f60726ba953ce13195d
ms.sourcegitcommit: 3a05f34dbeabac62ea8c35c12a045284271971bc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872560"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>O que os desenvolvedores podem fazer com a API do Power BI?

Ao usar a API REST do Power BI, é possível criar aplicativos que se integram a relatórios, dashboards e blocos do Power BI.

Com a API REST do Power BI, é possível realizar tarefas de gerenciamento em objetos do Power BI, como relatórios, conjuntos de dados e workspaces.

Aqui estão algumas das coisas que você pode fazer com as APIs do Power BI.

| **Para saber mais** | **Consultar estas informações** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Inserir relatórios, dashboards e blocos para usuários do Power BI e usuários que não têm o Power BI. | [Como inserir seus dashboards, relatórios e blocos do Power BI ](embedding-content.md) |
| Realize tarefas de gerenciamento em objetos do Power BI. | [Referência da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) |
| Estender um fluxo de trabalho de negócios existente para enviar por push dados de chave a um painel do Power BI. | [Enviar dados por push a um painel ](walkthrough-push-data.md) |
| Autentique-se no Power BI. | [Autenticar-se no Power BI ](get-azuread-access-token.md) |

> [!NOTE]
> As APIs do Power BI ainda se referem aos workspaces do aplicativo como grupos. As referências a grupos significam que você está trabalhando com workspaces do aplicativo.

## <a name="api-developer-tools"></a>Ferramentas para desenvolvedores de API

| Ferramentas | Descrição |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [Ferramenta de playground](https://microsoft.github.io/PowerBI-JavaScript/demo) | Experimente um exemplo completo de como usar as APIs JavaScript do Power BI. Essa ferramenta é também uma maneira rápida de experimentar diferentes tipos de exemplos do Power BI Embedded. |  |  |
| [Wiki do JavaScript do Power BI](https://github.com/Microsoft/powerbi-javascript/wiki) | Para obter mais informações sobre as APIs JavaScript do Power BI. |  |  |
| [Postman](https://www.getpostman.com/) | Executar solicitações, testar, depurar, monitorar, executar testes automatizados e muito mais. |

## <a name="push-data-into-power-bi"></a>Enviar dados por push ao Power BI

Você pode usar a API do Power BI para [enviar dados por push a um conjunto de dados](walkthrough-push-data.md). Esse recurso permite que você adicione uma linha a uma tabela dentro de um conjunto de dados. Os novos dados são então mostrados em blocos em um dashboard e dentro de elementos visuais no seu relatório.

![Exemplo de envio de dados por push](media/what-can-you-do/powerbi-push-data.png)

## <a name="github-repositories"></a>Repositórios GitHub

* [Exemplos para Desenvolvedores do Power BI](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [SDK do .NET](https://github.com/Microsoft/PowerBI-CSharp)
* [API do JavaScript](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>Próximas etapas

* [Enviar dados por push a um conjunto de dados](walkthrough-push-data.md)
* [Desenvolvimento de um visual personalizado do Power BI](custom-visual-develop-tutorial.md)
* [Referência da API REST do Power BI](rest-api-reference.md)
* [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
