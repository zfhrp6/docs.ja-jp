---
title: "方法: アセンブリを他のアプリケーション (Visual Basic) に共有 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ceebb3934c269284db18c9ca8e561417eaf5baa1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="7b01c-102">方法: アセンブリを他のアプリケーション (Visual Basic) と共有</span><span class="sxs-lookup"><span data-stu-id="7b01c-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="7b01c-103">アセンブリがプライベートまたは共有することができます。 既定では、ほとんどの単純なプログラムで構成されているプライベート アセンブリの他のアプリケーションで使用されるこれらの目的ではありませんので。</span><span class="sxs-lookup"><span data-stu-id="7b01c-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="7b01c-104">他のアプリケーションとアセンブリを共有するために配置する必要があります、[グローバル アセンブリ キャッシュ](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)(GAC)。</span><span class="sxs-lookup"><span data-stu-id="7b01c-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="7b01c-105">アセンブリの共有</span><span class="sxs-lookup"><span data-stu-id="7b01c-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="7b01c-106">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-106">Create your assembly.</span></span> <span data-ttu-id="7b01c-107">詳細については、次を参照してください。[アセンブリの作成](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4)します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-107">For more information, see [Creating Assemblies](http://msdn.microsoft.com/library/54832ee9-dca8-4c8b-913c-c0b9d265e9a4).</span></span>  
  
2.  <span data-ttu-id="7b01c-108">アセンブリに厳密な名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7b01c-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="7b01c-109">詳細については、次を参照してください。[方法: 厳密な名前でアセンブリに署名](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-109">For more information, see [How to: Sign an Assembly with a Strong Name](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).</span></span>  
  
3.  <span data-ttu-id="7b01c-110">アセンブリにバージョン情報を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7b01c-110">Assign version information to your assembly.</span></span> <span data-ttu-id="7b01c-111">詳細については、次を参照してください。[アセンブリのバージョン管理](https://msdn.microsoft.com/library/51ket42z)します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="7b01c-112">アセンブリをグローバル アセンブリ キャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="7b01c-113">詳細については、次を参照してください。[方法: グローバル アセンブリ キャッシュにアセンブリをインストール](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743)します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](http://msdn.microsoft.com/library/a7e6f091-d02c-49ba-b736-7295cb0eb743).</span></span>  
  
5.  <span data-ttu-id="7b01c-114">他のアプリケーションからアセンブリに含まれる型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7b01c-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="7b01c-115">詳細については、次を参照してください。[方法: 厳密な名前付きアセンブリを参照](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)します。</span><span class="sxs-lookup"><span data-stu-id="7b01c-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b01c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b01c-116">See Also</span></span>  
 <span data-ttu-id="7b01c-117">[プログラミングに関する概念](../../../../visual-basic/programming-guide/concepts/index.md)
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b01c-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)
 [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="7b01c-118"> [アセンブリを使用したプログラミング](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)</span><span class="sxs-lookup"><span data-stu-id="7b01c-118"> [Programming with Assemblies](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)</span></span>
