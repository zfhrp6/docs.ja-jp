---
title: "アプリケーション ドメインからのセットアップ情報の取得"
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
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 865ae7b5cb005a5fc4fef283d63527b028253ad6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="retrieving-setup-information-from-an-application-domain"></a><span data-ttu-id="8d1a1-102">アプリケーション ドメインからのセットアップ情報の取得</span><span class="sxs-lookup"><span data-stu-id="8d1a1-102">Retrieving Setup Information from an Application Domain</span></span>
<span data-ttu-id="8d1a1-103">アプリケーション ドメインの各インスタンスは、プロパティと <xref:System.AppDomainSetup> 情報の両方で構成されています。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-103">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="8d1a1-104"><xref:System.AppDomain?displayProperty=fullName> クラスを使って、アプリケーション ドメインからセットアップ情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-104">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=fullName> class.</span></span> <span data-ttu-id="8d1a1-105">このクラスでは、アプリケーション ドメインに関する構成情報を取得する複数のメンバーが提供されています。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-105">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="8d1a1-106">また、アプリケーション ドメインの **AppDomainSetup** オブジェクトに対してクエリを実行し、作成時にドメインに渡されたセットアップ情報を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-106">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="8d1a1-107">次の例では、新しいアプリケーション ドメインを作成し、いくつかのメンバーの値をコンソールに出力しています。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-107">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 <span data-ttu-id="8d1a1-108">[!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)] [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)] [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="8d1a1-108">[!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)] [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)] [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]</span></span>  
  
 <span data-ttu-id="8d1a1-109">次の例では、アプリケーション ドメインのセットアップ情報を設定してから取得しています。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-109">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="8d1a1-110">`AppDomain.SetupInformation.ApplicationBase` が構成情報を取得することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8d1a1-110">Note that `AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 <span data-ttu-id="8d1a1-111">[!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)] [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)] [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="8d1a1-111">[!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)] [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)] [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1a1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d1a1-112">See Also</span></span>  
 <span data-ttu-id="8d1a1-113">[アプリケーション ドメインを使用したプログラミング](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="8d1a1-113">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 [<span data-ttu-id="8d1a1-114">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="8d1a1-114">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

