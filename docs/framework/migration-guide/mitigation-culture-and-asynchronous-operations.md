---
title: "軽減策: カルチャおよび非同期操作"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: debcae8281c832d2815e1b9896fbbcb725c8ffc3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a><span data-ttu-id="a360e-102">軽減策: カルチャおよび非同期操作</span><span class="sxs-lookup"><span data-stu-id="a360e-102">Mitigation: Culture and Asynchronous Operations</span></span>
<span data-ttu-id="a360e-103">[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降のバージョンを対象とするアプリの場合、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> はスレッドの <xref:System.Threading.ExecutionContext> に格納され、非同期操作全体にフローします。</span><span class="sxs-lookup"><span data-stu-id="a360e-103">For apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later versions, <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are stored in a thread's <xref:System.Threading.ExecutionContext>, which flows across asynchronous operations.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a360e-104">影響</span><span class="sxs-lookup"><span data-stu-id="a360e-104">Impact</span></span>  
 <span data-ttu-id="a360e-105">この変更の結果、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が変更されると、後で非同期に実行されるタスクに反映されるようになります。</span><span class="sxs-lookup"><span data-stu-id="a360e-105">As a result of this change, changes to the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> are reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="a360e-106">これは、以前のバージョンの .NET Framework の動作とは異なります。以前のバージョンでは、すべての非同期タスクで <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> はシステムの既定値にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="a360e-106">This differs from the behavior of previous .NET Framework versions, which would reset <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> to the system default  in all asynchronous tasks.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a360e-107">軽減策</span><span class="sxs-lookup"><span data-stu-id="a360e-107">Mitigation</span></span>  
 <span data-ttu-id="a360e-108">この変更の影響を受けるアプリは、次のいずれかの方法で回避できます。</span><span class="sxs-lookup"><span data-stu-id="a360e-108">Apps affected by this change can work around it in either of two ways:</span></span>  
  
-   <span data-ttu-id="a360e-109">非同期タスクの最初の操作として、必要な <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティを明示的に設定する。</span><span class="sxs-lookup"><span data-stu-id="a360e-109">By explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> property as the first operation in an asynchronous task.</span></span>  
  
-   <span data-ttu-id="a360e-110">次の `AppContextSwitchOverrides` 要素をアプリケーションの構成ファイルに追加することで、フローしない <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> の旧バージョンの動作を選択する。</span><span class="sxs-lookup"><span data-stu-id="a360e-110">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by adding the following `AppContextSwitchOverrides` element to the application's configuration file:</span></span>  
  
    ```xml  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="a360e-111">次の互換性スイッチをプログラムで設定することで、フローしない <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> の旧バージョンの動作を選択する。</span><span class="sxs-lookup"><span data-stu-id="a360e-111">By opting into the old behavior of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> by setting the following compatibility switch programatically:</span></span>  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a360e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a360e-112">See Also</span></span>  
 [<span data-ttu-id="a360e-113">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="a360e-113">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

