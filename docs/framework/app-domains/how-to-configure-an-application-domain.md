---
title: "方法 : アプリケーション ドメインを構成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, configuring
- ApplicationBase property
ms.assetid: 07ea8438-7a34-49f0-a7e8-3d6ff7e4a482
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4f8c91a11deac63e2ad44628a609ed4ca6501e84
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-configure-an-application-domain"></a><span data-ttu-id="bb6ab-102">方法 : アプリケーション ドメインを構成する</span><span class="sxs-lookup"><span data-stu-id="bb6ab-102">How to: Configure an Application Domain</span></span>
<span data-ttu-id="bb6ab-103"><xref:System.AppDomainSetup> クラスを利用し、新しいアプリケーション ドメインの構成情報を共通言語ランタイムに提供できます。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-103">You can provide the common language runtime with configuration information for a new application domain using the <xref:System.AppDomainSetup> class.</span></span> <span data-ttu-id="bb6ab-104">独自のアプリケーション ドメインを作成するとき、最も重要なプロパティが <xref:System.AppDomainSetup.ApplicationBase%2A> です。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-104">When creating your own application domains, the most important property is <xref:System.AppDomainSetup.ApplicationBase%2A>.</span></span> <span data-ttu-id="bb6ab-105">その他の **AppDomainSetup** プロパティは、特定のアプリケーション ドメインを構成する目的で主にランタイム ホストにより使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-105">The other **AppDomainSetup** properties are used mainly by runtime hosts to configure a particular application domain.</span></span>  
  
 <span data-ttu-id="bb6ab-106">**ApplicationBase** プロパティにより、アプリケーションのルート ディレクトリが定義されます。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-106">The **ApplicationBase** property defines the root directory of the application.</span></span> <span data-ttu-id="bb6ab-107">ランタイムで型要求を満たす必要があるとき、**ApplicationBase** プロパティで指定されたディレクトリでその型を含むアセンブリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-107">When the runtime needs to satisfy a type request, it probes for the assembly containing the type in the directory specified by the **ApplicationBase** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb6ab-108">新しいアプリケーション ドメインは、作成者の **ApplicationBase** プロパティのみを継承します。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-108">A new application domain inherits only the **ApplicationBase** property of the creator.</span></span>  
  
 <span data-ttu-id="bb6ab-109">次の例では、**AppDomainSetup** クラスのインスタンスが作成され、このクラスを利用して新しいアプリケーション ドメインが作成され、情報がコンソールに書き込まれ、アプリケーション ドメインがアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="bb6ab-109">The following example creates an instance of the **AppDomainSetup** class, uses this class to create a new application domain, writes the information to console, and then unloads the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6ab-110">例</span><span class="sxs-lookup"><span data-stu-id="bb6ab-110">Example</span></span>  
 <span data-ttu-id="bb6ab-111">[!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)] [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)] [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="bb6ab-111">[!code-cpp[ADApplicationBase#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADApplicationBase/CPP/source2.cpp#2)] [!code-csharp[ADApplicationBase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADApplicationBase/CS/source2.cs#2)] [!code-vb[ADApplicationBase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADApplicationBase/VB/source2.vb#2)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6ab-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb6ab-112">See Also</span></span>  
 <span data-ttu-id="bb6ab-113">[アプリケーション ドメインを使用したプログラミング](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="bb6ab-113">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 [<span data-ttu-id="bb6ab-114">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="bb6ab-114">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

