---
title: "WCF ライブラリ プロジェクトの配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbbbff1d88559f8ab35caa48fcb04ff1cd7bf015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="2ad31-102">WCF ライブラリ プロジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="2ad31-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="2ad31-103">ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス ライブラリ プロジェクトの配置方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ad31-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="2ad31-104">WCF サービス ライブラリの配置</span><span class="sxs-lookup"><span data-stu-id="2ad31-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="2ad31-105">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリは、ダイナミックリンク ライブラリ (DLL) です。</span><span class="sxs-lookup"><span data-stu-id="2ad31-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="2ad31-106">それ自体を単独で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="2ad31-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="2ad31-107">ホスティング環境に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ad31-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="2ad31-108">このプロセスの詳細については、次を参照してください。[ホスティングと WCF サービスの消費](http://go.microsoft.com/fwlink/?LinkId=99932)です。</span><span class="sxs-lookup"><span data-stu-id="2ad31-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="2ad31-109">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリは、他の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスと同様に配置できます。</span><span class="sxs-lookup"><span data-stu-id="2ad31-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="2ad31-110">ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、DLL に対する構成がサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2ad31-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="2ad31-111"><xref:System.Configuration> では、アプリケーション ドメイン 1 つにつき、1 つの構成ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2ad31-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="2ad31-112">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ プロジェクトにより、配置中、ライブラリに App.config ファイルが提供され、この制限が緩和されます。</span><span class="sxs-lookup"><span data-stu-id="2ad31-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="2ad31-113">ただし、配置後、この App.config ファイルは認識されません。</span><span class="sxs-lookup"><span data-stu-id="2ad31-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="2ad31-114">構成コードは、ホスティング環境で認識されている構成ファイルに移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ad31-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="2ad31-115">自己ホストを行うには、App.config ファイルの内容をホスティング実行可能形式の App.config ファイルにコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="2ad31-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="2ad31-116">サービスのホスティングに IIS を使用する場合は、App.config ファイルの内容を仮想ディレクトリの Web.config ファイルにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ad31-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
