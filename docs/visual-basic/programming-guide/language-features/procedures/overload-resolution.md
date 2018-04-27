---
title: オーバーロードの解決法 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e62560d853c95bc4bba6ba829d8579ee4388858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="83918-102">オーバーロードの解決法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83918-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="83918-103">Visual Basic コンパイラには、いくつかのオーバー ロードされたバージョンで定義されているプロシージャへの呼び出しが検出されると、コンパイラはのどのオーバー ロードを呼び出すを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83918-103">When the Visual Basic compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="83918-104">これは、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="83918-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="83918-105">**アクセシビリティ。**</span><span class="sxs-lookup"><span data-stu-id="83918-105">**Accessibility.**</span></span> <span data-ttu-id="83918-106">呼び出し元のコードの呼び出しを防止するアクセス レベルを持つオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="83918-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="83918-107">**パラメーターの数。**</span><span class="sxs-lookup"><span data-stu-id="83918-107">**Number of Parameters.**</span></span> <span data-ttu-id="83918-108">呼び出しで指定された数と異なる数のパラメーターが定義されているオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="83918-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="83918-109">**パラメーターのデータ型。**</span><span class="sxs-lookup"><span data-stu-id="83918-109">**Parameter Data Types.**</span></span> <span data-ttu-id="83918-110">コンパイラは、拡張メソッドよりインスタンス メソッドの基本設定を示します。</span><span class="sxs-lookup"><span data-stu-id="83918-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="83918-111">拡大に合わせてプロシージャの呼び出しの変換だけを必要とする任意のインスタンス メソッドが見つかった場合は、すべての拡張メソッドは削除され、インスタンス メソッドの候補をコンパイラが続行されます。</span><span class="sxs-lookup"><span data-stu-id="83918-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="83918-112">このようなインスタンス メソッドが見つからない場合は、インスタンスと拡張メソッドの両方を続行します。</span><span class="sxs-lookup"><span data-stu-id="83918-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="83918-113">このステップでは、オーバー ロードで定義されているパラメーターの型への呼び出し元の引数のデータ型を変換できませんオーバー ロードがなくなります。</span><span class="sxs-lookup"><span data-stu-id="83918-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="83918-114">**縮小変換をします。**</span><span class="sxs-lookup"><span data-stu-id="83918-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="83918-115">定義済みパラメーターの型への呼び出し元の引数の型から縮小変換を必要なオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="83918-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="83918-116">これは、該当するかどうか、型チェック スイッチの ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`または`Off`です。</span><span class="sxs-lookup"><span data-stu-id="83918-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="83918-117">**最小の拡大。**</span><span class="sxs-lookup"><span data-stu-id="83918-117">**Least Widening.**</span></span> <span data-ttu-id="83918-118">コンパイラでは、ペアで残りのオーバー ロードと見なします。</span><span class="sxs-lookup"><span data-stu-id="83918-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="83918-119">各ペアに対して定義されているパラメーターのデータ型を比較します。</span><span class="sxs-lookup"><span data-stu-id="83918-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="83918-120">場合は、他の対応する型に拡大変換するすべてのオーバー ロードのいずれかの型、コンパイラは後者を除外します。</span><span class="sxs-lookup"><span data-stu-id="83918-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="83918-121">つまり、最低限の拡大変換を必要とするオーバー ロードを保持します。</span><span class="sxs-lookup"><span data-stu-id="83918-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="83918-122">**1 つの候補です。**</span><span class="sxs-lookup"><span data-stu-id="83918-122">**Single Candidate.**</span></span> <span data-ttu-id="83918-123">まで 1 つだけのペアでオーバー ロードをそのまま残り、オーバー ロードして、呼び出しを解決するオーバー ロードすることを検討して続行します。</span><span class="sxs-lookup"><span data-stu-id="83918-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="83918-124">コンパイラは、候補を 1 つのオーバー ロードを減らすことはできません、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="83918-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="83918-125">次の図は、一連のオーバー ロードされたバージョンを呼び出すのかを決定するプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="83918-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="83918-126">![オーバー ロードの解決プロセスのフロー ダイアグラム](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="83918-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="83918-127">オーバー ロードされたバージョン間での解決</span><span class="sxs-lookup"><span data-stu-id="83918-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="83918-128">次の例は、このオーバー ロードの解決プロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="83918-128">The following example illustrates this overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 <span data-ttu-id="83918-129">コンパイラがあるため最初のオーバー ロードを排除最初の呼び出しで最初の引数の型 (`Short`)、対応するパラメーターの型へ縮小変換 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="83918-129">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="83918-130">次に除去 3 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`) 3 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。</span><span class="sxs-lookup"><span data-stu-id="83918-130">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="83918-131">2 番目のオーバー ロードが必要な小さい拡大ので、コンパイラは、呼び出しに使用します。</span><span class="sxs-lookup"><span data-stu-id="83918-131">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="83918-132">2 番目の呼び出しでは、コンパイラは縮小に基づいてオーバー ロードのいずれかで除去ことはできません。</span><span class="sxs-lookup"><span data-stu-id="83918-132">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="83918-133">引数の型の少ない拡大変換と 2 番目のオーバー ロードを呼び出すことがあるため最初の呼び出しと同様に、同じ理由から、3 番目のオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="83918-133">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="83918-134">ただし、コンパイラは、最初と 2 番目のオーバー ロードの解決できません。</span><span class="sxs-lookup"><span data-stu-id="83918-134">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="83918-135">それぞれが、他の対応する型に拡大する 1 つの定義済みパラメーターの型 (`Byte`に`Short`が`Single`に`Double`)。</span><span class="sxs-lookup"><span data-stu-id="83918-135">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="83918-136">そのため、コンパイラには、オーバー ロードの解決エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="83918-136">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="83918-137">省略可能なオーバー ロードと ParamArray 引数</span><span class="sxs-lookup"><span data-stu-id="83918-137">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="83918-138">最後のパラメーターを宣言する点を除いて、プロシージャの 2 つのオーバー ロードが同じシグネチャを持つ場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)他のコンパイラとしてそのプロシージャの呼び出しを解決次に示します。</span><span class="sxs-lookup"><span data-stu-id="83918-138">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="83918-139">呼び出しが最後の引数として指定した場合</span><span class="sxs-lookup"><span data-stu-id="83918-139">If the call supplies the last argument as</span></span>|<span data-ttu-id="83918-140">コンパイラは最後の引数として宣言するオーバー ロードへの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="83918-140">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="83918-141">値なし (引数を省略すると)</span><span class="sxs-lookup"><span data-stu-id="83918-141">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="83918-142">1 つの値</span><span class="sxs-lookup"><span data-stu-id="83918-142">A single value</span></span>|`Optional`|  
|<span data-ttu-id="83918-143">コンマ区切りの一覧で、2 つ以上の値</span><span class="sxs-lookup"><span data-stu-id="83918-143">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="83918-144">(空の配列を含む) 任意の長さの配列</span><span class="sxs-lookup"><span data-stu-id="83918-144">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="83918-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="83918-145">See Also</span></span>  
 [<span data-ttu-id="83918-146">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="83918-146">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="83918-147">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="83918-147">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="83918-148">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="83918-148">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="83918-149">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="83918-149">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="83918-150">方法 : プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="83918-150">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="83918-151">方法 : オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="83918-151">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="83918-152">方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="83918-152">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="83918-153">方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="83918-153">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="83918-154">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="83918-154">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="83918-155">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="83918-155">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="83918-156">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="83918-156">Extension Methods</span></span>](./extension-methods.md)
