---
title: "方法 : アセンブリを他のアプリケーションと共有する (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 85117cfdc9b12a93891e89727412a03acc83289b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="391a0-102">方法 : アセンブリを他のアプリケーションと共有する (C#)</span><span class="sxs-lookup"><span data-stu-id="391a0-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="391a0-103">アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。</span><span class="sxs-lookup"><span data-stu-id="391a0-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="391a0-104">他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ](../../../../framework/app-domains/gac.md) (GAC) にアセンブリを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="391a0-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="391a0-105">アセンブリの共有</span><span class="sxs-lookup"><span data-stu-id="391a0-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="391a0-106">アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="391a0-106">Create your assembly.</span></span> <span data-ttu-id="391a0-107">詳しくは、「[アセンブリの作成](../../../../framework/app-domains/create-assemblies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="391a0-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="391a0-108">アセンブリに厳密な名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="391a0-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="391a0-109">詳しくは、「[方法 : 厳密な名前でアセンブリに署名する](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="391a0-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="391a0-110">アセンブリにバージョン情報を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="391a0-110">Assign version information to your assembly.</span></span> <span data-ttu-id="391a0-111">詳細については、「[アセンブリのバージョン管理](https://msdn.microsoft.com/library/51ket42z)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="391a0-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="391a0-112">グローバル アセンブリ キャッシュにアセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="391a0-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="391a0-113">詳しくは、「[方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="391a0-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="391a0-114">他のアプリケーションからアセンブリに含まれる型にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="391a0-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="391a0-115">詳しくは、「[方法 : 厳密な名前のアセンブリを参照する](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="391a0-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="391a0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="391a0-116">See Also</span></span>  
 <span data-ttu-id="391a0-117">[C# プログラミング ガイド](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="391a0-117">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="391a0-118">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="391a0-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)

