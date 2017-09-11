---
title: "オブジェクト変数または With ブロック変数が設定されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4db2c827c3e77cfa6cc51132f0d647a58c93c769
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="bd8c7-102">オブジェクト変数または With ブロック変数が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="bd8c7-103">無効なオブジェクト変数を参照しています。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="bd8c7-104">このエラーが発生する原因は複数あります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="bd8c7-105">型を指定せず、変数が宣言されました。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="bd8c7-106">型を指定せず、変数が宣言されている場合は、既定値は入力`Object`します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="bd8c7-107">宣言された変数など`Dim x`型であると`Object;`で宣言された変数`Dim x As String`型であると`String`です。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="bd8c7-108">`Option Strict`ステートメントでは、暗黙の型の指定が禁止されて、`Object`型です。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="bd8c7-109">型を省略すると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="bd8c7-110">参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="bd8c7-111">設定されているオブジェクトを参照しようとしています。`Nothing`</span><span class="sxs-lookup"><span data-stu-id="bd8c7-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="bd8c7-112">」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-112">.</span></span>  
  
-   <span data-ttu-id="bd8c7-113">適切に宣言されていない、配列変数の要素にアクセスしようとするとします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="bd8c7-114">としての配列の宣言など`products() As String`配列の要素を参照しようとする場合、エラーが発生`products(3) = "Widget"`します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="bd8c7-115">配列は、要素が存在しない、オブジェクトとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="bd8c7-116">アクセス コード内にしようとすると、`With...End With`ブロックを初期化する前にブロックします。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="bd8c7-117">A`With...End With`ブロックを実行することで初期化する必要があります、`With`ステートメントのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd8c7-118">以前のバージョンの Visual Basic または VBA でこのエラーを使用せず、変数に値を割り当てることによってもにトリガーされる、`Set`キーワード (`x = "name"`の代わりに`Set x = "name"`)。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="bd8c7-119">`Set`キーワードは Visual Basic .Net で無効になります。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd8c7-120">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bd8c7-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="bd8c7-121">設定`Option Strict`に`On`ファイルの先頭に次のコードを追加することで。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="bd8c7-122">有効にしたくない場合`Option Strict`、せず、型指定されている変数がある場合、コードを検索 (`Dim x`の代わりに`Dim x As String`) し、目的の型を宣言に追加します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="bd8c7-123">設定されている、オブジェクト変数を参照していないことを確認`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="bd8c7-124">コード内のキーワードの`Nothing`設定されていないオブジェクトになるように、コードを修正して`Nothing`を参照した後になるまでです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="bd8c7-125">アクセスする前に、配列変数の寸法はことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="bd8c7-126">最初に、配列を作成するときに、ディメンションを割り当てることができますか (`Dim x(5) As String`の代わりに`Dim x() As String`)、またはを使用して、`ReDim`最初にアクセスする前に、配列の次元を設定するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="bd8c7-127">必ず、`With`ブロックが実行することによって初期化されて、`With`ステートメントのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="bd8c7-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8c7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd8c7-128">See Also</span></span>  
 <span data-ttu-id="bd8c7-129">[オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c7-129">[Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="bd8c7-130"> [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bd8c7-130"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="bd8c7-131"> [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bd8c7-131"> [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
