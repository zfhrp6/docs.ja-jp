---
title: "ユーザー定義定数 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
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
ms.openlocfilehash: b1ab1501309823b1565d5198fff25edf2927a2ce
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="1b5e6-102">ユーザー定義定数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b5e6-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="1b5e6-103">定数とは、数値または変更されない文字列の代わりに使用されるわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="1b5e6-104">定数値は、その名前からわかるように、一定に保たれるアプリケーションの実行中に格納します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="1b5e6-105">コントロールや使用するコンポーネントで定義されている定数を使用するか、独自に作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="1b5e6-106">自分で作成した定数は*ユーザー定義*します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="1b5e6-107">持つ定数の宣言、`Const`ステートメント、変数名を作成する場合と同じガイドラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="1b5e6-108">場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="1b5e6-109">Const ステートメントの使用状況</span><span class="sxs-lookup"><span data-stu-id="1b5e6-109">Const Statement Usage</span></span>  
 <span data-ttu-id="1b5e6-110">A`Const`ステートメント、数学的な表現したり、日付/時刻の数量。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 <span data-ttu-id="1b5e6-111">[!code-vb[VbEnumsTask&#10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b5e6-111">[!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span></span>  
  
 <span data-ttu-id="1b5e6-112">定義できます`String`定数。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-112">It also can define `String` constants:</span></span>  
  
 <span data-ttu-id="1b5e6-113">[!code-vb[VbEnumsTask&#13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b5e6-113">[!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span></span>  
  
 <span data-ttu-id="1b5e6-114">等号の右側にある式 ( `=` ) 多くの場合、数値またはリテラル文字列が、(ただし、その式には、関数の呼び出しを含めることはできません)、数値または文字列に評価される式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-114">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="1b5e6-115">以前に定義された定数の観点から定数を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-115">You can even define constants in terms of previously defined constants:</span></span>  
  
 <span data-ttu-id="1b5e6-116">[!code-vb[VbEnumsTask&#15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b5e6-116">[!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span></span>  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="1b5e6-117">ユーザー定義関数のスコープ</span><span class="sxs-lookup"><span data-stu-id="1b5e6-117">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="1b5e6-118">A`Const`ステートメントのスコープは、同じ場所で宣言された変数のと同じです。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-118">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="1b5e6-119">次のような方法では、スコープを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-119">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="1b5e6-120">プロシージャ内でのみ存在する定数を作成するには、そのプロシージャ内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-120">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="1b5e6-121">使用できるは、そのモジュールの外部コードではなく、クラス内のすべてのプロシージャに定数を作成するには、クラスの宣言セクションで宣言します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-121">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="1b5e6-122">アセンブリの外部のクライアントではなく、アセンブリのすべてのメンバーには、使用できる定数を作成するには、宣言を使用して、`Friend`クラスの宣言セクションにキーワードです。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-122">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="1b5e6-123">アプリケーション全体で使用できる定数を作成するには、宣言を使用して、`Public`セクションで、クラスの宣言でキーワードです。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-123">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="1b5e6-124">詳細については、次を参照してください。[方法: A 定数の宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-124">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="1b5e6-125">循環参照の回避</span><span class="sxs-lookup"><span data-stu-id="1b5e6-125">Avoiding Circular References</span></span>  
 <span data-ttu-id="1b5e6-126">発生する可能性は他の定数の観点から定数を定義するため、*サイクル*、または&2; つ以上の定数の間での循環参照。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-126">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="1b5e6-127">サイクルは、2 つ以上のパブリック定数は、別の例を次の条件で定義したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-127">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 <span data-ttu-id="1b5e6-128">[!code-vb[VbEnumsTask&#16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b5e6-128">[!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span></span>  
<span data-ttu-id="1b5e6-129">[!code-vb[VbEnumsTask&17;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1b5e6-129">[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span></span>  
  
 <span data-ttu-id="1b5e6-130">循環参照が発生した場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1b5e6-130">If a cycle occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b5e6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b5e6-131">See Also</span></span>  
 <span data-ttu-id="1b5e6-132">[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-132">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="1b5e6-133"> [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-133"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="1b5e6-134"> [定数と列挙型](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-134"> [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span></span>  
<span data-ttu-id="1b5e6-135"> [定数と列挙型](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-135"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span></span>  
<span data-ttu-id="1b5e6-136"> [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-136"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="1b5e6-137"> [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-137"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="1b5e6-138"> [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-138"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="1b5e6-139"> [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="1b5e6-139"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="1b5e6-140"> [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="1b5e6-140"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
