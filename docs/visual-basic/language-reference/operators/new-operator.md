---
title: "New 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="53547-102">New 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53547-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="53547-103">導入されています、`New`句を新しいオブジェクト インスタンスを作成する型パラメーターにコンス トラクター制約を指定または識別、`Sub`クラス コンス トラクターと手順。</span><span class="sxs-lookup"><span data-stu-id="53547-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53547-104">コメント</span><span class="sxs-lookup"><span data-stu-id="53547-104">Remarks</span></span>  
 <span data-ttu-id="53547-105">代入ステートメントの宣言で、`New`句は、定義済みのインスタンスの作成元となるクラスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53547-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="53547-106">つまり、クラスが呼び出し元のコードがアクセスできる 1 つまたは複数のコンス トラクターを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53547-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="53547-107">使用することができます、`New`宣言ステートメントまたは代入ステートメントの句。</span><span class="sxs-lookup"><span data-stu-id="53547-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="53547-108">ステートメントを実行すると、指定した任意の引数を渡して、指定したクラスの適切なコンス トラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53547-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="53547-109">次の例では、これを示しますのインスタンスを作成することで、`Customer`いずれかのパラメーターをとらない使用し、文字列パラメーターを受け取るいずれかを使用する、2 つのコンス トラクターを持つクラス。</span><span class="sxs-lookup"><span data-stu-id="53547-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="53547-110">配列はクラス、`New`次の例に示すように、配列の新しいインスタンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="53547-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="53547-111">共通言語ランタイム (CLR) スロー、<xref:System.OutOfMemoryException>メモリ不足の新しいインスタンスを作成する場合はエラーです。</span><span class="sxs-lookup"><span data-stu-id="53547-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53547-112">`New`キーワードにも使用型パラメーター リストで指定された型がアクセスできるパラメーターなしコンス トラクターを公開する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="53547-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="53547-113">型パラメーターや制約の詳細については、次を参照してください。[型リスト](../../../visual-basic/language-reference/statements/type-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="53547-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="53547-114">クラスのコンス トラクターのプロシージャを作成するには、名前を設定、`Sub`する手順、`New`キーワード。</span><span class="sxs-lookup"><span data-stu-id="53547-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="53547-115">詳細については、次を参照してください。[オブジェクトの有効期間: オブジェクトが作成と破棄にはどのように](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)です。</span><span class="sxs-lookup"><span data-stu-id="53547-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="53547-116">キーワード `New` は次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="53547-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="53547-117">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="53547-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="53547-118">Of</span><span class="sxs-lookup"><span data-stu-id="53547-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="53547-119">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="53547-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="53547-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="53547-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="53547-121">キーワード</span><span class="sxs-lookup"><span data-stu-id="53547-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="53547-122">型リスト</span><span class="sxs-lookup"><span data-stu-id="53547-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="53547-123">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="53547-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="53547-124">オブジェクトの有効期間 : オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="53547-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
