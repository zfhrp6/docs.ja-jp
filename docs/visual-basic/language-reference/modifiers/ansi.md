---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c7037acac58de56a396bd89f595ef897743ff4e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595080"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="6ef89-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ef89-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="6ef89-103">Visual Basic で宣言されている外部プロシージャの名前に関係なく American National Standards Institute (ANSI) の値をすべての文字列をマーシャ リングする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ef89-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="6ef89-104">プロジェクト外で定義されたプロシージャを呼び出すときに、Visual Basic コンパイラには、プロシージャを正しく呼び出すために必要な情報へのアクセスはありません。</span><span class="sxs-lookup"><span data-stu-id="6ef89-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="6ef89-105">この情報には、プロシージャが配置されている、それを識別する方法、その呼び出しシーケンスおよび戻り値の型が含まれます。 および使用する文字列の文字セットします。</span><span class="sxs-lookup"><span data-stu-id="6ef89-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="6ef89-106">[Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)外部プロシージャへの参照を作成し、この必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef89-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="6ef89-107">`charsetmodifier`の一部、`Declare`ステートメントが外部プロシージャの呼び出し中に文字列をマーシャ リングするための文字セットの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6ef89-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="6ef89-108">Visual Basic が外部プロシージャ名を外部ファイルを検索する方法にも影響します。</span><span class="sxs-lookup"><span data-stu-id="6ef89-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="6ef89-109">`Ansi`修飾子は、Visual Basic がすべての文字列を ANSI 値のマーシャ リングする必要があり、検索中にその名前を変更することがなく、プロシージャを検索する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ef89-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="6ef89-110">文字セットに修飾子が指定されていない場合`Ansi`既定値です。</span><span class="sxs-lookup"><span data-stu-id="6ef89-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ef89-111">コメント</span><span class="sxs-lookup"><span data-stu-id="6ef89-111">Remarks</span></span>  
 <span data-ttu-id="6ef89-112">`Ansi`修飾子は、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ef89-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6ef89-113">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="6ef89-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="6ef89-114">スマート デバイスの開発者向け注意事項</span><span class="sxs-lookup"><span data-stu-id="6ef89-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="6ef89-115">このキーワードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="6ef89-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef89-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ef89-116">See Also</span></span>  
 [<span data-ttu-id="6ef89-117">Auto</span><span class="sxs-lookup"><span data-stu-id="6ef89-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="6ef89-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="6ef89-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="6ef89-119">キーワード</span><span class="sxs-lookup"><span data-stu-id="6ef89-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
