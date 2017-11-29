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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3febf1f3703377806493c8067b50c149bce0108
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="partial-trust"></a><span data-ttu-id="f042c-102">部分信頼</span><span class="sxs-lookup"><span data-stu-id="f042c-102">Partial Trust</span></span>
<span data-ttu-id="f042c-103">[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降では、部分的に信頼された呼び出し元は、<xref:System.ServiceModel>、<xref:System.Runtime.Serialization>、および <xref:System.ServiceModel.Web> に実装されたパブリック型とパブリック メソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f042c-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="f042c-104">このセクションでは、部分的に信頼されたアプリケーション内における [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の使用でサポートされるシナリオと、コード アクセス セキュリティ (CAS: Code Access Security) のアクセス許可レベルを下げて実行されるアプリケーションで利用できる、限られた [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f042c-104">This section describes supported scenarios for using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] within a partially trusted application as well as the limited subset of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f042c-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f042c-105">In This Section</span></span>  
 [<span data-ttu-id="f042c-106">サポートされている配置シナリオ</span><span class="sxs-lookup"><span data-stu-id="f042c-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="f042c-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を実行するための主な部分信頼シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f042c-107">Describes the main partial trust scenarios for running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="f042c-108">部分信頼機能の互換性</span><span class="sxs-lookup"><span data-stu-id="f042c-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="f042c-109">部分信頼では使用できない [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f042c-109">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="f042c-110">部分信頼のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f042c-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="f042c-111">部分信頼アプリケーションで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用するためのベスト プラクティスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="f042c-111">Contains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in partially trusted applications.</span></span>
