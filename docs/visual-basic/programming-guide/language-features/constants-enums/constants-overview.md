---
title: 定数の概要 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40330e8c2c60c866200e009a8280c7ec9c855435
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="bf825-102">定数の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf825-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="bf825-103">定数とは、数値または文字列が変化しないの代わりに使用されるわかりやすい名前です。</span><span class="sxs-lookup"><span data-stu-id="bf825-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="bf825-104">定数は、同じである、名前が示すように、アプリケーションの実行中の値を格納します。</span><span class="sxs-lookup"><span data-stu-id="bf825-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="bf825-105">大幅に、コードの読みやすさを向上し、定数を使用して管理しやすくできます。</span><span class="sxs-lookup"><span data-stu-id="bf825-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="bf825-106">再度表示される値を含むコード内を使用すると、保存または明確な意味がないが困難な特定の番号によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bf825-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="bf825-107">作成して、定数を使用する方法</span><span class="sxs-lookup"><span data-stu-id="bf825-107">How to Create and Use Constants</span></span>  
 <span data-ttu-id="bf825-108">Visual Basic には、主に印刷と表示を使用する定義済みの定数の数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bf825-108">Visual Basic contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="bf825-109">持つ独自の定数を作成することも、`Const`ステートメントでは、変数名を作成する場合と同じガイドラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf825-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="bf825-110">場合`Option Strict`は`On`、定数の型を明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf825-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="bf825-111">名前を修飾せずに参照できるすべてのコードのセットである、定数のスコープでは、同じ場所に宣言された変数のと同じです。</span><span class="sxs-lookup"><span data-stu-id="bf825-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="bf825-112">特定のプロシージャのスコープ内に存在する定数を作成するには、そのプロシージャ内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="bf825-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="bf825-113">アプリケーション全体で使用できる定数の宣言を使用して、`Public`クラスの宣言セクション内のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="bf825-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf825-114">定数には、変数と似ていますに変更したり、変数にすることができますに新しい値を代入することはできません。</span><span class="sxs-lookup"><span data-stu-id="bf825-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="bf825-115">コントロールやコンポーネントを使用するためのオブジェクト モデルによって、コードで使用する定数を定義できますも、ユーザー定義できます (つまり、自分で作成した)。</span><span class="sxs-lookup"><span data-stu-id="bf825-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="bf825-116">コンパイル時と実行時の定数</span><span class="sxs-lookup"><span data-stu-id="bf825-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="bf825-117">コンパイル時定数は、実行時の定数は、アプリケーションの実行中にのみ計算するときに、コードのコンパイル時に計算されます。</span><span class="sxs-lookup"><span data-stu-id="bf825-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="bf825-118">コンパイル時定数は、アプリケーションが実行されるたび、そのたびに変化する可能性があります、実行時の定数に同じ値になります。</span><span class="sxs-lookup"><span data-stu-id="bf825-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="bf825-119">コンパイル時の定数は、配列の範囲、case 式は、列挙子の初期化子などの場合も必要です。</span><span class="sxs-lookup"><span data-stu-id="bf825-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf825-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bf825-120">In This Section</span></span>  
  
|<span data-ttu-id="bf825-121">定義</span><span class="sxs-lookup"><span data-stu-id="bf825-121">Definition</span></span>|<span data-ttu-id="bf825-122">用語</span><span class="sxs-lookup"><span data-stu-id="bf825-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="bf825-123">方法 : 定数を宣言する</span><span class="sxs-lookup"><span data-stu-id="bf825-123">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|<span data-ttu-id="bf825-124">使用する方法について説明します、`Const`ステートメント定数を宣言し、その値を設定する定数を宣言するには、値にわかりやすい名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bf825-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="bf825-125">ユーザー定義定数</span><span class="sxs-lookup"><span data-stu-id="bf825-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|<span data-ttu-id="bf825-126">循環参照を回避する方法とスコープの設定に関する情報など、独自の定数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf825-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="bf825-127">定数とリテラルのデータ型</span><span class="sxs-lookup"><span data-stu-id="bf825-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|<span data-ttu-id="bf825-128">Visual Basic コンパイラでの定数の初期化方法に関する情報を提供時に`Option Explicit`がオフになっています。</span><span class="sxs-lookup"><span data-stu-id="bf825-128">Provides information on how the Visual Basic compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="bf825-129">方法 : 関連する定数値をまとめてグループ化する</span><span class="sxs-lookup"><span data-stu-id="bf825-129">How to: Group Related Constant Values Together</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|<span data-ttu-id="bf825-130">関連付けられている定数の値をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf825-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="bf825-131">参照</span><span class="sxs-lookup"><span data-stu-id="bf825-131">Reference</span></span>  
  
|<span data-ttu-id="bf825-132">定義</span><span class="sxs-lookup"><span data-stu-id="bf825-132">Definition</span></span>|<span data-ttu-id="bf825-133">用語</span><span class="sxs-lookup"><span data-stu-id="bf825-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="bf825-134">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="bf825-134">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|<span data-ttu-id="bf825-135">Visual Basic での定義済み定数を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="bf825-135">Lists the constants predefined by Visual Basic.</span></span>|  
|[<span data-ttu-id="bf825-136">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="bf825-136">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="bf825-137">について説明します、`Const`ステートメントとその使用します。</span><span class="sxs-lookup"><span data-stu-id="bf825-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="bf825-138">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="bf825-138">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="bf825-139">について説明します、`Option Strict`ステートメントとその使用します。</span><span class="sxs-lookup"><span data-stu-id="bf825-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf825-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf825-140">See Also</span></span>  
 [<span data-ttu-id="bf825-141">列挙型の概要</span><span class="sxs-lookup"><span data-stu-id="bf825-141">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="bf825-142">方法: Visual Basic で配列変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="bf825-142">How to: Initialize an Array Variable in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
