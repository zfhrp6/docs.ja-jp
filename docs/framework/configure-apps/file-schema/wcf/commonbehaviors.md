---
title: '&lt;commonBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b39942cc438201ceaecf1fee62ce3fefdc27b68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` セクションは、machine.config ファイルでだけ定義できます。 このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、コンピューター上の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のすべてのエンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。 `endpointBehaviors` で定義される動作はクライアントだけに適用され、`serviceBehaviors` で定義される動作はサービスだけに適用されます。 ある動作が `commonBehaviors` と `behaviors` の両方のセクションで定義されている場合は、`behaviors` セクション内の動作が優先されます。
