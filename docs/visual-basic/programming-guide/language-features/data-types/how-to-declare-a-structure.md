---
title: "方法: 構造体を宣言する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8203327e189d095c9f7ceeb3b68ea24efe9ba882
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="5db86-102">方法: 構造体を宣言する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5db86-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="5db86-103">ある構造体の宣言を開始する、 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)で終了して、 `End` `Structure`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5db86-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End` `Structure` statement.</span></span> <span data-ttu-id="5db86-104">これら 2 つのステートメントの間で、少なくとも 1 つを宣言する必要があります*要素*です。</span><span class="sxs-lookup"><span data-stu-id="5db86-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="5db86-105">任意のデータ型の要素を指定できますが、非共有変数または非共有、非カスタム イベントのいずれかにするには、少なくとも 1 つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="5db86-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="5db86-106">構造体の宣言で構造体の要素を初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="5db86-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="5db86-107">構造型の変数を宣言するときに、要素に、変数にアクセスすることにより値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5db86-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="5db86-108">構造体とクラス間の違いの詳細については、次を参照してください。[構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="5db86-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="5db86-109">デモの目的の従業員の名前、内線番号、および給与を追跡するような状況を検討してください。</span><span class="sxs-lookup"><span data-stu-id="5db86-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="5db86-110">構造体では、これは 1 つの変数で実行することができます。</span><span class="sxs-lookup"><span data-stu-id="5db86-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="5db86-111">構造体を宣言するには</span><span class="sxs-lookup"><span data-stu-id="5db86-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="5db86-112">最初と最後のステートメントの構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="5db86-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="5db86-113">使用して、構造体のアクセス レベルを指定することができます、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、またはすることができますできます既定で`Public`です。</span><span class="sxs-lookup"><span data-stu-id="5db86-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="5db86-114">構造体の本体に要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="5db86-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="5db86-115">構造体には、少なくとも 1 つの要素が必要です。</span><span class="sxs-lookup"><span data-stu-id="5db86-115">A structure must have at least one element.</span></span> <span data-ttu-id="5db86-116">すべての要素を宣言し、ファイルのアクセス レベルを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5db86-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="5db86-117">使用する場合、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、キーワードのないユーザー補助機能の既定値`Public`です。</span><span class="sxs-lookup"><span data-stu-id="5db86-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="5db86-118">`salary`フィールド前の例では`Private`、これは外側のクラスからでも、構造体の外部アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="5db86-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="5db86-119">ただし、`giveRaise`プロシージャは`Public`ので、構造体の外部から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5db86-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="5db86-120">同様に上げることができます、`salaryReviewTime`構造の外部からのイベントです。</span><span class="sxs-lookup"><span data-stu-id="5db86-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="5db86-121">変数だけでなく`Sub`プロシージャ、およびイベント、定数を定義することもできます。`Function`プロシージャ、および構造のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5db86-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="5db86-122">として最大で 1 つのプロパティを指定することができます、*既定プロパティ*に少なくとも 1 つの引数を受け取る提供します。</span><span class="sxs-lookup"><span data-stu-id="5db86-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="5db86-123">イベントを処理することができます、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5db86-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="5db86-124">詳細については、次を参照してください。[する方法: Visual Basic の既定のプロパティを呼び出してくださいを宣言し](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="5db86-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db86-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="5db86-125">See Also</span></span>  
 [<span data-ttu-id="5db86-126">データの種類</span><span class="sxs-lookup"><span data-stu-id="5db86-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="5db86-127">基本データ型</span><span class="sxs-lookup"><span data-stu-id="5db86-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="5db86-128">複合データ型</span><span class="sxs-lookup"><span data-stu-id="5db86-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="5db86-129">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="5db86-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="5db86-130">構造体</span><span class="sxs-lookup"><span data-stu-id="5db86-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5db86-131">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="5db86-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="5db86-132">構造体変数</span><span class="sxs-lookup"><span data-stu-id="5db86-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="5db86-133">構造体とその他のプログラミング要素</span><span class="sxs-lookup"><span data-stu-id="5db86-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="5db86-134">構造体とクラス</span><span class="sxs-lookup"><span data-stu-id="5db86-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="5db86-135">ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="5db86-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
