---
title: Unicode (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: a61fd8e10c39569d92dd84180f678a1ff05a9310
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595723"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="3a79c-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a79c-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="3a79c-103">Visual Basic には、宣言されている外部プロシージャの名前に関係なく、Unicode の値にすべての文字列がマーシャ リングを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a79c-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="3a79c-104">プロジェクト外で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラには、プロシージャを正しく呼び出すために必要があります情報へのアクセスはありません。</span><span class="sxs-lookup"><span data-stu-id="3a79c-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="3a79c-105">この情報には、プロシージャが配置されている、それを識別する方法、その呼び出しシーケンスおよび戻り値の型が含まれます。 および使用する文字列の文字セットします。</span><span class="sxs-lookup"><span data-stu-id="3a79c-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="3a79c-106">[Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、この必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3a79c-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="3a79c-107">`charsetmodifier`の一部、`Declare`ステートメントは、外部プロシージャの呼び出し中に文字列をマーシャ リングには、文字セットの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3a79c-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="3a79c-108">Visual Basic が外部プロシージャ名を外部ファイルを検索する方法にも影響します。</span><span class="sxs-lookup"><span data-stu-id="3a79c-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="3a79c-109">`Unicode`修飾子は、Visual Basic がすべての文字列を Unicode 値のマーシャ リングする必要があり、検索中にその名前を変更することがなく、プロシージャを検索する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a79c-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="3a79c-110">文字セットに修飾子が指定されていない場合`Ansi`既定値です。</span><span class="sxs-lookup"><span data-stu-id="3a79c-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a79c-111">コメント</span><span class="sxs-lookup"><span data-stu-id="3a79c-111">Remarks</span></span>  
 <span data-ttu-id="3a79c-112">`Unicode`修飾子は、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3a79c-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3a79c-113">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="3a79c-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="3a79c-114">スマート デバイスの開発者向け注意事項</span><span class="sxs-lookup"><span data-stu-id="3a79c-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="3a79c-115">このキーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3a79c-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a79c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a79c-116">See Also</span></span>  
 [<span data-ttu-id="3a79c-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="3a79c-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [<span data-ttu-id="3a79c-118">Auto</span><span class="sxs-lookup"><span data-stu-id="3a79c-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="3a79c-119">キーワード</span><span class="sxs-lookup"><span data-stu-id="3a79c-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
