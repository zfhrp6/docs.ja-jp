---
title: "定数の概要 (Visual Basic) |Microsoft ドキュメント"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
ms.openlocfilehash: 2df21b9e3e814c654b355472aa645481060c6f68
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="4cb33-102">定数の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cb33-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="4cb33-103">定数とは、数値または変更されない文字列の代わりに使用されるわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="4cb33-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="4cb33-104">定数は、同じである、名前が示すように、アプリケーションの実行中の値を格納します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="4cb33-105">大幅に、コードの読みやすさを向上し、定数を使用して管理しやすきます。</span><span class="sxs-lookup"><span data-stu-id="4cb33-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="4cb33-106">再表示される値を含むコード内を使用すると、特定の数値を記憶または明確な意味がないしにくいに依存します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="4cb33-107">作成して、定数を使用する方法</span><span class="sxs-lookup"><span data-stu-id="4cb33-107">How to Create and Use Constants</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4cb33-108">印刷および表示するために主を使用して、定義済みの定数の数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4cb33-108"> contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="4cb33-109">持つ独自の定数を作成することも、`Const`ステートメントの場合と同じガイドラインを使用して、変数名を作成します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="4cb33-110">場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4cb33-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="4cb33-111">一連の名前を修飾せずに参照できるすべてのコードでは、定数のスコープは、同じ場所で宣言された変数と同じです。</span><span class="sxs-lookup"><span data-stu-id="4cb33-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="4cb33-112">特定のプロシージャのスコープ内に存在する定数を作成するには、そのプロシージャ内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="4cb33-113">アプリケーション全体で使用できる定数を作成するには、宣言を使用して、`Public`クラスの宣言セクションにキーワードです。</span><span class="sxs-lookup"><span data-stu-id="4cb33-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cb33-114">定数には、変数と似ていますに変更したり、変数のように、新しい値を代入することはできません。</span><span class="sxs-lookup"><span data-stu-id="4cb33-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="4cb33-115">コントロールやコンポーネントを使用するためのオブジェクト モデルでは、コードで使用する定数を定義できますか、ユーザー定義できます (つまり、自分で作成した)。</span><span class="sxs-lookup"><span data-stu-id="4cb33-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="4cb33-116">コンパイル時と実行時定数</span><span class="sxs-lookup"><span data-stu-id="4cb33-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="4cb33-117">コンパイル時定数は、実行時定数は、アプリケーションの実行中にのみ計算するときに、コードのコンパイル時に計算されます。</span><span class="sxs-lookup"><span data-stu-id="4cb33-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="4cb33-118">コンパイル時定数では、実行時定数たびに変わる可能性があります中に、アプリケーションが実行されるたびに同じ値があります。</span><span class="sxs-lookup"><span data-stu-id="4cb33-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="4cb33-119">コンパイル時定数は、配列の範囲、case 式は、列挙子の初期化子などの場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="4cb33-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cb33-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4cb33-120">In This Section</span></span>  
  
|<span data-ttu-id="4cb33-121">定義</span><span class="sxs-lookup"><span data-stu-id="4cb33-121">Definition</span></span>|<span data-ttu-id="4cb33-122">用語</span><span class="sxs-lookup"><span data-stu-id="4cb33-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="4cb33-123">方法 : 定数を宣言する</span><span class="sxs-lookup"><span data-stu-id="4cb33-123">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|<span data-ttu-id="4cb33-124">使用する方法について説明、`Const`定数を宣言し、その値を設定するステートメントは定数を宣言すると、値にわかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4cb33-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="4cb33-125">ユーザー定義定数</span><span class="sxs-lookup"><span data-stu-id="4cb33-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|<span data-ttu-id="4cb33-126">循環参照を回避する方法とスコープの設定に関する情報など、独自の定数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="4cb33-127">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="4cb33-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|<span data-ttu-id="4cb33-128">方法に関する情報を提供[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ定数の初期化時に`Option Explicit`は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="4cb33-128">Provides information on how the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="4cb33-129">方法 : 関連する定数値をまとめてグループ化する</span><span class="sxs-lookup"><span data-stu-id="4cb33-129">How to: Group Related Constant Values Together</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|<span data-ttu-id="4cb33-130">関連付けられている定数の値をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="4cb33-131">参照</span><span class="sxs-lookup"><span data-stu-id="4cb33-131">Reference</span></span>  
  
|<span data-ttu-id="4cb33-132">定義</span><span class="sxs-lookup"><span data-stu-id="4cb33-132">Definition</span></span>|<span data-ttu-id="4cb33-133">用語</span><span class="sxs-lookup"><span data-stu-id="4cb33-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="4cb33-134">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="4cb33-134">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|<span data-ttu-id="4cb33-135">定義済み定数[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-135">Lists the constants predefined by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>|  
|[<span data-ttu-id="4cb33-136">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="4cb33-136">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="4cb33-137">説明、`Const`ステートメントとその使用します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="4cb33-138">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="4cb33-138">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="4cb33-139">説明、`Option Strict`ステートメントとその使用します。</span><span class="sxs-lookup"><span data-stu-id="4cb33-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cb33-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cb33-140">See Also</span></span>  
 <span data-ttu-id="4cb33-141">[列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4cb33-141">[Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="4cb33-142"> [方法: Visual Basic で配列変数を初期化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="4cb33-142"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
