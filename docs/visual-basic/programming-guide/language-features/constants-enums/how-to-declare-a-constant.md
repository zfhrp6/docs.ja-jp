---
title: "方法: 定数を宣言する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554f659e060087228fb43efd8b9d06103e21e980
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-constant-visual-basic"></a><span data-ttu-id="1568c-102">方法: 定数を宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1568c-102">How to: Declare A Constant (Visual Basic)</span></span>
<span data-ttu-id="1568c-103">使用する、`Const`定数を宣言し、その値を設定するステートメント。</span><span class="sxs-lookup"><span data-stu-id="1568c-103">You use the `Const` statement to declare a constant and set its value.</span></span> <span data-ttu-id="1568c-104">定数を宣言すると、値にわかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1568c-104">By declaring a constant, you assign a meaningful name to a value.</span></span> <span data-ttu-id="1568c-105">定数が宣言されると、変更または新しい値を代入することはできません。</span><span class="sxs-lookup"><span data-stu-id="1568c-105">Once a constant is declared, it cannot be modified or assigned a new value.</span></span>  
  
 <span data-ttu-id="1568c-106">プロシージャ内で、またはモジュール、クラスまたは構造体の宣言セクションに定数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="1568c-106">You declare a constant within a procedure or in the declarations section of a module, class, or structure.</span></span> <span data-ttu-id="1568c-107">クラスまたは構造体レベルの定数が`Private`既定としても宣言することがありますが、 `Public`、 `Friend`、 `Protected`、または`Protected Friend`適切なレベルのコード アクセスします。</span><span class="sxs-lookup"><span data-stu-id="1568c-107">Class or structure-level constants are `Private` by default, but may also be declared as `Public`, `Friend`, `Protected`, or `Protected Friend` for the appropriate level of code access.</span></span>  
  
 <span data-ttu-id="1568c-108">定数は、(、規則は、同じ変数名を作成するためのものとして) 有効なシンボリック名および数値または文字列定数、演算子、(関数の呼び出しはありません) を組み合わせた式が必要です。</span><span class="sxs-lookup"><span data-stu-id="1568c-108">The constant must have a valid symbolic name (the rules are the same as those for creating variable names) and an expression composed of numeric or string constants and operators (but no function calls).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a><span data-ttu-id="1568c-109">定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="1568c-109">To declare a constant</span></span>  
  
