---
title: "方法 : アプリケーション ドメインをアンロードする"
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
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eefaf670202e6b4977d75fffa906f1b07053eb3e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="676a2-102">方法 : アプリケーション ドメインをアンロードする</span><span class="sxs-lookup"><span data-stu-id="676a2-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="676a2-103">アプリケーション ドメインの使用が完了したら、<xref:System.AppDomain.Unload%2A?displayProperty=fullName> メソッドを使用してアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="676a2-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="676a2-104">**Unload** メソッドは、指定したアプリケーション ドメインを正常にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="676a2-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="676a2-105">アンロード プロセス中は、新たなスレッドがアプリケーション ドメインにアクセスすることはできません。また、アプリケーション ドメイン固有のデータ構造はすべて解放されます。</span><span class="sxs-lookup"><span data-stu-id="676a2-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="676a2-106">アプリケーション ドメインに読み込まれたアセンブリは、削除され、以後は使用できません。</span><span class="sxs-lookup"><span data-stu-id="676a2-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="676a2-107">アプリケーション ドメイン内のアセンブリが、ドメインに中立である場合、アセンブリのデータは、プロセス全体がシャットダウンされるまでメモリに残ります。</span><span class="sxs-lookup"><span data-stu-id="676a2-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="676a2-108">プロセス全体をシャットダウンする以外に、ドメインに中立なアセンブリをアンロードする機構はありません。</span><span class="sxs-lookup"><span data-stu-id="676a2-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="676a2-109">アプリケーション ドメインのアンロード要求が機能しない場合は、<xref:System.CannotUnloadAppDomainException> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="676a2-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="676a2-110">次の例では、`MyDomain` という新しいアプリケーション ドメインを作成し、情報をコンソールに出力してから、アプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="676a2-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="676a2-111">このコードは、アンロードされたアプリケーション ドメインのフレンドリ名をコンソールに出力しようとすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="676a2-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="676a2-112">このアクションでは、例外が生成されます。この例外は、プログラムの最後の try ステートメントまたは catch ステートメントで処理されます。</span><span class="sxs-lookup"><span data-stu-id="676a2-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="676a2-113">例</span><span class="sxs-lookup"><span data-stu-id="676a2-113">Example</span></span>  
 <span data-ttu-id="676a2-114">[!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="676a2-114">[!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)] [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)] [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676a2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="676a2-115">See Also</span></span>  
 <span data-ttu-id="676a2-116">[アプリケーション ドメインを使用したプログラミング](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="676a2-116">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 <span data-ttu-id="676a2-117">[方法: アプリケーション ドメインを作成する](../../../docs/framework/app-domains/how-to-create-an-application-domain.md) </span><span class="sxs-lookup"><span data-stu-id="676a2-117">[How to: Create an Application Domain](../../../docs/framework/app-domains/how-to-create-an-application-domain.md) </span></span>  
 [<span data-ttu-id="676a2-118">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="676a2-118">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)

