---
title: '方法 : グローバル アセンブリ キャッシュの内容を表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e582f86eac03a51437b965f87f1bc7f29294eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="383bf-102">方法 : グローバル アセンブリ キャッシュの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="383bf-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="383bf-103">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用すると、グローバル アセンブリ キャッシュの内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="383bf-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="383bf-104">グローバル アセンブリ キャッシュ内のアセンブリの一覧を表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="383bf-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="383bf-105">[Visual Studio コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)で次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="383bf-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="383bf-106">**gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="383bf-106">**gacutil -l** </span></span>  
     <span data-ttu-id="383bf-107">- または -</span><span class="sxs-lookup"><span data-stu-id="383bf-107">-or-</span></span>  
    <span data-ttu-id="383bf-108">**gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="383bf-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="383bf-109">以前のバージョンの .NET Framework では、Windows のシェル拡張機能である [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) により、エクスプローラーでグローバル アセンブリ キャッシュを表示することができました。</span><span class="sxs-lookup"><span data-stu-id="383bf-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="383bf-110">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、Shfusion.dll は廃止されましたが、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="383bf-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383bf-111">参照</span><span class="sxs-lookup"><span data-stu-id="383bf-111">See Also</span></span>  
 [<span data-ttu-id="383bf-112">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="383bf-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="383bf-113">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="383bf-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
