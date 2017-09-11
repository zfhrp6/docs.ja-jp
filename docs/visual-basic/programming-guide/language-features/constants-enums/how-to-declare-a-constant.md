---
title: "方法: 定数 (Visual Basic) を宣言 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
dev_langs:
- VB
helpviewer_keywords:
- Integer data type, declaring constants
- Single data type, declaring constants
- Const statement [Visual Basic], declaring constants
- procedures, declaration
- data types [Visual Basic], constants
- Long data type, declaring constants
- Visual Basic code, declaring variables and constants
- Double data type, declaring constants
- Boolean data type, declaring constants
- modules, declaring constants
- Byte data type, declaring constants
- constants, declaring
- Date data type, declaring constants
- String data type, declaring constants
- declaring constants, const keyword
- Currency data type, declaring constants and variants
- module-level constants and variables
- Object data type, declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: b7fc499336c2b5db3b4d2fe9c0cd11799ea0ad77
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="66307-102">方法: 定数を宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66307-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="66307-103">使用する、`Const`定数を宣言し、その値を設定するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="66307-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="66307-104">定数を宣言することでは、値をわかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="66307-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="66307-105">定数が宣言されると、変更または新しい値を代入することはできません。</span><span class="sxs-lookup"><span data-stu-id="66307-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="66307-106">プロシージャ内で、またはモジュール、クラスまたは構造体の宣言セクションに定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="66307-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="66307-107">クラスまたは構造のレベルの定数は、`Private`既定としても宣言することがありますが、 `Public`、 `Friend`、 `Protected`、または`Protected Friend`コードへのアクセスの適切なレベルとして。</span><span class="sxs-lookup"><span data-stu-id="66307-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="66307-108">定数は、(、規則は、同じ変数名を作成するためのものと)、有効なシンボリック名と数値または文字列定数、演算子、(関数を呼び出す) を組み合わせた式が必要です。</span><span class="sxs-lookup"><span data-stu-id="66307-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="66307-109">定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="66307-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="66307-110">アクセス指定子を含む宣言を書き込む、`Const`キーワード、および次の例のように、式。</span><span class="sxs-lookup"><span data-stu-id="66307-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     <span data-ttu-id="66307-111">[!code-vb[VbEnumsTask&#8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="66307-111">[!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]</span></span>  
  
     <span data-ttu-id="66307-112">[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`、データ型を指定して定数を明示的に宣言する必要があります (`Boolean`、 `Byte`、 `Char`、 `DateTime`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Short`、 `Single`、または`String`)。</span><span class="sxs-lookup"><span data-stu-id="66307-112">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="66307-113">`Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。</span><span class="sxs-lookup"><span data-stu-id="66307-113">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="66307-114">コンパイラでは、式の型の定数の型を決定します。</span><span class="sxs-lookup"><span data-stu-id="66307-114">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="66307-115">詳細については、次を参照してください。[定数とリテラルのデータ型](constant-and-literal-data-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="66307-115">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="66307-116">明示的に定められたデータ型を持つ定数を宣言するのには</span><span class="sxs-lookup"><span data-stu-id="66307-116">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="66307-117">含む宣言を書き込む、`As`次の例のように、キーワードと明示的なデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="66307-117">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     <span data-ttu-id="66307-118">[!code-vb[VbEnumsTask&#9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="66307-118">[!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]</span></span>  
  
     <span data-ttu-id="66307-119">コードが読みやすく&1; 行につき&1; つの定数のみを宣言する場合は、1 行に複数の定数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="66307-119">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="66307-120">1 行に複数の定数を宣言する場合が必要にすべて同じアクセス レベル (`Public`、 `Private`、 `Friend`、 `Protected`、または`Protected Friend`)。</span><span class="sxs-lookup"><span data-stu-id="66307-120">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="66307-121">1 行に複数の定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="66307-121">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="66307-122">宣言は、次の例のように、スペースとコンマで区切ってください。</span><span class="sxs-lookup"><span data-stu-id="66307-122">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="66307-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="66307-123">See Also</span></span>  
 <span data-ttu-id="66307-124">[Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="66307-124">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="66307-125"> [定数とリテラルのデータ型](constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="66307-125"> [Constant and Literal Data Types](constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="66307-126"> [定数の概要](constants-overview.md)
 [方法: 定数を宣言](how-to-declare-a-constant.md)
 [ユーザー定義定数](user-defined-constants.md)
 [定数とリテラルのデータ型](constant-and-literal-data-types.md)
 [する方法: 関連する定数値をまとめてグループ](how-to-group-related-constant-values-together.md)
 [列挙型の概要](enumerations-overview.md)
 [する方法: 列挙型を宣言](how-to-declare-enumerations.md)
 [方法: 列挙型のメンバーを参照してください](how-to-refer-to-an-enumeration-member.md)
 [列挙型と名前修飾](enumerations-and-name-qualification.md)
 [する方法: 列挙型を反復](how-to-iterate-through-an-enumeration.md)
 [する方法: 文字列を確認します。列挙値に関連付けられている](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [列挙体を使用する場合](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="66307-126"> [Constants Overview](constants-overview.md)
 [How to: Declare A Constant](how-to-declare-a-constant.md)
 [User-Defined Constants](user-defined-constants.md)
 [Constant and Literal Data Types](constant-and-literal-data-types.md)
 [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md)
 [Enumerations Overview](enumerations-overview.md)
 [How to: Declare Enumerations](how-to-declare-enumerations.md)
 [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md)
 [Enumerations and Name Qualification](enumerations-and-name-qualification.md)
 [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md)
 [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 <span data-ttu-id="66307-127">[列挙型の概要](enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="66307-127">[Enumerations Overview](enumerations-overview.md) </span></span>  
<span data-ttu-id="66307-128"> [定数の概要](constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="66307-128"> [Constants Overview](constants-overview.md) </span></span>  
<span data-ttu-id="66307-129"> [方法: 列挙型を宣言](how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="66307-129"> [How to: Declare an Enumeration](how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="66307-130"> [列挙型と名前修飾](enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="66307-130"> [Enumerations and Name Qualification](enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="66307-131"> [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="66307-131"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="66307-132"> [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="66307-132"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>

