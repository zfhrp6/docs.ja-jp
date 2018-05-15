---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: aaf89f73b6de250aaa572b8fef31e5a1ebd5482b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="484d7-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="484d7-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="484d7-103">`commonBehaviors` セクションは、machine.config ファイルでだけ定義できます。</span><span class="sxs-lookup"><span data-stu-id="484d7-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="484d7-104">このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="484d7-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="484d7-105">各コレクションは、コンピューター上の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のすべてのエンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="484d7-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="484d7-106">`endpointBehaviors` で定義される動作はクライアントだけに適用され、`serviceBehaviors` で定義される動作はサービスだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="484d7-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="484d7-107">ある動作が `commonBehaviors` と `behaviors` の両方のセクションで定義されている場合は、`behaviors` セクション内の動作が優先されます。</span><span class="sxs-lookup"><span data-stu-id="484d7-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
