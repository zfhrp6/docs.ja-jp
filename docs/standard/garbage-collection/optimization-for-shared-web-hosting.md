---
title: "共有 Web ホストの最適化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="f9da2-102">共有 Web ホストの最適化</span><span class="sxs-lookup"><span data-stu-id="f9da2-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="f9da2-103">複数の小規模 Web サイトをホストすることにより共有されているサーバーの管理者がいる場合は、パフォーマンスを最適化し、次を追加することによってサイト容量を増やす`gcTrimCommitOnLowMemory`設定、 `runtime` .net Aspnet.config ファイル内のノードディレクトリ:</span><span class="sxs-lookup"><span data-stu-id="f9da2-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="f9da2-104">この設定は推奨のみ共有 Web をホスティングのシナリオです。</span><span class="sxs-lookup"><span data-stu-id="f9da2-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="f9da2-105">ガベージ コレクターは、将来の割り当て用のメモリを保持しているためにより厳密に必要なものをコミットされた領域にできます。</span><span class="sxs-lookup"><span data-stu-id="f9da2-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="f9da2-106">時刻を格納するには、この領域を減らすことができますが、システム メモリの負荷が高い場合。</span><span class="sxs-lookup"><span data-stu-id="f9da2-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="f9da2-107">このコミットされた領域を減らすことにより、パフォーマンスが向上しより多くのサイトをホストする能力を展開します。</span><span class="sxs-lookup"><span data-stu-id="f9da2-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="f9da2-108">ときに、`gcTrimCommitOnLowMemory`設定が有効になっていると、ガベージ コレクターは、システム メモリの負荷を評価し、負荷が 90% に達すると、トリミング モードに入ります。</span><span class="sxs-lookup"><span data-stu-id="f9da2-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="f9da2-109">負荷が 85% を未満になるまで、トリミング モードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="f9da2-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="f9da2-110">条件は次の許可、ガベージ コレクター場合ことができますを`gcTrimCommitOnLowMemory`設定されず、現在のアプリケーションのヘルプ、それを無視します。</span><span class="sxs-lookup"><span data-stu-id="f9da2-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9da2-111">例</span><span class="sxs-lookup"><span data-stu-id="f9da2-111">Example</span></span>  
 <span data-ttu-id="f9da2-112">次の XML フラグメントが有効にする方法を示しています、`gcTrimCommitOnLowMemory`設定します。</span><span class="sxs-lookup"><span data-stu-id="f9da2-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="f9da2-113">省略記号ボタンを示すようになります。 その他の設定、`runtime`ノード。</span><span class="sxs-lookup"><span data-stu-id="f9da2-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9da2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9da2-114">See Also</span></span>  
 [<span data-ttu-id="f9da2-115">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="f9da2-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
