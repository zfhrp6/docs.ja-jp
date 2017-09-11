---
title: "方法: 不特定数のパラメーター (Visual Basic) を受け取るプロシージャをオーバー ロード |Microsoft ドキュメント"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: 3e4ef81049f3b0d3ab1271fb709f07c37f274a88
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="aec66-102">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aec66-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="aec66-103">プロシージャがある場合、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、パラメーター配列の&1; 次元配列を取得するオーバー ロードされたバージョンを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="aec66-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="aec66-104">詳細については、「暗黙的なオーバー ロードに、ParamArray パラメーター」を参照してください[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="aec66-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="aec66-105">可変個のパラメーターを受け取るプロシージャをオーバー ロードするには</span><span class="sxs-lookup"><span data-stu-id="aec66-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="aec66-106">プロシージャは、コードのロジックとメリットを呼び出すことがから複数のバージョンのオーバー ロードされたことを確認、`ParamArray`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="aec66-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="aec66-107">「オーバー ロードと Paramarray」を参照してください[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="aec66-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="aec66-108">パラメーター リストの可変部分で、プロシージャが受け取る指定された値の数を決定します。</span><span class="sxs-lookup"><span data-stu-id="aec66-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="aec66-109">値がない場合が挙げられ、1 つの&1; 次元配列の大文字と小文字を含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="aec66-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="aec66-110">指定された値の許容数ごとに、書き込み、`Sub`または`Function`対応するパラメーター リストを定義する宣言ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="aec66-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="aec66-111">使用しないで、`Optional`または`ParamArray`このオーバー ロードされたバージョンのキーワードです。</span><span class="sxs-lookup"><span data-stu-id="aec66-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="aec66-112">各宣言の前に、`Sub`または`Function`キーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="aec66-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="aec66-113">次の各宣言には、呼び出し元のコードには、その宣言のパラメーター リストに対応する値が指定されている場合に実行するプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="aec66-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="aec66-114">各プロシージャの終了、`End Sub`または`End Function`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="aec66-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aec66-115">例</span><span class="sxs-lookup"><span data-stu-id="aec66-115">Example</span></span>  
 <span data-ttu-id="aec66-116">次の例で定義された手順を示しています、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、および、同等の一連のオーバー ロードされたプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="aec66-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 <span data-ttu-id="aec66-117">[!code-vb[VbVbcnProcedures #&69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="aec66-117">[!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span></span>  
  
 <span data-ttu-id="aec66-118">[!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="aec66-118">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span></span>  
  
 <span data-ttu-id="aec66-119">パラメーター配列の&1; 次元配列を受け取り、パラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="aec66-119">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="aec66-120">ただし、その他の暗黙のオーバー ロードの署名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="aec66-120">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="aec66-121">次の宣言では、これを示しています。</span><span class="sxs-lookup"><span data-stu-id="aec66-121">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="aec66-122">[!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="aec66-122">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span></span>  
  
 <span data-ttu-id="aec66-123">オーバー ロードされたバージョンのコードは呼び出し元のコードの&1; つまたは複数の値を指定するかどうかをテストする必要はありません、`ParamArray`パラメーター、その場合、または数。</span><span class="sxs-lookup"><span data-stu-id="aec66-123">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="aec66-124">呼び出しの引数リストに一致するバージョンに制御を渡す。</span><span class="sxs-lookup"><span data-stu-id="aec66-124"> passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aec66-125">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="aec66-125">Compiling the Code</span></span>  
 <span data-ttu-id="aec66-126">の手順、`ParamArray`パラメーターは、一連のオーバー ロードされたバージョンに、これらの暗黙的なオーバー ロードのいずれかに対応する、パラメーター リストでこのようなプロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="aec66-126">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="aec66-127">詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="aec66-127">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="aec66-128">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="aec66-128">.NET Framework Security</span></span>  
 <span data-ttu-id="aec66-129">無制限に大きくなる可能性の配列を処理するたびに、アプリケーションの内部の容量を超過してしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aec66-129">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="aec66-130">パラメーターの配列を受け取る場合に、呼び出し元のコードが渡された配列の長さをテストし、アプリケーションに対して大きすぎる場合は、適切な手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="aec66-130">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec66-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="aec66-131">See Also</span></span>  
 <span data-ttu-id="aec66-132">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-132">[Procedures](./index.md) </span></span>  
<span data-ttu-id="aec66-133"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-133"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="aec66-134"> [省略可能なパラメーター](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-134"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="aec66-135"> [パラメーター配列](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-135"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="aec66-136"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="aec66-137"> [トラブルシューティングの手順](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="aec66-138"> [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-138"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="aec66-139"> [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-139"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="aec66-140"> [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="aec66-140"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="aec66-141"> [オーバーロードの解決](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="aec66-141"> [Overload Resolution](./overload-resolution.md)</span></span>
