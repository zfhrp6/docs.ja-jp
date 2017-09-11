---
title: "方法: 列挙型 (Visual Basic) を宣言 |Microsoft ドキュメント"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
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
ms.openlocfilehash: 7adaca7e7252ce7165a5fd27b5bc9c049388206c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="63439-102">方法: 列挙型を宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63439-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="63439-103">持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="63439-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="63439-104">メソッド内で列挙体を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="63439-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="63439-105">適切なアクセス レベルを指定する`Private`、 `Protected`、 `Friend`、または`Public`です。</span><span class="sxs-lookup"><span data-stu-id="63439-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="63439-106">`Enum`型は、名前、基になる型では、および一連のフィールド、それぞれが表す定数。</span><span class="sxs-lookup"><span data-stu-id="63439-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="63439-107">名前を有効にする必要があります[!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]修飾子です。</span><span class="sxs-lookup"><span data-stu-id="63439-107">The name must be a valid [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualifier.</span></span> <span data-ttu-id="63439-108">基になる型は整数型のいずれかを指定する必要があります:`Byte`、 `Short`、`Long`または`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="63439-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="63439-109">`Integer` が既定値です。</span><span class="sxs-lookup"><span data-stu-id="63439-109">`Integer` is the default.</span></span> <span data-ttu-id="63439-110">列挙型は、常に厳密に型指定し、整数の数値型に置き換えることはできません。</span><span class="sxs-lookup"><span data-stu-id="63439-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="63439-111">列挙体には、浮動小数点値を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="63439-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="63439-112">列挙体には、浮動小数点値が割り当てられる場合`Option Strict On`、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="63439-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="63439-113">場合`Option Strict`は`Off`、値が自動的に変換する、`Enum`型です。</span><span class="sxs-lookup"><span data-stu-id="63439-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="63439-114">使用する方法および名について、`Imports`ステートメントを名前の修飾を不要なを参照してください[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)します。</span><span class="sxs-lookup"><span data-stu-id="63439-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="63439-115">列挙型を宣言するには</span><span class="sxs-lookup"><span data-stu-id="63439-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="63439-116">コード アクセス レベルでは、宣言を書き込む、`Enum`キーワード、および有効な名前、次の例のように、別の宣言`Enum`します。</span><span class="sxs-lookup"><span data-stu-id="63439-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     <span data-ttu-id="63439-117">[!code-vb[VbEnumsTask&#3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="63439-117">[!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span></span>  
  
2.  <span data-ttu-id="63439-118">列挙型の定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="63439-118">Define the constants in the enumeration.</span></span> <span data-ttu-id="63439-119">既定では、列挙体の最初の定数に初期化`0`、それに続く定数よりも前の定数のいずれかの値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="63439-119">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="63439-120">たとえば、次の列挙`Days`、という名前の定数が含まれています`Sunday`値を持つ`0`、という名前の定数`Monday`値を持つ`1`、という名前の定数`Tuesday`の値を持つ`2`、という具合です。</span><span class="sxs-lookup"><span data-stu-id="63439-120">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     <span data-ttu-id="63439-121">[!code-vb[VbEnumsTask&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="63439-121">[!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span></span>  
  
3.  <span data-ttu-id="63439-122">代入ステートメントを使用して列挙で定数に値を明示的に代入できます。</span><span class="sxs-lookup"><span data-stu-id="63439-122">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="63439-123">負の数値を含む任意の整数値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="63439-123">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="63439-124">たとえば、エラー状態を表す&0; より小さい値を持つ定数ができます。</span><span class="sxs-lookup"><span data-stu-id="63439-124">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="63439-125">次の列挙型定数`Invalid`、値が明示的に割り当てられた`–1`と定数`Sunday`、値が割り当てられた`0`します。</span><span class="sxs-lookup"><span data-stu-id="63439-125">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="63439-126">最初の定数、列挙型であるため`Saturday`は、値に初期化も`0`です。</span><span class="sxs-lookup"><span data-stu-id="63439-126">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="63439-127">値`Monday`は`1`(いずれかの値よりも詳細`Sunday`); の値`Tuesday`は`2`、という具合です。</span><span class="sxs-lookup"><span data-stu-id="63439-127">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     <span data-ttu-id="63439-128">[!code-vb[VbEnumsTask&#5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="63439-128">[!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span></span>  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="63439-129">明示的な型として列挙型を宣言するには</span><span class="sxs-lookup"><span data-stu-id="63439-129">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="63439-130">使用して列挙型の型を指定する、`As`句は、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="63439-130">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     <span data-ttu-id="63439-131">[!code-vb[VbEnumsTask&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="63439-131">[!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63439-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="63439-132">See Also</span></span>  
 <span data-ttu-id="63439-133">[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="63439-133">[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="63439-134"> [方法: 列挙型のメンバーを参照してください](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="63439-134"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="63439-135"> [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="63439-135"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="63439-136"> [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="63439-136"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="63439-137"> [列挙体を使用する場合](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="63439-137"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="63439-138"> [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="63439-138"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="63439-139"> [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="63439-139"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="63439-140"> [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="63439-140"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
