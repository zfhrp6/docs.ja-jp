---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350323"
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="d39ec-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="d39ec-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="d39ec-103">`commonBehaviors` セクションは、machine.config ファイルでだけ定義できます。</span><span class="sxs-lookup"><span data-stu-id="d39ec-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="d39ec-104">このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="d39ec-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d39ec-105">各コレクションは、すべての WCF エンドポイントと、コンピューター上のサービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="d39ec-105">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="d39ec-106">`endpointBehaviors` で定義される動作はクライアントだけに適用され、`serviceBehaviors` で定義される動作はサービスだけに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d39ec-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="d39ec-107">ある動作が `commonBehaviors` と `behaviors` の両方のセクションで定義されている場合は、`behaviors` セクション内の動作が優先されます。</span><span class="sxs-lookup"><span data-stu-id="d39ec-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
