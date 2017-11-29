---
title: "軽減策: XML スキーマ検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8bc8aab23490b5531a155798520936cacbd6a6d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="ae08c-102">軽減策: XML スキーマ検証</span><span class="sxs-lookup"><span data-stu-id="ae08c-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="ae08c-103">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降では、複合キーが使用され、1 つのキーが空の場合、XSD スキーマ検証で一意制約の違反が検出されます。</span><span class="sxs-lookup"><span data-stu-id="ae08c-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ae08c-104">影響</span><span class="sxs-lookup"><span data-stu-id="ae08c-104">Impact</span></span>  
 <span data-ttu-id="ae08c-105">この変更の影響は最小限のものになります。スキーマの仕様に基づき、複合キーが空のキーと共に使用されて `xsd:unique` の違反が発生した場合、スキーマの検証エラーの発生が予期されます。</span><span class="sxs-lookup"><span data-stu-id="ae08c-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ae08c-106">軽減策</span><span class="sxs-lookup"><span data-stu-id="ae08c-106">Mitigation</span></span>  
 <span data-ttu-id="ae08c-107">複合キーに空の 1 つのキーがある場合にスキーマ検証エラーが検出されるようにするかどうかは、構成可能な機能です。</span><span class="sxs-lookup"><span data-stu-id="ae08c-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="ae08c-108">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降を対象とするアプリでは、スキーマ検証エラーの検出は既定で有効になっています。ただし、この動作を無効にして、スキーマ検証エラーが検出されないようにすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="ae08c-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="ae08c-109">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] の下で実行されているものの、[!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 以前のバージョンを対象とするアプリでは、既定ではスキーマ検証エラーが検出されません。ただし、この動作を有効にして、スキーマ検証エラーが検出されるようにすることも可能です。</span><span class="sxs-lookup"><span data-stu-id="ae08c-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="ae08c-110">この動作は、<xref:System.AppContext> クラスを使用して `System.Xml.IgnoreEmptyKeySequences` スイッチの値を定義することにより構成できます。</span><span class="sxs-lookup"><span data-stu-id="ae08c-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="ae08c-111">スイッチの既定値が `false` (空のキー シーケンスが無視されない) であるため、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] を対象とするアプリは、以下のコードを使用してスイッチの値を `true` に設定することにより、その動作を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ae08c-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="ae08c-112">[!INCLUDE[net_v452](../../../includes/net-v452-md.md)] 以前のバージョンを対象とするアプリでは、スイッチの既定値が `true` (空のキー シーケンスが無視される) であるため、以下のコードを使用してスイッチの値を `false` に設定することにより、複合キーに空のキーがある場合にスキーマ検証エラーを生成させることが可能です。</span><span class="sxs-lookup"><span data-stu-id="ae08c-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ae08c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae08c-113">See Also</span></span>  
 [<span data-ttu-id="ae08c-114">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="ae08c-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
