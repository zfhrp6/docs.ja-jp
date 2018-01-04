---
title: "部分信頼"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac76f092d5583519220d2d1b7a8d6d1bbb665632
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="partial-trust"></a><span data-ttu-id="c28ba-102">部分信頼</span><span class="sxs-lookup"><span data-stu-id="c28ba-102">Partial Trust</span></span>
<span data-ttu-id="c28ba-103">[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降では、部分的に信頼された呼び出し元は、<xref:System.ServiceModel>、<xref:System.Runtime.Serialization>、および <xref:System.ServiceModel.Web> に実装されたパブリック型とパブリック メソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c28ba-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="c28ba-104">このセクションでは、部分的に信頼されたアプリケーション内における [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の使用でサポートされるシナリオと、コード アクセス セキュリティ (CAS: Code Access Security) のアクセス許可レベルを下げて実行されるアプリケーションで利用できる、限られた [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="c28ba-104">This section describes supported scenarios for using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] within a partially trusted application as well as the limited subset of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c28ba-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c28ba-105">In This Section</span></span>  
 [<span data-ttu-id="c28ba-106">サポートされている配置シナリオ</span><span class="sxs-lookup"><span data-stu-id="c28ba-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="c28ba-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を実行するための主な部分信頼シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c28ba-107">Describes the main partial trust scenarios for running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="c28ba-108">部分信頼機能の互換性</span><span class="sxs-lookup"><span data-stu-id="c28ba-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="c28ba-109">部分信頼では使用できない [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="c28ba-109">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="c28ba-110">部分信頼のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c28ba-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="c28ba-111">部分信頼アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用するためのベスト プラクティスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="c28ba-111">Contains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in partially trusted applications.</span></span>
