---
title: '方法 : アプリケーション ドメインを構成する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8db75edec8e80e0e137593a424f12575cfc747b
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="95de5-102">方法 : アプリケーション ドメインを構成する</span><span class="sxs-lookup"><span data-stu-id="95de5-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="95de5-103"><xref:System.AppDomainSetup> クラスを利用し、新しいアプリケーション ドメインの構成情報を共通言語ランタイムに提供できます。</span><span class="sxs-lookup"><span data-stu-id="95de5-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="95de5-104">独自のアプリケーション ドメインを作成するとき、最も重要なプロパティが <xref:System.AppDomainSetup.ApplicationBase%2A> です。</span><span class="sxs-lookup"><span data-stu-id="95de5-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="95de5-105">その他の **AppDomainSetup** プロパティは、特定のアプリケーション ドメインを構成する目的で主にランタイム ホストにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="95de5-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="95de5-106">**ApplicationBase** プロパティにより、アプリケーションのルート ディレクトリが定義されます。</span><span class="sxs-lookup"><span data-stu-id="95de5-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="95de5-107">ランタイムで型要求を満たす必要があるとき、**ApplicationBase** プロパティで指定されたディレクトリでその型を含むアセンブリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="95de5-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95de5-108">新しいアプリケーション ドメインは、作成者の **ApplicationBase** プロパティのみを継承します。</span><span class="sxs-lookup"><span data-stu-id="95de5-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="95de5-109">次の例では、**AppDomainSetup** クラスのインスタンスが作成され、このクラスを利用して新しいアプリケーション ドメインが作成され、情報がコンソールに書き込まれ、アプリケーション ドメインがアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="95de5-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95de5-110">例</span><span class="sxs-lookup"><span data-stu-id="95de5-110">Example</span></span>  
 [!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)]
 [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)]
 [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="95de5-111">参照</span><span class="sxs-lookup"><span data-stu-id="95de5-111">See Also</span></span>  
 [<span data-ttu-id="95de5-112">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="95de5-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="95de5-113">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="95de5-113">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
