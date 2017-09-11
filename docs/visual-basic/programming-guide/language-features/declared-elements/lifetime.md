---
title: "Visual Basic における有効期間 |Microsoft ドキュメント"
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
- static variables, lifetime
- static variables, Visual Basic
- declared elements, lifetime
- Shared variable lifetime
- lifetime, declared elements
- lifetime, Visual Basic
- lifetime
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
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
ms.openlocfilehash: 4e183d1fa36c967facbb81ebd6917a8fb75d48cd
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="lifetime-in-visual-basic"></a><span data-ttu-id="0d500-102">Visual Basic における有効期間</span><span class="sxs-lookup"><span data-stu-id="0d500-102">Lifetime in Visual Basic</span></span>
<span data-ttu-id="0d500-103">*有効期間*宣言された要素は、一定時間その中に、使用可能です。</span><span class="sxs-lookup"><span data-stu-id="0d500-103">The *lifetime* of a declared element is the period of time during which it is available for use.</span></span> <span data-ttu-id="0d500-104">変数は、有効期間がある要素だけです。</span><span class="sxs-lookup"><span data-stu-id="0d500-104">Variables are the only elements that have lifetime.</span></span> <span data-ttu-id="0d500-105">この目的では、コンパイラは、プロシージャのパラメーターを処理し、変数の特殊なケースとして関数を返します。</span><span class="sxs-lookup"><span data-stu-id="0d500-105">For this purpose, the compiler treats procedure parameters and function returns as special cases of variables.</span></span> <span data-ttu-id="0d500-106">変数の有効期間は、値を保持できる期間を表します。</span><span class="sxs-lookup"><span data-stu-id="0d500-106">The lifetime of a variable represents the period of time during which it can hold a value.</span></span> <span data-ttu-id="0d500-107">その値をその有効期間を通じて変更できますが、いくつかの値を常に保持します。</span><span class="sxs-lookup"><span data-stu-id="0d500-107">Its value can change over its lifetime, but it always holds some value.</span></span>  
  
## <a name="different-lifetimes"></a><span data-ttu-id="0d500-108">別の有効期間</span><span class="sxs-lookup"><span data-stu-id="0d500-108">Different Lifetimes</span></span>  
 <span data-ttu-id="0d500-109">A*メンバー変数*(プロシージャの外側のモジュール レベルで宣言された) が宣言された要素と同じ有効期間は、通常ができます。</span><span class="sxs-lookup"><span data-stu-id="0d500-109">A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared.</span></span> <span data-ttu-id="0d500-110">クラスまたは構造体で宣言されている非共有変数は、クラスまたは構造体の宣言されているは、各インスタンスの別のコピーとして存在します。</span><span class="sxs-lookup"><span data-stu-id="0d500-110">A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="0d500-111">このような各変数には、そのインスタンスと同じ有効期間があります。</span><span class="sxs-lookup"><span data-stu-id="0d500-111">Each such variable has the same lifetime as its instance.</span></span> <span data-ttu-id="0d500-112">ただし、`Shared`変数が有効期間は&1; つだけでは継続時間全体で、アプリケーションが実行されています。</span><span class="sxs-lookup"><span data-stu-id="0d500-112">However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.</span></span>  
  
 <span data-ttu-id="0d500-113">A*ローカル変数*(プロシージャ内で宣言された) が宣言されているプロシージャの実行中にのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="0d500-113">A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running.</span></span> <span data-ttu-id="0d500-114">関数の戻り値とそのプロシージャのパラメーターにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="0d500-114">This applies also to that procedure's parameters and to any function return.</span></span> <span data-ttu-id="0d500-115">ただし、プロシージャが他のプロシージャを呼び出した場合は、呼び出されたプロシージャが実行中にローカル変数の値は保持します。</span><span class="sxs-lookup"><span data-stu-id="0d500-115">However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.</span></span>  
  
