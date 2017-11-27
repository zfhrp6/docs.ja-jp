---
title: "方法: アセンブリ共有する他のアプリケーション (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 491791ba9b6f0cf6da86a160eddf8e78109b11c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="83143-102">方法: アセンブリ共有する他のアプリケーション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83143-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="83143-103">アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。</span><span class="sxs-lookup"><span data-stu-id="83143-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="83143-104">他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ](../../../../framework/app-domains/gac.md) (GAC) にアセンブリを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="83143-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="83143-105">アセンブリの共有</span><span class="sxs-lookup"><span data-stu-id="83143-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="83143-106">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="83143-106">Create your assembly.</span></span> <span data-ttu-id="83143-107">詳しくは、「[アセンブリの作成](../../../../framework/app-domains/create-assemblies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83143-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="83143-108">アセンブリに厳密な名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="83143-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="83143-109">詳しくは、「[方法 : 厳密な名前でアセンブリに署名する](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83143-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="83143-110">アセンブリにバージョン情報を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="83143-110">Assign version information to your assembly.</span></span> <span data-ttu-id="83143-111">詳細については、「[アセンブリのバージョン管理](https://msdn.microsoft.com/library/51ket42z)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83143-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="83143-112">グローバル アセンブリ キャッシュにアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="83143-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="83143-113">詳しくは、「[方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83143-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="83143-114">他のアプリケーションからアセンブリに含まれる型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="83143-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="83143-115">詳しくは、「[方法 : 厳密な名前のアセンブリを参照する](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="83143-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83143-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="83143-116">See Also</span></span>  
 <span data-ttu-id="83143-117">[プログラミングに関する概念](../../../../visual-basic/programming-guide/concepts/index.md)[アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="83143-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="83143-118">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="83143-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
