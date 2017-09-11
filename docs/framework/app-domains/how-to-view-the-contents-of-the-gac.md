---
title: "方法 : グローバル アセンブリ キャッシュの内容を表示する"
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
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 55ed52873b6fa944c3dd5d95066432f593719c2e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="d5ae8-102">方法 : グローバル アセンブリ キャッシュの内容を表示する</span><span class="sxs-lookup"><span data-stu-id="d5ae8-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="d5ae8-103">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用すると、グローバル アセンブリ キャッシュの内容を表示できます。</span><span class="sxs-lookup"><span data-stu-id="d5ae8-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="d5ae8-104">グローバル アセンブリ キャッシュ内のアセンブリの一覧を表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="d5ae8-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="d5ae8-105">[Visual Studio コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)で次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d5ae8-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="d5ae8-106">**gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="d5ae8-106">**gacutil -l** </span></span>  
     <span data-ttu-id="d5ae8-107">または</span><span class="sxs-lookup"><span data-stu-id="d5ae8-107">-or-</span></span>  
    <span data-ttu-id="d5ae8-108">**gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="d5ae8-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="d5ae8-109">以前のバージョンの .NET Framework では、Windows のシェル拡張機能である [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) により、エクスプローラーでグローバル アセンブリ キャッシュを表示することができました。</span><span class="sxs-lookup"><span data-stu-id="d5ae8-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="d5ae8-110">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、Shfusion.dll は廃止されましたが、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="d5ae8-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ae8-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5ae8-111">See Also</span></span>  
 <span data-ttu-id="d5ae8-112">[アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="d5ae8-112">[Working with Assemblies and the Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
 [<span data-ttu-id="d5ae8-113">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="d5ae8-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)

