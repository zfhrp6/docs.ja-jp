---
title: '方法: 関連する定数値をまとめてグループ化する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 320373116ad4d61293690353fce6b7b152e79a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646405"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="3e6d0-102">方法: 関連する定数値をまとめてグループ化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e6d0-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="3e6d0-103">列挙型は、関連する定数をグループ化する最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="3e6d0-104">持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="3e6d0-105">詳細については、次を参照してください。[する方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="3e6d0-106">グループに関連する定数値</span><span class="sxs-lookup"><span data-stu-id="3e6d0-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="3e6d0-107">コードのアクセス レベルを含む宣言を書き込み、`Enum`キーワード、および有効な名前です。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="3e6d0-108">この例で作成、`Private`列挙型、`temperatureValues`です。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="3e6d0-109">列挙体の定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="3e6d0-110">この例で作成、`Public`列挙`temperatureValues`し、その値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3e6d0-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3e6d0-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e6d0-111">See Also</span></span>  
 [<span data-ttu-id="3e6d0-112">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="3e6d0-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="3e6d0-113">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="3e6d0-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="3e6d0-114">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="3e6d0-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="3e6d0-115">定数の概要</span><span class="sxs-lookup"><span data-stu-id="3e6d0-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="3e6d0-116">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="3e6d0-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="3e6d0-117">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="3e6d0-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
