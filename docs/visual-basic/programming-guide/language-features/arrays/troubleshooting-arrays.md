---
title: "配列のトラブルシューティング (Visual Basic) |Microsoft ドキュメント"
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
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: 17
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
ms.openlocfilehash: 571731ae7066ba7ec52d4a2413b4d948f3f35bfe
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-arrays-visual-basic"></a><span data-ttu-id="eef61-102">配列のトラブルシューティング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eef61-102">Troubleshooting Arrays (Visual Basic)</span></span>
<span data-ttu-id="eef61-103">ここでは、配列を扱うときに発生する一般的な問題についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="eef61-103">This page lists some common problems that can occur when working with arrays.</span></span>  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a><span data-ttu-id="eef61-104">コンパイル エラーを宣言して、配列の初期化</span><span class="sxs-lookup"><span data-stu-id="eef61-104">Compilation Errors Declaring and Initializing an Array</span></span>  
 <span data-ttu-id="eef61-105">コンパイル エラーは、宣言、作成、および配列の初期化の規則の誤解から発生します。</span><span class="sxs-lookup"><span data-stu-id="eef61-105">Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays.</span></span> <span data-ttu-id="eef61-106">エラーの最も一般的な原因として、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eef61-106">The most common causes of errors are the following:</span></span>  
  
-   <span data-ttu-id="eef61-107">指定すること、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)配列変数の宣言に次元の長さを指定した後の句。</span><span class="sxs-lookup"><span data-stu-id="eef61-107">Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration.</span></span> <span data-ttu-id="eef61-108">次のコード行では、この型の無効な宣言を表示します。</span><span class="sxs-lookup"><span data-stu-id="eef61-108">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   <span data-ttu-id="eef61-109">ジャグ配列の最上位の配列の次元の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="eef61-109">Specifying dimension lengths for more than the top-level array of a jagged array.</span></span> <span data-ttu-id="eef61-110">次のコード行では、この型の無効な宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="eef61-110">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   <span data-ttu-id="eef61-111">省略すると、`New`キーワードは要素の値を指定する場合。</span><span class="sxs-lookup"><span data-stu-id="eef61-111">Omitting the `New` keyword when specifying the element values.</span></span> <span data-ttu-id="eef61-112">次のコード行では、この型の無効な宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="eef61-112">The following code line shows an invalid declaration of this type.</span></span>  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   <span data-ttu-id="eef61-113">指定すること、`New`句なしで中かっこ (`{}`)。</span><span class="sxs-lookup"><span data-stu-id="eef61-113">Supplying a `New` clause without braces (`{}`).</span></span> <span data-ttu-id="eef61-114">次のコード行では、この型の無効な宣言を表示します。</span><span class="sxs-lookup"><span data-stu-id="eef61-114">The following code lines show invalid declarations of this type.</span></span>  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a><span data-ttu-id="eef61-115">配列の範囲外にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="eef61-115">Accessing an Array Out of Bounds</span></span>  
 <span data-ttu-id="eef61-116">配列を初期化するプロセスは、各次元に、上限と下限の境界を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="eef61-116">The process of initializing an array assigns an upper bound and a lower bound to each dimension.</span></span> <span data-ttu-id="eef61-117">配列の要素へのアクセスには、有効なインデックスまたは添字のすべてのディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="eef61-117">Every access to an element of the array must specify a valid index, or subscript, for every dimension.</span></span> <span data-ttu-id="eef61-118">下限またはその上限を超えて任意のインデックスがある場合、<xref:System.IndexOutOfRangeException>例外が発生します</xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="eef61-118">If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results.</span></span> <span data-ttu-id="eef61-119">コンパイラは、実行時にエラーが発生したため、このようなエラーを検出できません。</span><span class="sxs-lookup"><span data-stu-id="eef61-119">The compiler cannot detect such an error, so an error occurs at run time.</span></span>  
  
### <a name="determining-bounds"></a><span data-ttu-id="eef61-120">範囲の確認</span><span class="sxs-lookup"><span data-stu-id="eef61-120">Determining Bounds</span></span>  
 <span data-ttu-id="eef61-121">別のコンポーネントは、配列をコードに合格した場合など、プロシージャの引数としてわからないその配列のサイズまたはその次元の長さ。</span><span class="sxs-lookup"><span data-stu-id="eef61-121">If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions.</span></span> <span data-ttu-id="eef61-122">要素にアクセスしようとする前に、配列のすべての次元の上限の境界を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="eef61-122">You should always determine the upper bound for every dimension of an array before you attempt to access any elements.</span></span> <span data-ttu-id="eef61-123">かどうか、配列が作成されてなんらかの方法で以外の場合、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New`句、下限の境界、0 以外の場合がありますおよびが安全にもその下限の境界を決定します。</span><span class="sxs-lookup"><span data-stu-id="eef61-123">If the array has been created by some means other than a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.</span></span>  
  
### <a name="specifying-the-dimension"></a><span data-ttu-id="eef61-124">ディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="eef61-124">Specifying the Dimension</span></span>  
 <span data-ttu-id="eef61-125">多次元配列の境界を決定する際は、ディメンションを指定する方法ように注意します。</span><span class="sxs-lookup"><span data-stu-id="eef61-125">When determining the bounds of a multidimensional array, take care how you specify the dimension.</span></span> <span data-ttu-id="eef61-126">`dimension`のパラメーター、<xref:System.Array.GetLowerBound%2A>と<xref:System.Array.GetUpperBound%2A>メソッドは、中に、0 から始まる、`Rank`のパラメーター、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A>と<xref:Microsoft.VisualBasic.Information.UBound%2A>関数は、1 から始まります</xref:Microsoft.VisualBasic.Information.UBound%2A></xref:Microsoft.VisualBasic.Information.LBound%2A></xref:System.Array.GetUpperBound%2A></xref:System.Array.GetLowerBound%2A>。</span><span class="sxs-lookup"><span data-stu-id="eef61-126">The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef61-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="eef61-127">See Also</span></span>  
 <span data-ttu-id="eef61-128">[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="eef61-128">[Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="eef61-129"> [方法: Visual Basic で配列変数を初期化](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="eef61-129"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