## <a name="beginning-of-lifetime"></a><span data-ttu-id="0d500-116">有効期間の開始</span><span class="sxs-lookup"><span data-stu-id="0d500-116">Beginning of Lifetime</span></span>  
 <span data-ttu-id="0d500-117">ローカル変数の有効期間は、制御が宣言されている手順を開始するときに開始されます。</span><span class="sxs-lookup"><span data-stu-id="0d500-117">A local variable's lifetime begins when control enters the procedure in which it is declared.</span></span> <span data-ttu-id="0d500-118">プロシージャが開始されるとすぐには、すべてのローカル変数をそのデータ型の既定値に初期化を実行しています。</span><span class="sxs-lookup"><span data-stu-id="0d500-118">Every local variable is initialized to the default value for its data type as soon as the procedure begins running.</span></span> <span data-ttu-id="0d500-119">プロシージャが検出した場合、`Dim`を初期値を指定するステートメントにローカル変数に設定これらの値をコードではその他の値に既に割り当ていた場合でもです。</span><span class="sxs-lookup"><span data-stu-id="0d500-119">When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.</span></span>  
  
 <span data-ttu-id="0d500-120">構造体変数の各メンバーは、そうでは別々 の変数として初期化されます。</span><span class="sxs-lookup"><span data-stu-id="0d500-120">Each member of a structure variable is initialized as if it were a separate variable.</span></span> <span data-ttu-id="0d500-121">同様に、配列変数の各要素は、個別に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="0d500-121">Similarly, each element of an array variable is initialized individually.</span></span>  
  
 <span data-ttu-id="0d500-122">プロシージャ内のブロック内で宣言された変数 (など、`For`ループ)、プロシージャへのエントリが初期化されています。</span><span class="sxs-lookup"><span data-stu-id="0d500-122">Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure.</span></span> <span data-ttu-id="0d500-123">このような初期化を有効に、コードがこれまで、ブロックを実行するかどうか。</span><span class="sxs-lookup"><span data-stu-id="0d500-123">These initializations take effect whether or not your code ever executes the block.</span></span>  
  
