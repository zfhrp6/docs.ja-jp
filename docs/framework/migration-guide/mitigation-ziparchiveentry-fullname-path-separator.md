---
title: "軽減策: ZipArchiveEntry.FullName パスの区切り文字"
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
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ca43e4952f7ff457cf61c2c36334ab6213e50ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a><span data-ttu-id="17d7f-102">軽減策: ZipArchiveEntry.FullName パスの区切り文字</span><span class="sxs-lookup"><span data-stu-id="17d7f-102">Mitigation: ZipArchiveEntry.FullName Path Separator</span></span>
<span data-ttu-id="17d7f-103">[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降を対象とするアプリでは、<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> プロパティで使用されるパスの区切り文字は、以前のバージョンの .NET Framework で使用されていた円記号 ("\\") からスラッシュ ("/") に変更されました。</span><span class="sxs-lookup"><span data-stu-id="17d7f-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], the path separator used in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property has changed from the backslash ("\\") used in previous versions of the .NET Framework to a forward slash ("/").</span></span>   <span data-ttu-id="17d7f-104"><xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> メソッドのオーバーロードのいずれかを呼び出すことで、<xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="17d7f-104"><xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> objects are created by calling one of the overloads of the <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="17d7f-105">影響</span><span class="sxs-lookup"><span data-stu-id="17d7f-105">Impact</span></span>  
 <span data-ttu-id="17d7f-106">この変更によって、.NET の実装が [.ZIP ファイル形式の仕様](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)のセクション 4.4.17.1 に準拠するようになったほか、Windows 以外のシステムで ZIP アーカイブを圧縮解除できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="17d7f-106">The change brings the .NET implementation into conformity with section 4.4.17.1 of the [.ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) and allows .ZIP archives to be decompressed on non-Windows systems.</span></span>  
  
 <span data-ttu-id="17d7f-107">Macintosh などの Windows 以外のオペレーティング システムで以前のバージョンの .NET Framework を対象とするアプリで作成された zip ファイルを圧縮解除すると、ディレクトリ構造を保持できません。</span><span class="sxs-lookup"><span data-stu-id="17d7f-107">Decompressing a zip file created  by an app that targets a previous version of the .NET Framework on non-Windows operating systems such as the Macintosh fails to preserve the directory structure.</span></span> <span data-ttu-id="17d7f-108">たとえば、Macintosh で、ディレクトリ パスとファイル名が円記号 ("\\") 文字で連結された名前を持つ一連のファイルを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="17d7f-108">For example, on the Macintosh, it creates a set of files whose filename concatenates the directory path, along with any backslash ("\\") characters, and the filename.</span></span> <span data-ttu-id="17d7f-109">その場合、圧縮解除されたファイルのディレクトリ構造は保持されません。</span><span class="sxs-lookup"><span data-stu-id="17d7f-109">As a result, the directory structure of decompressed files is not preserved.</span></span>  
  
 <span data-ttu-id="17d7f-110">.NET Framework <xref:System.IO> 名前空間の API によって、Windows オペレーティング システムで展開される .zip ファイルでは、この変更の影響は最小限になるはずです。これらの API では、スラッシュ ("/") または円記号 ("\\") をパスの区切り文字としてシームレスに処理できるためです。</span><span class="sxs-lookup"><span data-stu-id="17d7f-110">The impact of this change on .ZIP files that are decompressed on the Windows operating system by APIs in the .NET Framework <xref:System.IO> namespace should be minimal, since these APIs can seamlessly handle either a slash ("/") or a backslash ("\\") as the path separator character.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="17d7f-111">軽減策</span><span class="sxs-lookup"><span data-stu-id="17d7f-111">Mitigation</span></span>  
 <span data-ttu-id="17d7f-112">この動作が望ましくない場合は、アプリケーション構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="17d7f-112">If this behavior is undesirable, you can opt out of by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="17d7f-113">以下は、`<runtime>` セクションと無効への切り替えの両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="17d7f-113">The following shows both the `<runtime>` section and the opt-out switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 <span data-ttu-id="17d7f-114">また、以前のバージョンの .NET Framework を対象とするものの、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降のバージョンで実行されているアプリでは、アプリケーション構成ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに構成設定を追加して、この動作を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="17d7f-114">In addition, apps that target previous versions of the .NET Framework but are running on the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding a configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file.</span></span> <span data-ttu-id="17d7f-115">以下は、`<runtime>` セクションと有効への切り替えの両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="17d7f-115">The following shows both the `<runtime>` section and the opt-in switch.</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17d7f-116">参照</span><span class="sxs-lookup"><span data-stu-id="17d7f-116">See Also</span></span>  
 [<span data-ttu-id="17d7f-117">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="17d7f-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)  
 [<span data-ttu-id="17d7f-118">4.6.1 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="17d7f-118">Application Compatibility in 4.6.1</span></span>](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
