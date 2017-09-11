---
title: "軽減策: WPF アプリのカルチャおよびディスパッチャー操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 455c1452-8ce0-45ae-a092-21fb8edf1cac
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41fc52679884d547809f1c1e9f47e29eb668cb8e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a><span data-ttu-id="4580c-102">軽減策: WPF アプリのカルチャおよびディスパッチャー操作</span><span class="sxs-lookup"><span data-stu-id="4580c-102">Mitigation: Culture and Dispatcher Operations in WPF Apps</span></span>
<span data-ttu-id="4580c-103">.NET Framework 4.6 と .NET Framework 4.6.1 を対象とするアプリでは、<xref:System.Windows.Threading.Dispatcher> 内で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティ、または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに対して加えられた変更は、ディスパッチャー操作の最後に失われます。</span><span class="sxs-lookup"><span data-stu-id="4580c-103">In apps that target the .NET Framework 4.6 and the .NET Framework 4.6.1, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties that are made within a <xref:System.Windows.Threading.Dispatcher> are lost at the end of that dispatcher operation.</span></span> <span data-ttu-id="4580c-104">同様に、ディスパッチャー操作の外部で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> に加えられた変更は、その操作の実行時には反映されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4580c-104">Similarly, changes to <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> made outside of a dispatcher operation may not be reflected when that operation executes.</span></span>  
  
 <span data-ttu-id="4580c-105">これは、<xref:System.Threading.ExecutionContext> が変更され、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が実行コンテキストに格納されるようになったためです。</span><span class="sxs-lookup"><span data-stu-id="4580c-105">This is due to a change in <xref:System.Threading.ExecutionContext> that causes the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to be stored in the execution context.</span></span> <span data-ttu-id="4580c-106">WPF ディスパッチャー操作は、操作を開始するために使用された実行コンテキストを格納して、操作が完了したときに、以前のコンテキストを復元します。</span><span class="sxs-lookup"><span data-stu-id="4580c-106">WPF dispatcher operations store the execution context used to begin the operation and restore the previous context when the operation is completed.</span></span> <span data-ttu-id="4580c-107"><xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> がそのコンテキストの一部になったため、ディスパッチャー操作内でそれらに加えられた変更は、操作の外部では保持されません。</span><span class="sxs-lookup"><span data-stu-id="4580c-107">Because <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are now part of that context, changes to them within a dispatcher operation are not persisted outside of the operation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4580c-108">影響</span><span class="sxs-lookup"><span data-stu-id="4580c-108">Impact</span></span>  
 <span data-ttu-id="4580c-109">具体的には、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティと <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに加えられた変更は、WPF UI コールバックと WPF アプリケーション内の他のコードとの間でフローされない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4580c-109">Practically, this means that changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> properties may not flow between WPF UI callbacks and other code in a WPF application.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="4580c-110">軽減策</span><span class="sxs-lookup"><span data-stu-id="4580c-110">Mitigation</span></span>  
 <span data-ttu-id="4580c-111">この変更の影響を受けるアプリは、次のいずれかの方法で回避できます。</span><span class="sxs-lookup"><span data-stu-id="4580c-111">Apps affected by this change may work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="4580c-112">望ましい <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> をフィールドに格納し、正しい <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が設定されているすべての <xref:System.Windows.Threading.Dispatcher> 操作の本体 (UI イベントのコールバック ハンドラーを含む) をチェックインする。</span><span class="sxs-lookup"><span data-stu-id="4580c-112">By storing the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> in a field and checking in all <xref:System.Windows.Threading.Dispatcher> operation bodies (including UI event callback handlers) that the correct <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or  <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> is set.</span></span>  
  
-   <span data-ttu-id="4580c-113"><xref:System.Threading.ExecutionContext> の変更は、.NET Framework 4.6 または .NET Framework 4.6.1 を対象とする WPF アプリにのみ影響するため、対象を .NET Framework 4.5.2 とするか、4.6.2 以降のバージョンの .NET Framework を対象とすることで回避できます。</span><span class="sxs-lookup"><span data-stu-id="4580c-113">Because the change to <xref:System.Threading.ExecutionContext> only affects WPF apps that target the .NET Framework 4.6 or the .NET Framework 4.6.1, this change can be avoided by targeting the .NET Framework 4.5.2 or by targeting a version of the .NET Framework starting with 4.6.2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4580c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4580c-114">See Also</span></span>  
 [<span data-ttu-id="4580c-115">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="4580c-115">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

