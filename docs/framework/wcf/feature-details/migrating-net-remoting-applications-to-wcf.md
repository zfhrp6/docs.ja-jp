---
title: ".NET リモート処理アプリケーションの WCF への移行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7d305adf1810832016cdafbb60fc025f17e0786
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="e164c-102">.NET リモート処理アプリケーションの WCF への移行</span><span class="sxs-lookup"><span data-stu-id="e164c-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="e164c-103">**このトピックの対象は、既存のアプリケーションとの下位互換性のために残されているレガシ テクノロジに特定されています。新規の開発には、このトピックを適用しないでください。現在、分散アプリケーションは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して開発する必要があります。**</span><span class="sxs-lookup"><span data-stu-id="e164c-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="e164c-104">既存の .NET リモート処理アプリケーションから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を利用するには、統合と移行という 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e164c-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="e164c-105">統合によって、.NET Remoting 2.0 と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を並行で実行できるようになり、既存の.NET Remoting 2.0 のコードに手を加えることなく、両方のテクノロジで同時に同じビジネス オブジェクトを公開できます。</span><span class="sxs-lookup"><span data-stu-id="e164c-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="e164c-106">統合では、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 以降が実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e164c-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="e164c-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の機能を利用し、Remoting 2.0 システムとのネットワーク上での互換性が必要ではない場合は、サービス全体を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行できます。</span><span class="sxs-lookup"><span data-stu-id="e164c-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="e164c-108">.NET Remoting 2.0 から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] への移行には、リモート オブジェクトのインターフェイスとその構成設定の変更が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e164c-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="e164c-109">これらのトピックの両方については、「[からリモート処理を Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403)です。</span><span class="sxs-lookup"><span data-stu-id="e164c-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e164c-110">参照</span><span class="sxs-lookup"><span data-stu-id="e164c-110">See Also</span></span>  
 [<span data-ttu-id="e164c-111">概念</span><span class="sxs-lookup"><span data-stu-id="e164c-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
