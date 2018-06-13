---
title: '方法 : アプリケーション ドメインをアンロードする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a9e5ee865b5e0ac9ec0214a4a0b5194bbcd9f30
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742089"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="f31c5-102">方法 : アプリケーション ドメインをアンロードする</span><span class="sxs-lookup"><span data-stu-id="f31c5-102">How to: Unload an Application Domain</span></span>
<span data-ttu-id="f31c5-103">アプリケーション ドメインの使用が完了したら、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドを使用してアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="f31c5-103">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f31c5-104">**Unload** メソッドは、指定したアプリケーション ドメインを正常にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="f31c5-104">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="f31c5-105">アンロード プロセス中は、新たなスレッドがアプリケーション ドメインにアクセスすることはできません。また、アプリケーション ドメイン固有のデータ構造はすべて解放されます。</span><span class="sxs-lookup"><span data-stu-id="f31c5-105">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="f31c5-106">アプリケーション ドメインに読み込まれたアセンブリは、削除され、以後は使用できません。</span><span class="sxs-lookup"><span data-stu-id="f31c5-106">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="f31c5-107">アプリケーション ドメイン内のアセンブリが、ドメインに中立である場合、アセンブリのデータは、プロセス全体がシャットダウンされるまでメモリに残ります。</span><span class="sxs-lookup"><span data-stu-id="f31c5-107">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="f31c5-108">プロセス全体をシャットダウンする以外に、ドメインに中立なアセンブリをアンロードする機構はありません。</span><span class="sxs-lookup"><span data-stu-id="f31c5-108">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="f31c5-109">アプリケーション ドメインのアンロード要求が機能しない場合は、<xref:System.CannotUnloadAppDomainException> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f31c5-109">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="f31c5-110">次の例では、`MyDomain` という新しいアプリケーション ドメインを作成し、情報をコンソールに出力してから、アプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="f31c5-110">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="f31c5-111">このコードは、アンロードされたアプリケーション ドメインのフレンドリ名をコンソールに出力しようとすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f31c5-111">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="f31c5-112">このアクションでは、例外が生成されます。この例外は、プログラムの最後の try ステートメントまたは catch ステートメントで処理されます。</span><span class="sxs-lookup"><span data-stu-id="f31c5-112">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f31c5-113">例</span><span class="sxs-lookup"><span data-stu-id="f31c5-113">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f31c5-114">参照</span><span class="sxs-lookup"><span data-stu-id="f31c5-114">See Also</span></span>  
 [<span data-ttu-id="f31c5-115">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="f31c5-115">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)  
 [<span data-ttu-id="f31c5-116">方法: アプリケーション ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="f31c5-116">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [<span data-ttu-id="f31c5-117">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="f31c5-117">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
