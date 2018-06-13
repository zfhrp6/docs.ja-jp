---
title: .NET リモート処理アプリケーションの WCF への移行
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492497"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="25bc5-102">.NET リモート処理アプリケーションの WCF への移行</span><span class="sxs-lookup"><span data-stu-id="25bc5-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="25bc5-103">**このトピックの対象は、既存のアプリケーションとの下位互換性のために残されているレガシ テクノロジに特定されています。新規の開発には、このトピックを適用しないでください。WCF を使用して、分散アプリケーションを開発する必要がありますようになりました。**</span><span class="sxs-lookup"><span data-stu-id="25bc5-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="25bc5-104">既存の .NET リモート処理アプリケーションで WCF を活用するために 2 つの方法: 統合と移行します。</span><span class="sxs-lookup"><span data-stu-id="25bc5-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="25bc5-105">統合を使用すると、.net Remoting 2.0 とを実行している WCF 側の側では、によって、既存の .Net を変更しなくても同時に両方のテクノロジで、同じビジネス オブジェクトを公開すること Remoting 2.0 コード。</span><span class="sxs-lookup"><span data-stu-id="25bc5-105">Integration allows you to have .Net Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="25bc5-106">統合では、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 以降が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="25bc5-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="25bc5-107">WCF の機能を利用して、Remoting 2.0 システムとの互換性をネットワーク上の必要はない場合、は、サービス全体を WCF に移行できます。</span><span class="sxs-lookup"><span data-stu-id="25bc5-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="25bc5-108">.NET Remoting 2.0 から WCF への移行には、リモート オブジェクトのインターフェイスとその構成設定の変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="25bc5-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="25bc5-109">これらのトピックの両方については、「[からリモート処理を Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403)です。</span><span class="sxs-lookup"><span data-stu-id="25bc5-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bc5-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="25bc5-110">See Also</span></span>  
 [<span data-ttu-id="25bc5-111">概念</span><span class="sxs-lookup"><span data-stu-id="25bc5-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
