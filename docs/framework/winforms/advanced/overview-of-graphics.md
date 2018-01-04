---
title: "グラフィックスについて"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3438fe2f1c3a6fc40efda0ff2583208f38bf7d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-graphics"></a><span data-ttu-id="d9e76-102">グラフィックスについて</span><span class="sxs-lookup"><span data-stu-id="d9e76-102">Overview of Graphics</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d9e76-103">Microsoft Windows オペレーティング システムのサブシステムを形成する、アプリケーション プログラミング インターフェイス (API)。</span><span class="sxs-lookup"><span data-stu-id="d9e76-103"> is an application programming interface (API) that forms the subsystem of the Microsoft Windows operating system.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d9e76-104">画面およびプリンターの情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="d9e76-104"> is responsible for displaying information on screens and printers.</span></span> <span data-ttu-id="d9e76-105">その名前からわかるように、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] の後継であり、以前のバージョンの Windows に含まれているグラフィックス デバイス インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d9e76-105">As its name suggests, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is the successor to [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)], the Graphics Device Interface included with earlier versions of Windows.</span></span>  
  
## <a name="managed-class-interface"></a><span data-ttu-id="d9e76-106">マネージ クラスのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9e76-106">Managed Class Interface</span></span>  
 <span data-ttu-id="d9e76-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API は、一連のマネージ コードとして展開されているクラスを通じて公開されます。</span><span class="sxs-lookup"><span data-stu-id="d9e76-107">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API is exposed through a set of classes deployed as managed code.</span></span> <span data-ttu-id="d9e76-108">このクラスのセットと呼ばれる、*マネージ クラスのインターフェイス*に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d9e76-108">This set of classes is called the *managed class interface* to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="d9e76-109">次の名前空間は、マネージ クラスのインターフェイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="d9e76-109">The following namespaces make up the managed class interface:</span></span>  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 <span data-ttu-id="d9e76-110">グラフィックス デバイス インターフェイスを備えたなど[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、画面またはプリンターの情報を表示するには、特定のディスプレイ デバイスの詳細について考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d9e76-110">With a Graphics Device Interface, such as [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can display information on a screen or printer without having to be concerned about the details of a particular display device.</span></span> <span data-ttu-id="d9e76-111">プログラマは [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] クラスによって提供されるさまざまなメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d9e76-111">The programmer makes calls to methods provided by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span> <span data-ttu-id="d9e76-112">次に、これらのメソッドで、特定のデバイス ドライバーへの適切な呼び出しを実行します。</span><span class="sxs-lookup"><span data-stu-id="d9e76-112">Those methods, in turn, make the appropriate calls to specific device drivers.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="d9e76-113"> は、グラフィックス ハードウェアからアプリケーションを分離します。</span><span class="sxs-lookup"><span data-stu-id="d9e76-113"> insulates the application from the graphics hardware.</span></span> <span data-ttu-id="d9e76-114">このデバイスに依存しないアプリケーションを作成するプログラマができるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="d9e76-114">It is this insulation that enables a programmer to create device-independent applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e76-115">参照</span><span class="sxs-lookup"><span data-stu-id="d9e76-115">See Also</span></span>  
 [<span data-ttu-id="d9e76-116">グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="d9e76-116">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)
