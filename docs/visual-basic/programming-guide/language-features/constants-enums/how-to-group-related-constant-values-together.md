---
title: "方法: 関連する定数値をまとめてグループ化する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="6992f-102">方法: 関連する定数値をまとめてグループ化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6992f-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="6992f-103">列挙型は、関連する定数をグループ化する最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="6992f-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="6992f-104">持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="6992f-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="6992f-105">詳細については、次を参照してください。[する方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)です。</span><span class="sxs-lookup"><span data-stu-id="6992f-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="6992f-106">グループに関連する定数値</span><span class="sxs-lookup"><span data-stu-id="6992f-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="6992f-107">コードのアクセス レベルを含む宣言を書き込み、`Enum`キーワード、および有効な名前です。</span><span class="sxs-lookup"><span data-stu-id="6992f-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="6992f-108">この例で作成、`Private`列挙型、`temperatureValues`です。</span><span class="sxs-lookup"><span data-stu-id="6992f-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="6992f-109">列挙体の定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="6992f-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="6992f-110">この例で作成、`Public`列挙`temperatureValues`し、その値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6992f-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6992f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6992f-111">See Also</span></span>  
 [<span data-ttu-id="6992f-112">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="6992f-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="6992f-113">方法 : 列挙型のメンバーを参照する</span><span class="sxs-lookup"><span data-stu-id="6992f-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="6992f-114">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="6992f-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="6992f-115">定数の概要</span><span class="sxs-lookup"><span data-stu-id="6992f-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="6992f-116">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="6992f-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="6992f-117">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="6992f-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
