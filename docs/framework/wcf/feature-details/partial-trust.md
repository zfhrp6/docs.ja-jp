---
title: 部分信頼
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: a6bdcd4424670b18a81d8fa274f213ef4be4c2c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492012"
---
# <a name="partial-trust"></a><span data-ttu-id="c1494-102">部分信頼</span><span class="sxs-lookup"><span data-stu-id="c1494-102">Partial Trust</span></span>
<span data-ttu-id="c1494-103">[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 以降では、部分的に信頼された呼び出し元は、<xref:System.ServiceModel>、<xref:System.Runtime.Serialization>、および <xref:System.ServiceModel.Web> に実装されたパブリック型とパブリック メソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c1494-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="c1494-104">このセクションがコード アクセス セキュリティ (CAS) で実行されているアプリケーションで使用可能な WCF 機能の限定サブセットと同様に、部分的に信頼されたアプリケーション内で Windows Communication Foundation (WCF) を使用するためのサポートされるシナリオについて説明しますアクセス許可です。</span><span class="sxs-lookup"><span data-stu-id="c1494-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1494-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c1494-105">In This Section</span></span>  
 [<span data-ttu-id="c1494-106">サポートされている配置シナリオ</span><span class="sxs-lookup"><span data-stu-id="c1494-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="c1494-107">WCF を実行するための主な部分信頼シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c1494-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="c1494-108">部分信頼機能の互換性</span><span class="sxs-lookup"><span data-stu-id="c1494-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="c1494-109">部分信頼では使用できません WCF の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1494-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="c1494-110">部分信頼のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="c1494-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="c1494-111">部分的に信頼されたアプリケーションで WCF を使用するためのベスト プラクティスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1494-111">Contains best practices for using WCF in partially trusted applications.</span></span>
