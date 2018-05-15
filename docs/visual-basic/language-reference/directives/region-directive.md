---
title: '#領域ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: d25871140ef0674c013fc70d1306b2b4d0858556
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="region-directive"></a><span data-ttu-id="9a773-102">#Region ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="9a773-102">#Region Directive</span></span>
<span data-ttu-id="9a773-103">Visual Basic ファイルのコードのセクションを折りたたんで非表示にします。</span><span class="sxs-lookup"><span data-stu-id="9a773-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a773-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a773-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="9a773-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9a773-105">Parts</span></span>  
  
|<span data-ttu-id="9a773-106">用語</span><span class="sxs-lookup"><span data-stu-id="9a773-106">Term</span></span>|<span data-ttu-id="9a773-107">定義</span><span class="sxs-lookup"><span data-stu-id="9a773-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="9a773-108">必須。</span><span class="sxs-lookup"><span data-stu-id="9a773-108">Required.</span></span> <span data-ttu-id="9a773-109">領域が折りたたまれたときにその領域のタイトルとして機能する文字列です。</span><span class="sxs-lookup"><span data-stu-id="9a773-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="9a773-110">既定では、領域は折りたたまれています。</span><span class="sxs-lookup"><span data-stu-id="9a773-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="9a773-111">`#Region` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="9a773-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a773-112">コメント</span><span class="sxs-lookup"><span data-stu-id="9a773-112">Remarks</span></span>  
 <span data-ttu-id="9a773-113">Visual Studio コード エディターのアウトライン機能を使うときに展開または折りたたみの対象となるコード ブロックを指定するには、`#Region` ディレクティブを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a773-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="9a773-114">配置することができますまたは*入れ子*、類似した領域をグループ化するには、その他の領域内の領域。</span><span class="sxs-lookup"><span data-stu-id="9a773-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a773-115">例</span><span class="sxs-lookup"><span data-stu-id="9a773-115">Example</span></span>  
 <span data-ttu-id="9a773-116">`#Region` ディレクティブの使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9a773-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9a773-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a773-117">See Also</span></span>  
 [<span data-ttu-id="9a773-118">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="9a773-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="9a773-119">アウトライン</span><span class="sxs-lookup"><span data-stu-id="9a773-119">Outlining</span></span>](/visualstudio/ide/outlining)  
 [<span data-ttu-id="9a773-120">方法 : コードのセクションを折りたたんで非表示にする</span><span class="sxs-lookup"><span data-stu-id="9a773-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
