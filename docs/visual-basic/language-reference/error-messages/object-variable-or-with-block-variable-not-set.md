---
title: オブジェクト変数または With ブロック変数が設定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: b2bd1be83f57dbdc7a64b407dc1052074e19c74b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597665"
---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="289a8-102">オブジェクト変数または With ブロック変数が設定されていません。</span><span class="sxs-lookup"><span data-stu-id="289a8-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="289a8-103">無効なオブジェクト変数を参照しています。</span><span class="sxs-lookup"><span data-stu-id="289a8-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="289a8-104">このエラーが発生する原因は複数あります。</span><span class="sxs-lookup"><span data-stu-id="289a8-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="289a8-105">変数は、型を指定せずに宣言されました。</span><span class="sxs-lookup"><span data-stu-id="289a8-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="289a8-106">型を指定せず、変数を宣言している場合、既定値は入力`Object`です。</span><span class="sxs-lookup"><span data-stu-id="289a8-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="289a8-107">たとえば、変数を使用して宣言`Dim x`型になります`Object;`で宣言された変数`Dim x As String`型になります`String`です。</span><span class="sxs-lookup"><span data-stu-id="289a8-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="289a8-108">`Option Strict`ステートメントで暗黙の型の指定は許可されていません、`Object`型です。</span><span class="sxs-lookup"><span data-stu-id="289a8-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="289a8-109">型を省略すると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="289a8-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="289a8-110">参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="289a8-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="289a8-111">設定されているオブジェクトを参照しようとしています `Nothing`</span><span class="sxs-lookup"><span data-stu-id="289a8-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="289a8-112">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="289a8-112">.</span></span>  
  
-   <span data-ttu-id="289a8-113">適切に宣言されていない配列変数の要素にアクセスしようとするとします。</span><span class="sxs-lookup"><span data-stu-id="289a8-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="289a8-114">たとえば、配列として宣言されている`products() As String`配列の要素を参照しようとする場合、エラーをトリガーする`products(3) = "Widget"`です。</span><span class="sxs-lookup"><span data-stu-id="289a8-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="289a8-115">配列は、要素が存在しないと、オブジェクトとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="289a8-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="289a8-116">アクセス コード内にしようとすると、`With...End With`ブロック、ブロックが初期化される前にします。</span><span class="sxs-lookup"><span data-stu-id="289a8-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="289a8-117">A`With...End With`ブロックを実行することで初期化する必要があります、`With`ステートメントのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="289a8-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="289a8-118">以前のバージョンの Visual Basic または VBA でこのエラーを使用せず、変数に値を割り当てることによってもにトリガーされる、`Set`キーワード (`x = "name"`の代わりに`Set x = "name"`)。</span><span class="sxs-lookup"><span data-stu-id="289a8-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="289a8-119">`Set`キーワードは Visual Basic .Net で無効になりました。</span><span class="sxs-lookup"><span data-stu-id="289a8-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="289a8-120">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="289a8-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="289a8-121">設定`Option Strict`に`On`ファイルの先頭に次のコードを追加することで。</span><span class="sxs-lookup"><span data-stu-id="289a8-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="289a8-122">有効にしたくない場合`Option Strict`、せず、型指定されている変数がある場合、コードを検索 (`Dim x`の代わりに`Dim x As String`) し、目的の型を宣言に追加します。</span><span class="sxs-lookup"><span data-stu-id="289a8-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="289a8-123">設定されているオブジェクト変数を参照していないことを確認`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="289a8-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="289a8-124">コード内のキーワードの`Nothing`設定されていないオブジェクトになるように、コードを修正および`Nothing`後を参照していることになるまでです。</span><span class="sxs-lookup"><span data-stu-id="289a8-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="289a8-125">アクセスする前に、配列変数の寸法はことを確認します。</span><span class="sxs-lookup"><span data-stu-id="289a8-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="289a8-126">最初に、配列を作成するときに、ディメンションを割り当てることができますか (`Dim x(5) As String`の代わりに`Dim x() As String`)、または使用、`ReDim`キーワードを最初にアクセスする前に、配列の次元を設定します。</span><span class="sxs-lookup"><span data-stu-id="289a8-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="289a8-127">確認、`With`ブロックが実行することによって初期化されて、`With`ステートメントのエントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="289a8-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289a8-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="289a8-128">See Also</span></span>  
 [<span data-ttu-id="289a8-129">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="289a8-129">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="289a8-130">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="289a8-130">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="289a8-131">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="289a8-131">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
