---
title: "方法: 列挙型のメンバーを参照する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4e6eb9c011095c6cf0abe1ee3ac7a68f156f01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="44383-102">方法: 列挙型のメンバーを参照する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44383-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="44383-103">列挙体は、関連する定数のセットを使用して、定数値の名前に関連付ける便利な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="44383-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="44383-104">たとえば、一連の整数型の定数を曜日に関連付けて列挙型として宣言すると、コードで整数値ではなく曜日名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="44383-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="44383-105">完全修飾名を使用して回避することができます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="44383-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="44383-106">詳細については、次を参照してください。[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)です。</span><span class="sxs-lookup"><span data-stu-id="44383-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="44383-107">列挙体のメンバーを参照するには</span><span class="sxs-lookup"><span data-stu-id="44383-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="44383-108">列挙体のメンバー名を修飾します。</span><span class="sxs-lookup"><span data-stu-id="44383-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="44383-109">たとえば、次の例が割り当てられます、`Saturday`のメンバー、`FirstDayOfWeek`列挙型変数を`DayValue`です。</span><span class="sxs-lookup"><span data-stu-id="44383-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="44383-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="44383-110">See Also</span></span>  
 [<span data-ttu-id="44383-111">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="44383-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="44383-112">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="44383-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="44383-113">方法: Visual Basic で列挙型を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="44383-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="44383-114">方法 : 列挙値に関連付けられている文字列を確認する</span><span class="sxs-lookup"><span data-stu-id="44383-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="44383-115">列挙型を使用する状況</span><span class="sxs-lookup"><span data-stu-id="44383-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