## <a name="end-of-lifetime"></a><span data-ttu-id="0d500-124">有効期間の終了</span><span class="sxs-lookup"><span data-stu-id="0d500-124">End of Lifetime</span></span>  
 <span data-ttu-id="0d500-125">プロシージャが終了すると、そのローカル変数の値は保持されず、および[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="0d500-125">When a procedure terminates, the values of its local variables are not preserved, and [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] reclaims their memory.</span></span> <span data-ttu-id="0d500-126">次に、プロシージャを呼び出すとき、すべてのローカル変数が新しく作成して再初期化します。</span><span class="sxs-lookup"><span data-stu-id="0d500-126">The next time you call the procedure, all its local variables are created afresh and reinitialized.</span></span>  
  
 <span data-ttu-id="0d500-127">クラスまたは構造体のインスタンスが終了すると、非共有変数には、そのメモリとその値が失われます。</span><span class="sxs-lookup"><span data-stu-id="0d500-127">When an instance of a class or structure terminates, its nonshared variables lose their memory and their values.</span></span> <span data-ttu-id="0d500-128">クラスまたは構造体の新しいインスタンスごとでは、作成し、非共有変数を再初期化します。</span><span class="sxs-lookup"><span data-stu-id="0d500-128">Each new instance of the class or structure creates and reinitializes its nonshared variables.</span></span> <span data-ttu-id="0d500-129">ただし、`Shared`変数は、アプリケーションの実行が停止されるまで保持されます。</span><span class="sxs-lookup"><span data-stu-id="0d500-129">However, `Shared` variables are preserved until your application stops running.</span></span>  
  
## <a name="extension-of-lifetime"></a><span data-ttu-id="0d500-130">有効期間の延長</span><span class="sxs-lookup"><span data-stu-id="0d500-130">Extension of Lifetime</span></span>  
 <span data-ttu-id="0d500-131">ローカル変数を宣言する場合、`Static`キーワード、その有効期間は、プロシージャの実行時間より長い。</span><span class="sxs-lookup"><span data-stu-id="0d500-131">If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure.</span></span> <span data-ttu-id="0d500-132">次の表は、プロシージャの宣言が期間を指定する方法を示しています、`Static`変数が存在します。</span><span class="sxs-lookup"><span data-stu-id="0d500-132">The following table shows how the procedure declaration determines how long a `Static` variable exists.</span></span>  
  
|<span data-ttu-id="0d500-133">プロシージャの場所との共有</span><span class="sxs-lookup"><span data-stu-id="0d500-133">Procedure location and sharing</span></span>|<span data-ttu-id="0d500-134">静的変数の有効期間を開始します。</span><span class="sxs-lookup"><span data-stu-id="0d500-134">Static variable lifetime begins</span></span>|<span data-ttu-id="0d500-135">静的変数の有効期間の終了</span><span class="sxs-lookup"><span data-stu-id="0d500-135">Static variable lifetime ends</span></span>|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|<span data-ttu-id="0d500-136">(既定では共有) モジュールで</span><span class="sxs-lookup"><span data-stu-id="0d500-136">In a module (shared by default)</span></span>|<span data-ttu-id="0d500-137">初めてのプロシージャが呼び出されたとき</span><span class="sxs-lookup"><span data-stu-id="0d500-137">The first time the procedure is called</span></span>|<span data-ttu-id="0d500-138">アプリケーションの実行が終了</span><span class="sxs-lookup"><span data-stu-id="0d500-138">When your application stops running</span></span>|  
|<span data-ttu-id="0d500-139">クラスでは、 `Shared` (手順は、インスタンスのメンバーではありません)</span><span class="sxs-lookup"><span data-stu-id="0d500-139">In a class, `Shared` (procedure is not an instance member)</span></span>|<span data-ttu-id="0d500-140">最初に、特定のインスタンスまたはクラスまたは構造体名自体のいずれかの手順が呼び出されます</span><span class="sxs-lookup"><span data-stu-id="0d500-140">The first time the procedure is called either on a specific instance or on the class or structure name itself</span></span>|<span data-ttu-id="0d500-141">アプリケーションの実行が終了</span><span class="sxs-lookup"><span data-stu-id="0d500-141">When your application stops running</span></span>|  
|<span data-ttu-id="0d500-142">クラスのインスタンスでない`Shared`(手順では、インスタンス メンバー)</span><span class="sxs-lookup"><span data-stu-id="0d500-142">In an instance of a class, not `Shared` (procedure is an instance member)</span></span>|<span data-ttu-id="0d500-143">初めてのプロシージャは、特定のインスタンスで呼び出されます</span><span class="sxs-lookup"><span data-stu-id="0d500-143">The first time the procedure is called on the specific instance</span></span>|<span data-ttu-id="0d500-144">ガベージ コレクション (GC) のインスタンスを解放する場合</span><span class="sxs-lookup"><span data-stu-id="0d500-144">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="static-variables-of-the-same-name"></a><span data-ttu-id="0d500-145">同じ名前の静的変数</span><span class="sxs-lookup"><span data-stu-id="0d500-145">Static Variables of the Same Name</span></span>  
 <span data-ttu-id="0d500-146">1 つ以上の手順で同じ名前を持つ静的変数を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="0d500-146">You can declare static variables with the same name in more than one procedure.</span></span> <span data-ttu-id="0d500-147">これを行う場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラは、このような各変数は別々 の要素を考慮します。</span><span class="sxs-lookup"><span data-stu-id="0d500-147">If you do this, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler considers each such variable to be a separate element.</span></span> <span data-ttu-id="0d500-148">これらの変数のいずれかの初期化では、他の値は影響しません。</span><span class="sxs-lookup"><span data-stu-id="0d500-148">The initialization of one of these variables does not affect the values of the others.</span></span> <span data-ttu-id="0d500-149">同じには、プロシージャのオーバー ロードのセットを定義およびオーバー ロードごとに同じ名前を持つ静的変数を宣言する場合が適用されます。</span><span class="sxs-lookup"><span data-stu-id="0d500-149">The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.</span></span>  
  
## <a name="containing-elements-for-static-variables"></a><span data-ttu-id="0d500-150">静的変数のコンテナー要素</span><span class="sxs-lookup"><span data-stu-id="0d500-150">Containing Elements for Static Variables</span></span>  
 <span data-ttu-id="0d500-151">つまり、そのクラスのプロシージャの中、クラス内で静的ローカル変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="0d500-151">You can declare a static local variable within a class, that is, inside a procedure in that class.</span></span> <span data-ttu-id="0d500-152">ただし、構造体のメンバー、またはその構造内のプロシージャのローカル変数として、構造内で静的ローカル変数を宣言できません。</span><span class="sxs-lookup"><span data-stu-id="0d500-152">However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d500-153">例</span><span class="sxs-lookup"><span data-stu-id="0d500-153">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0d500-154">説明</span><span class="sxs-lookup"><span data-stu-id="0d500-154">Description</span></span>  
 <span data-ttu-id="0d500-155">次の例で変数が宣言、[静的](../../../../visual-basic/language-reference/modifiers/static.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="0d500-155">The following example declares a variable with the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span> <span data-ttu-id="0d500-156">(必要としないこと、`Dim`キーワードと、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)など、修飾子を使用して`Static`)。</span><span class="sxs-lookup"><span data-stu-id="0d500-156">(Note that you do not need the `Dim` keyword when the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)</span></span>  
  
### <a name="code"></a><span data-ttu-id="0d500-157">コード</span><span class="sxs-lookup"><span data-stu-id="0d500-157">Code</span></span>  
 <span data-ttu-id="0d500-158">[!code-vb[VbVbalrKeywords&#13;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0d500-158">[!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]</span></span>  
  
### <a name="comments"></a><span data-ttu-id="0d500-159">コメント</span><span class="sxs-lookup"><span data-stu-id="0d500-159">Comments</span></span>  
 <span data-ttu-id="0d500-160">上記の例では、変数`applesSold`手順の後に存在し続けます`runningTotal`呼び出し元のコードを返します。</span><span class="sxs-lookup"><span data-stu-id="0d500-160">In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code.</span></span> <span data-ttu-id="0d500-161">次回`runningTotal`が呼び出されると、`applesSold`以前の計算値を保持します。</span><span class="sxs-lookup"><span data-stu-id="0d500-161">The next time `runningTotal` is called, `applesSold` retains its previously calculated value.</span></span>  
  
 <span data-ttu-id="0d500-162">場合`applesSold`を使用せずに宣言されていた`Static`への呼び出しによる、以前の累積値を保持されませんが`runningTotal`です。</span><span class="sxs-lookup"><span data-stu-id="0d500-162">If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`.</span></span> <span data-ttu-id="0d500-163">次回`runningTotal`、呼び出された`applesSold`は再作成され、0 に初期化と`runningTotal`あればだけ返さ呼び出されたのと同じ値です。</span><span class="sxs-lookup"><span data-stu-id="0d500-163">The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.</span></span>  
  
### <a name="compiling-the-code"></a><span data-ttu-id="0d500-164">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0d500-164">Compiling the Code</span></span>  
 <span data-ttu-id="0d500-165">宣言の一部として静的ローカル変数の値を初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="0d500-165">You can initialize the value of a static local variable as part of its declaration.</span></span> <span data-ttu-id="0d500-166">配列を宣言する場合`Static`、そのランク (次元数)、各次元の長さと個々 の要素の値に初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="0d500-166">If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.</span></span>  
  
### <a name="security"></a><span data-ttu-id="0d500-167">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0d500-167">Security</span></span>  
 <span data-ttu-id="0d500-168">前の例では、宣言することで有効期間は同じを生成できます`applesSold`モジュール レベルです。</span><span class="sxs-lookup"><span data-stu-id="0d500-168">In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level.</span></span> <span data-ttu-id="0d500-169">こうすると、変数のスコープを変更した場合は、ただし、プロシージャ不要になったに排他的にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0d500-169">If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it.</span></span> <span data-ttu-id="0d500-170">他のプロシージャにアクセスできなかったため`applesSold`とその値を変更、集計の途中の信頼性が低いことがおよび、コードを保守が困難でした。 します。</span><span class="sxs-lookup"><span data-stu-id="0d500-170">Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d500-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d500-171">See Also</span></span>  
 <span data-ttu-id="0d500-172">[共有](../../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-172">[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="0d500-173"> [何もない](../../../../visual-basic/language-reference/nothing.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-173"> [Nothing](../../../../visual-basic/language-reference/nothing.md) </span></span>  
<span data-ttu-id="0d500-174"> [宣言された要素名](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-174"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="0d500-175"> [宣言された要素への参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-175"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="0d500-176"> [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-176"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="0d500-177"> [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-177"> [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span></span>  
<span data-ttu-id="0d500-178"> [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-178"> [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="0d500-179"> [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-179"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="0d500-180"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="0d500-180"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="0d500-181"> [Static](../../../../visual-basic/language-reference/modifiers/static.md)</span><span class="sxs-lookup"><span data-stu-id="0d500-181"> [Static](../../../../visual-basic/language-reference/modifiers/static.md)</span></span>
