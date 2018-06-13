---
title: Visual Basic における変数
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 79cd5629d4de6279eb370c18db617a5ad532108d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654474"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="a962a-102">Visual Basic における変数</span><span class="sxs-lookup"><span data-stu-id="a962a-102">Variables in Visual Basic</span></span>
<span data-ttu-id="a962a-103">多くの場合、Visual Basic を使用して計算を実行するときに、値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a962a-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="a962a-104">たとえば、いくつかの値を計算し、比較し、比較の結果に応じて、さまざまな操作を実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="a962a-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="a962a-105">比較する場合には、その値を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a962a-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="a962a-106">使用法</span><span class="sxs-lookup"><span data-stu-id="a962a-106">Usage</span></span>  
 <span data-ttu-id="a962a-107">Visual Basic では、ほとんどのプログラミング言語と同じように変数を使用して値を格納します。</span><span class="sxs-lookup"><span data-stu-id="a962a-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="a962a-108">*変数*には (変数に含まれる値を参照するために使用する語である) 名前があります。</span><span class="sxs-lookup"><span data-stu-id="a962a-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="a962a-109">変数には、(変数に格納できるデータの種類を決定する) データ型もあります。</span><span class="sxs-lookup"><span data-stu-id="a962a-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="a962a-110">密接に関連するデータ項目のインデックス セットを格納する必要がある場合、変数で配列を表現することもできます。</span><span class="sxs-lookup"><span data-stu-id="a962a-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="a962a-111">ローカル型推論では、データ型を明示的に指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="a962a-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="a962a-112">代わりに、コンパイラは、初期化式の型から変数の型を推測します。</span><span class="sxs-lookup"><span data-stu-id="a962a-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="a962a-113">詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」と「[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a962a-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="a962a-114">値の代入</span><span class="sxs-lookup"><span data-stu-id="a962a-114">Assigning Values</span></span>  
 <span data-ttu-id="a962a-115">次の例のように、計算を実行し、結果を変数に割り当てるために、代入ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a962a-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="a962a-116">この例の等号 (`=`) は、等値演算子ではなく代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="a962a-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="a962a-117">この値は、変数 `applesSold` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a962a-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="a962a-118">詳細については、「[方法 : 変数に値を格納する、および変数から値を取得する](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a962a-118">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="a962a-119">変数とプロパティ</span><span class="sxs-lookup"><span data-stu-id="a962a-119">Variables and Properties</span></span>  
 <span data-ttu-id="a962a-120">変数と同様に、*プロパティ*はアクセス可能な値です。</span><span class="sxs-lookup"><span data-stu-id="a962a-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="a962a-121">ただし、変数よりも複雑です。</span><span class="sxs-lookup"><span data-stu-id="a962a-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="a962a-122">プロパティは、その値を設定し取得する方法を制御するコード ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="a962a-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="a962a-123">詳細については、「[Visual Basic のプロパティと変数の違い](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a962a-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a962a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a962a-124">See Also</span></span>  
 [<span data-ttu-id="a962a-125">変数宣言</span><span class="sxs-lookup"><span data-stu-id="a962a-125">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="a962a-126">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="a962a-126">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="a962a-127">変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a962a-127">Troubleshooting Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [<span data-ttu-id="a962a-128">方法 : 変数に値を格納する、および変数から値を取得する</span><span class="sxs-lookup"><span data-stu-id="a962a-128">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="a962a-129">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="a962a-129">Differences Between Properties and Variables in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [<span data-ttu-id="a962a-130">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="a962a-130">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
