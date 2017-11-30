---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="38705-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38705-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="38705-103">ソース ファイルの先頭にある属性がアセンブリ全体に適用されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="38705-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38705-104">コメント</span><span class="sxs-lookup"><span data-stu-id="38705-104">Remarks</span></span>  
 <span data-ttu-id="38705-105">多くの属性は、クラスやプロパティなどの個別のプログラミング要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="38705-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="38705-106">山かっこ内で、属性ブロックをアタッチすることによってこのような属性を適用する (`< >`)、宣言ステートメントに直接できます。</span><span class="sxs-lookup"><span data-stu-id="38705-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="38705-107">ソース ファイルの先頭に、属性ブロックを配置しを持つ属性を識別属性は、次の要素だけでなく、アセンブリ全体を示し場合、`Assembly`キーワード。</span><span class="sxs-lookup"><span data-stu-id="38705-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="38705-108">使用するには、現在のアセンブリ モジュールに適用する場合、[モジュール](../../../visual-basic/language-reference/modifiers/module-keyword.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="38705-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="38705-109">できますも属性を適用する AssemblyInfo.vb ファイルでアセンブリに後者がありません、メインのソース コード ファイルで属性ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="38705-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38705-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="38705-110">See Also</span></span>  
 [<span data-ttu-id="38705-111">Module \<キーワード></span><span class="sxs-lookup"><span data-stu-id="38705-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="38705-112">属性の概要</span><span class="sxs-lookup"><span data-stu-id="38705-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

