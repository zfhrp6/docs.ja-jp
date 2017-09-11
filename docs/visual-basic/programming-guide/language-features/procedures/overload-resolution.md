---
title: "オーバー ロードの解決 (Visual Basic) |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- overload resolution
- procedures, overloading
- procedures, calling
- procedure overloading, overload resolution
- signatures, procedure
- overloads, resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
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
ms.openlocfilehash: a4f350af0f7d964df45974990991a2e94b26551e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="95b13-102">オーバーロードの解決法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95b13-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="95b13-103">ときに、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラは、いくつかのオーバー ロードされたバージョンで定義されているプロシージャの呼び出しを検出すると、コンパイラは、オーバー ロードを呼び出すを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95b13-103">When the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="95b13-104">次の手順を実行することによってこれが行われます。</span><span class="sxs-lookup"><span data-stu-id="95b13-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="95b13-105">**ユーザー補助機能です。**</span><span class="sxs-lookup"><span data-stu-id="95b13-105">**Accessibility.**</span></span> <span data-ttu-id="95b13-106">呼び出し元のコードの呼び出しを防止するアクセス レベルを持つオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="95b13-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="95b13-107">**パラメーターの数。**</span><span class="sxs-lookup"><span data-stu-id="95b13-107">**Number of Parameters.**</span></span> <span data-ttu-id="95b13-108">呼び出しで指定された数と異なる数のパラメーターが定義されているオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="95b13-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="95b13-109">**パラメーターのデータ型。**</span><span class="sxs-lookup"><span data-stu-id="95b13-109">**Parameter Data Types.**</span></span> <span data-ttu-id="95b13-110">コンパイラは、拡張メソッドよりインスタンス メソッドを優先します。</span><span class="sxs-lookup"><span data-stu-id="95b13-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="95b13-111">拡大に合わせてプロシージャの呼び出しの変換だけが必要な任意のインスタンス メソッドが見つかった場合は、すべての拡張メソッドは削除され、インスタンス メソッドの候補をコンパイラが続行します。</span><span class="sxs-lookup"><span data-stu-id="95b13-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="95b13-112">このようなインスタンス メソッドが見つからない場合は、インスタンスと拡張メソッドの両方で続行します。</span><span class="sxs-lookup"><span data-stu-id="95b13-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="95b13-113">この手順で、オーバー ロードで定義されているパラメーターの型への呼び出しの引数のデータ型を変換できませんオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="95b13-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="95b13-114">**縮小変換です。**</span><span class="sxs-lookup"><span data-stu-id="95b13-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="95b13-115">定義されたパラメーターの型への呼び出しの引数の型から縮小変換を必要なオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="95b13-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="95b13-116">これは、該当の型チェックを切り替えるかどうか ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`または`Off`です。</span><span class="sxs-lookup"><span data-stu-id="95b13-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="95b13-117">**最小の拡大。**</span><span class="sxs-lookup"><span data-stu-id="95b13-117">**Least Widening.**</span></span> <span data-ttu-id="95b13-118">コンパイラは、ペアで残りのオーバー ロードを考慮します。</span><span class="sxs-lookup"><span data-stu-id="95b13-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="95b13-119">各ペアに対して定義されているパラメーターのデータ型を比較します。</span><span class="sxs-lookup"><span data-stu-id="95b13-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="95b13-120">すべてのオーバー ロードのいずれかの型は、もう一方で対応する型に拡大する場合、コンパイラは、後者を除外します。</span><span class="sxs-lookup"><span data-stu-id="95b13-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="95b13-121">つまり、最小限の拡大を必要とするオーバー ロードを保持します。</span><span class="sxs-lookup"><span data-stu-id="95b13-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="95b13-122">**1 つの候補です。**</span><span class="sxs-lookup"><span data-stu-id="95b13-122">**Single Candidate.**</span></span> <span data-ttu-id="95b13-123">オーバー ロードを&1; つだけまでのペアがそのまま残り、オーバー ロードし、そのオーバー ロードの呼び出しを解決することを検討して続行します。</span><span class="sxs-lookup"><span data-stu-id="95b13-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="95b13-124">コンパイラは、候補を&1; つのオーバー ロードを減らすことができない、エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="95b13-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="95b13-125">次の図は、一連のオーバー ロードされたバージョンを呼び出すのどれかを判断するプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="95b13-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="95b13-126">![オーバー ロードの解決プロセスのフロー図](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="95b13-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="95b13-127">オーバー ロードされたバージョンを解決します。</span><span class="sxs-lookup"><span data-stu-id="95b13-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="95b13-128">次の例では、このオーバー ロードの解決プロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="95b13-128">The following example illustrates this overload resolution process.</span></span>  
  
 <span data-ttu-id="95b13-129">[!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="95b13-129">[!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span></span>  
  
 <span data-ttu-id="95b13-130">[!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="95b13-130">[!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span></span>  
  
 <span data-ttu-id="95b13-131">最初の呼び出しで、コンパイラが最初のオーバー ロードを排除の最初の引数の型 (`Short`) に対応するパラメーターの型を変更して (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="95b13-131">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="95b13-132">次に除去&3; 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`)&3; 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。</span><span class="sxs-lookup"><span data-stu-id="95b13-132">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="95b13-133">2 番目のオーバー ロードが必要な拡大が少ないので、コンパイラは、呼び出しの使用します。</span><span class="sxs-lookup"><span data-stu-id="95b13-133">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="95b13-134">2 番目の呼び出しで、コンパイラは縮小に基づいてオーバー ロードのいずれかを取り除くことはできません。</span><span class="sxs-lookup"><span data-stu-id="95b13-134">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="95b13-135">除外した引数型の&2; 番目のオーバー ロードを呼び出すことがあるため、最初の呼び出しと同様に、同じ理由から&3; 番目のオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="95b13-135">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="95b13-136">ただし、コンパイラは、最初と&2; 番目のオーバー ロードの間で解決できません。</span><span class="sxs-lookup"><span data-stu-id="95b13-136">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="95b13-137">もう一方で対応する型を拡張する&1; つの定義済みパラメーターの型を持つ各 (`Byte`に`Short`が`Single`に`Double`)。</span><span class="sxs-lookup"><span data-stu-id="95b13-137">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="95b13-138">そのため、コンパイラは、オーバー ロードの解決エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="95b13-138">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="95b13-139">省略可能なオーバー ロードと ParamArray 引数</span><span class="sxs-lookup"><span data-stu-id="95b13-139">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="95b13-140">最後のパラメーターを宣言する点を除いて、プロシージャの&2; つのオーバー ロードと同じシグネチャを持つ場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 、もう一方で、コンパイラは解決そのプロシージャを呼び出す次のようにします。</span><span class="sxs-lookup"><span data-stu-id="95b13-140">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="95b13-141">呼び出しが最後の引数として指定した場合</span><span class="sxs-lookup"><span data-stu-id="95b13-141">If the call supplies the last argument as</span></span>|<span data-ttu-id="95b13-142">コンパイラは最後の引数として宣言するオーバー ロードの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="95b13-142">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="95b13-143">値なし (引数を省略すると)</span><span class="sxs-lookup"><span data-stu-id="95b13-143">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="95b13-144">1 つの値</span><span class="sxs-lookup"><span data-stu-id="95b13-144">A single value</span></span>|`Optional`|  
|<span data-ttu-id="95b13-145">コンマ区切りの一覧で、2 つ以上の値</span><span class="sxs-lookup"><span data-stu-id="95b13-145">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="95b13-146">(空の配列を含む) 任意の長さの配列</span><span class="sxs-lookup"><span data-stu-id="95b13-146">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="95b13-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="95b13-147">See Also</span></span>  
 <span data-ttu-id="95b13-148">[省略可能なパラメーター](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-148">[Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="95b13-149"> [パラメーター配列](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-149"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="95b13-150"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-150"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="95b13-151"> [トラブルシューティングの手順](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-151"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="95b13-152"> [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-152"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="95b13-153"> [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-153"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="95b13-154"> [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-154"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="95b13-155"> [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-155"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="95b13-156"> [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-156"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="95b13-157"> [オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="95b13-157"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="95b13-158"> [拡張メソッド](./extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="95b13-158"> [Extension Methods](./extension-methods.md)</span></span>
