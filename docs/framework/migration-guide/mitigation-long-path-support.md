---
title: "軽減策: 長いパスのサポート"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a><span data-ttu-id="a0b08-102">軽減策: 長いパスのサポート</span><span class="sxs-lookup"><span data-stu-id="a0b08-102">Mitigation: Long Path Support</span></span>
<span data-ttu-id="a0b08-103">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降を対象とするアプリでは、パスまたは完全修飾ファイル名が 260 (または `MAX_PATH`) 文字を超える場合、ファイル システムの I/O メソッドで自動的に <xref:System.IO.PathTooLongException> がスローされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a0b08-103">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)],  file system I/O methods not longer automatically throw a <xref:System.IO.PathTooLongException> if a path or fully qualified file name exceeds 260 (or `MAX_PATH`) characters.</span></span> <span data-ttu-id="a0b08-104">代わりに、最大 32K の文字の長いパスがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a0b08-104">Instead, long paths of up to 32K characters are supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a0b08-105">影響</span><span class="sxs-lookup"><span data-stu-id="a0b08-105">Impact</span></span>  
 <span data-ttu-id="a0b08-106">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象として再コンパイルされたアプリのうち、パスが 260 文字を超えたために以前は <xref:System.IO.PathTooLongException> を自動的にスローしていたアプリが、次の条件下でのみ <xref:System.IO.PathTooLongException> をスローするようになります。</span><span class="sxs-lookup"><span data-stu-id="a0b08-106">Apps recompiled to target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] and that previously threw a <xref:System.IO.PathTooLongException> automatically because a path exceeded 260 characters will now throw a <xref:System.IO.PathTooLongException> only under the following conditions:</span></span>  
  
-   <span data-ttu-id="a0b08-107">パスの長さが <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) 文字を超えている。</span><span class="sxs-lookup"><span data-stu-id="a0b08-107">The length of the path is greater than  <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) characters.</span></span>  
  
-   <span data-ttu-id="a0b08-108">オペレーティング システムが `COR_E_PATHTOOLONG` またはそれと同等のものを返す。</span><span class="sxs-lookup"><span data-stu-id="a0b08-108">The operating system returns `COR_E_PATHTOOLONG` or its equivalent.</span></span>  
  
 <span data-ttu-id="a0b08-109">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前を対象とするアプリの従来の動作では、パスが 260 文字を超えるたびにランタイムで自動的に <xref:System.IO.PathTooLongException> がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="a0b08-109">The legacy behavior for apps that target the[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier is that the runtime automatically throws a <xref:System.IO.PathTooLongException> whenever a path exceeds 260 characters.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a0b08-110">軽減策</span><span class="sxs-lookup"><span data-stu-id="a0b08-110">Mitigation</span></span>  
 <span data-ttu-id="a0b08-111">[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリでは、長いパスのサポートが望ましくない場合、app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することでサポートを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a0b08-111">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], you can opt out of long path support if it is not desirable by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 <span data-ttu-id="a0b08-112">以前のバージョンの .NET Framework を対象とするものの、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降で実行されているアプリでは、app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することで、長いパスのサポートを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="a0b08-112">For apps that target earlier versions of the .NET Framework but run on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later., you can opt in to long path support by adding the following to    to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0b08-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0b08-113">See Also</span></span>  
 [<span data-ttu-id="a0b08-114">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="a0b08-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

