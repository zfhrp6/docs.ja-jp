---
title: "#Region ディレクティブ |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
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
ms.openlocfilehash: 86b8e9ce99a8c12e290f5efdc5a5c4da57f350d9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="region-directive"></a>#<span data-ttu-id="e7621-102">Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="e7621-102">Region Directive</span></span>
<span data-ttu-id="e7621-103">Visual Basic ファイルのコードのセクションを折りたたんで非表示にします。</span><span class="sxs-lookup"><span data-stu-id="e7621-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7621-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7621-104">Syntax</span></span>  
  
```  
  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="e7621-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="e7621-105">Parts</span></span>  
  
|<span data-ttu-id="e7621-106">用語</span><span class="sxs-lookup"><span data-stu-id="e7621-106">Term</span></span>|<span data-ttu-id="e7621-107">定義</span><span class="sxs-lookup"><span data-stu-id="e7621-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="e7621-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="e7621-108">Required.</span></span> <span data-ttu-id="e7621-109">領域が折りたたまれたときにその領域のタイトルとして機能する文字列です。</span><span class="sxs-lookup"><span data-stu-id="e7621-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="e7621-110">既定では、領域は折りたたまれています。</span><span class="sxs-lookup"><span data-stu-id="e7621-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="e7621-111">`#Region` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="e7621-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7621-112">コメント</span><span class="sxs-lookup"><span data-stu-id="e7621-112">Remarks</span></span>  
 <span data-ttu-id="e7621-113">Visual Studio コード エディターのアウトライン機能を使うときに展開または折りたたみの対象となるコード ブロックを指定するには、`#Region` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="e7621-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="e7621-114">配置することができますか*入れ子*、類似した領域のグループ化するには、その他の地域内の領域です。</span><span class="sxs-lookup"><span data-stu-id="e7621-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7621-115">例</span><span class="sxs-lookup"><span data-stu-id="e7621-115">Example</span></span>  
 <span data-ttu-id="e7621-116">`#Region` ディレクティブの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e7621-116">This example uses the `#Region` directive.</span></span>  
  
 <span data-ttu-id="e7621-117">[!code-vb[VbVbalrConditionalComp&4;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e7621-117">[!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7621-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7621-118">See Also</span></span>  
 <span data-ttu-id="e7621-119">[#If.#Else ディレクティブ。](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="e7621-119">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="e7621-120"> [アウトラインの中止](https://docs.microsoft.com/visualstudio/ide/outlining) </span><span class="sxs-lookup"><span data-stu-id="e7621-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining) </span></span>  
<span data-ttu-id="e7621-121"> [方法 : コードのセクションを折りたたんで非表示にする](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span><span class="sxs-lookup"><span data-stu-id="e7621-121"> [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)</span></span>
