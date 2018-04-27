---
title: アセンブリに必要な参照&#39; &lt;assemblyname&gt; &#39;基本クラスを含む&#39; &lt;classname&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6dd53e2d0bf0535de50e465293edb26a5b1d484
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a><span data-ttu-id="d47e3-102">アセンブリに必要な参照&#39; &lt;assemblyname&gt; &#39;基本クラスを含む&#39; &lt;classname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="d47e3-102">Reference required to assembly &#39;&lt;assemblyname&gt;&#39; containing the base class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="d47e3-103">参照アセンブリが必要です '\<assemblyname >' を含む基底クラスの\<classname >' です。</span><span class="sxs-lookup"><span data-stu-id="d47e3-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="d47e3-104">プロジェクトに参照を追加してください。</span><span class="sxs-lookup"><span data-stu-id="d47e3-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="d47e3-105">プロジェクト内で直接参照されないダイナミック リンク ライブラリ (DLL) またはアセンブリでクラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="d47e3-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="d47e3-106">Visual Basic コンパイラでは、クラスが 1 つ以上の DLL またはアセンブリで定義されている場合に備えて、あいまいさを避けるためへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="d47e3-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="d47e3-107">**エラー ID:** BC30007</span><span class="sxs-lookup"><span data-stu-id="d47e3-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d47e3-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d47e3-108">To correct this error</span></span>  
  
-   <span data-ttu-id="d47e3-109">参照されない DLL またはアセンブリの名前をプロジェクト参照に含めます。</span><span class="sxs-lookup"><span data-stu-id="d47e3-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47e3-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d47e3-110">See Also</span></span>  
   
 [<span data-ttu-id="d47e3-111">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="d47e3-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="d47e3-112">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d47e3-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
