---
title: "アセンブリ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
dev_langs:
- VB
helpviewer_keywords:
- Assembly modifier
- Assembly keyword
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b83102c24c80b7ee6ec4c0ffc4a446e26b7811cf
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="assembly-visual-basic"></a><span data-ttu-id="1ab84-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ab84-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="1ab84-103">ソース ファイルの先頭にある属性がアセンブリ全体に適用されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ab84-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ab84-104">コメント</span><span class="sxs-lookup"><span data-stu-id="1ab84-104">Remarks</span></span>  
 <span data-ttu-id="1ab84-105">多くの属性は、クラスやプロパティなどの個別のプログラミング要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="1ab84-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="1ab84-106">山かっこ内の属性ブロックをアタッチすることによってこのような属性を適用する (`< >`)、宣言のステートメントに直接します。</span><span class="sxs-lookup"><span data-stu-id="1ab84-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="1ab84-107">属性ブロックをソース ファイルの先頭に配置して、この属性を識別属性が次の要素だけでなく、アセンブリ全体に関係している場合、`Assembly`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="1ab84-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="1ab84-108">使用するには、現在のアセンブリのモジュールに適用する場合、[モジュール](../../../visual-basic/language-reference/modifiers/module-keyword.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="1ab84-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="1ab84-109">適用できます属性 AssemblyInfo.vb ファイルでアセンブリにあり場合する、主要なソース コード ファイルで属性ブロックを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1ab84-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab84-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ab84-110">See Also</span></span>  
 <span data-ttu-id="1ab84-111">[モジュール\<キーワード >](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span><span class="sxs-lookup"><span data-stu-id="1ab84-111">[Module \<keyword>](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span></span>  
<span data-ttu-id="1ab84-112"> [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="1ab84-112"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span></span>