-   <span data-ttu-id="1568c-110">アクセス指定子を含む宣言を記述、`Const`キーワード、および次の例のように、式。</span><span class="sxs-lookup"><span data-stu-id="1568c-110">Write a declaration that includes an access specifier, the `Const` keyword, and an expression, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     <span data-ttu-id="1568c-111">ときに[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`、データ型を指定することによって、定数を明示的に宣言する必要があります (`Boolean`、 `Byte`、 `Char`、 `DateTime`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Short`、 `Single`、または`String`)。</span><span class="sxs-lookup"><span data-stu-id="1568c-111">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare a constant explicitly by specifying a data type (`Boolean`, `Byte`, `Char`, `DateTime`, `Decimal`, `Double`, `Integer`, `Long`, `Short`, `Single`, or `String`).</span></span>  
  
     <span data-ttu-id="1568c-112">ときに`Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。</span><span class="sxs-lookup"><span data-stu-id="1568c-112">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="1568c-113">コンパイラでは、定数式の型からの型を決定します。</span><span class="sxs-lookup"><span data-stu-id="1568c-113">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="1568c-114">詳細については、次を参照してください。[定数とリテラルのデータ型](constant-and-literal-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="1568c-114">For more information, see [Constant and Literal Data Types](constant-and-literal-data-types.md).</span></span>  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a><span data-ttu-id="1568c-115">明示的に指定されたデータ型を持つ定数を宣言するのには</span><span class="sxs-lookup"><span data-stu-id="1568c-115">To declare a constant that has an explicitly stated data type</span></span>  
  
-   <span data-ttu-id="1568c-116">含む宣言を記述、`As`次の例のように、キーワードと明示的なデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="1568c-116">Write a declaration that includes the `As` keyword and an explicit data type, as in the following examples:</span></span>  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     <span data-ttu-id="1568c-117">コードが読みやすく 1 行につき 1 つの定数のみを宣言する場合は、単一行で複数の定数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="1568c-117">You can declare multiple constants on a single line, although your code is more readable if you declare only a single constant per line.</span></span> <span data-ttu-id="1568c-118">1 行に複数の定数を宣言する場合、すべて必要があります、同じアクセス レベル (`Public`、 `Private`、 `Friend`、 `Protected`、または`Protected Friend`)。</span><span class="sxs-lookup"><span data-stu-id="1568c-118">If you declare multiple constants on a single line, they must all have the same access level (`Public`, `Private`, `Friend`, `Protected`, or `Protected Friend`).</span></span>  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a><span data-ttu-id="1568c-119">1 行に複数の定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="1568c-119">To declare multiple constants on a single line</span></span>  
  
-   <span data-ttu-id="1568c-120">コンマと空白に次の例のように、宣言に分割します。</span><span class="sxs-lookup"><span data-stu-id="1568c-120">Separate the declarations with a comma and a space, as in the following example:</span></span>  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1568c-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1568c-121">See Also</span></span>  
 [<span data-ttu-id="1568c-122">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="1568c-122">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="1568c-123">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="1568c-123">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)  
 <span data-ttu-id="1568c-124">[定数の概要](constants-overview.md)[する方法: 定数を宣言](how-to-declare-a-constant.md)[ユーザー定義定数](user-defined-constants.md)[定数とリテラルのデータ型](constant-and-literal-data-types.md)[する方法: グループ関連する定数値を一緒に](how-to-group-related-constant-values-together.md)[列挙型の概要](enumerations-overview.md)[する方法: 列挙型を宣言](how-to-declare-enumerations.md)[する方法: 列挙体のメンバーを参照してください](how-to-refer-to-an-enumeration-member.md)[列挙型と名前修飾](enumerations-and-name-qualification.md)[する方法: 列挙型を反復](how-to-iterate-through-an-enumeration.md)[する方法: 列挙値に関連付けられている文字列を確認する](how-to-determine-the-string-associated-with-an-enumeration-value.md)[列挙体を使用する場合](when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="1568c-124">[Constants Overview](constants-overview.md) [How to: Declare A Constant](how-to-declare-a-constant.md) [User-Defined Constants](user-defined-constants.md) [Constant and Literal Data Types](constant-and-literal-data-types.md) [How to: Group Related Constant Values Together](how-to-group-related-constant-values-together.md) [Enumerations Overview](enumerations-overview.md) [How to: Declare Enumerations](how-to-declare-enumerations.md) [How to: Refer to an Enumeration Member](how-to-refer-to-an-enumeration-member.md) [Enumerations and Name Qualification](enumerations-and-name-qualification.md) [How to: Iterate Through An Enumeration](how-to-iterate-through-an-enumeration.md) [How to: Determine the String Associated with an Enumeration Value](how-to-determine-the-string-associated-with-an-enumeration-value.md) [When to Use an Enumeration](when-to-use-an-enumeration.md)</span></span>

 [<span data-ttu-id="1568c-125">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="1568c-125">Enumerations Overview</span></span>](enumerations-overview.md)  
 [<span data-ttu-id="1568c-126">定数の概要</span><span class="sxs-lookup"><span data-stu-id="1568c-126">Constants Overview</span></span>](constants-overview.md)  
 [<span data-ttu-id="1568c-127">方法: 列挙型を宣言</span><span class="sxs-lookup"><span data-stu-id="1568c-127">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)  
 [<span data-ttu-id="1568c-128">列挙型と名前の修飾</span><span class="sxs-lookup"><span data-stu-id="1568c-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)  
 [<span data-ttu-id="1568c-129">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="1568c-129">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="1568c-130">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="1568c-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
