---
title: "型 &quot;&lt;typename&gt;&quot; コンス トラクターを持たない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30251
- vbc30251
dev_langs:
- VB
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
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
ms.openlocfilehash: 6348f774971ebbe8657910989e021f7c01cdf867
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-39lttypenamegt39-has-no-constructors"></a><span data-ttu-id="62146-102">型 '&lt;typename&gt;' コンス トラクターがありません</span><span class="sxs-lookup"><span data-stu-id="62146-102">Type &#39;&lt;typename&gt;&#39; has no constructors</span></span>
<span data-ttu-id="62146-103">型が `Sub New()` の呼び出しをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="62146-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="62146-104">コンパイラまたはバイナリ ファイルが破損していることが原因の&1; つとして考えられます。</span><span class="sxs-lookup"><span data-stu-id="62146-104">One possible cause is a corrupted compiler or binary file.</span></span>  
  
 <span data-ttu-id="62146-105">**エラー ID:** BC30251</span><span class="sxs-lookup"><span data-stu-id="62146-105">**Error ID:** BC30251</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62146-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="62146-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="62146-107">型が別のプロジェクトまたは参照ファイル内にある場合は、プロジェクトまたはファイルを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="62146-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>  
  
2.  <span data-ttu-id="62146-108">型が同じプロジェクト内にある場合は、型を含むアセンブリを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="62146-108">If the type is in the same project, recompile the assembly containing the type.</span></span>  
  
3.  <span data-ttu-id="62146-109">エラーがまだ発生する場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="62146-109">If the error recurs, reinstall the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler.</span></span>  
  
4.  <span data-ttu-id="62146-110">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="62146-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62146-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="62146-111">See Also</span></span>  
 <span data-ttu-id="62146-112">[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="62146-112">[Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="62146-113"> [ご意見](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="62146-113"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
