---
title: Visual Basic における変数
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7a47ad7e4ade9f15159c27ac672aeb937a05493
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="fd283-102">Visual Basic における変数</span><span class="sxs-lookup"><span data-stu-id="fd283-102">Variables in Visual Basic</span></span>
<span data-ttu-id="fd283-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で計算を行う場合、しばしば値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd283-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="fd283-104">たとえば、いくつかの値を計算し、比較し、比較の結果に応じて、さまざまな操作を実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="fd283-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="fd283-105">比較する場合には、その値を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd283-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="fd283-106">使用方法</span><span class="sxs-lookup"><span data-stu-id="fd283-106">Usage</span></span>  
 <span data-ttu-id="fd283-107">他のほとんどのプログラミング言語と同じように、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では値の格納に変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="fd283-107">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="fd283-108">*変数*には (変数に含まれる値を参照するために使用する語である) 名前があります。</span><span class="sxs-lookup"><span data-stu-id="fd283-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="fd283-109">変数には、(変数に格納できるデータの種類を決定する) データ型もあります。</span><span class="sxs-lookup"><span data-stu-id="fd283-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="fd283-110">密接に関連するデータ項目のインデックス セットを格納する必要がある場合、変数で配列を表現することもできます。</span><span class="sxs-lookup"><span data-stu-id="fd283-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="fd283-111">ローカル型推論では、データ型を明示的に指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="fd283-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="fd283-112">代わりに、コンパイラは、初期化式の型から変数の型を推測します。</span><span class="sxs-lookup"><span data-stu-id="fd283-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="fd283-113">詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」と「[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd283-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="fd283-114">値の代入</span><span class="sxs-lookup"><span data-stu-id="fd283-114">Assigning Values</span></span>  
 <span data-ttu-id="fd283-115">次の例のように、計算を実行し、結果を変数に割り当てるために、代入ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fd283-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="fd283-116">この例の等号 (`=`) は、等値演算子ではなく代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="fd283-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="fd283-117">この値は、変数 `applesSold` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="fd283-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="fd283-118">詳細については、「[方法 : 変数に値を格納する、および変数から値を取得する](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd283-118">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="fd283-119">変数とプロパティ</span><span class="sxs-lookup"><span data-stu-id="fd283-119">Variables and Properties</span></span>  
 <span data-ttu-id="fd283-120">変数と同様に、*プロパティ*はアクセス可能な値です。</span><span class="sxs-lookup"><span data-stu-id="fd283-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="fd283-121">ただし、変数よりも複雑です。</span><span class="sxs-lookup"><span data-stu-id="fd283-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="fd283-122">プロパティは、その値を設定し取得する方法を制御するコード ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd283-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="fd283-123">詳細については、「[Visual Basic のプロパティと変数の違い](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd283-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd283-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd283-124">See Also</span></span>  
 [<span data-ttu-id="fd283-125">変数宣言</span><span class="sxs-lookup"><span data-stu-id="fd283-125">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="fd283-126">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="fd283-126">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="fd283-127">変数のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fd283-127">Troubleshooting Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [<span data-ttu-id="fd283-128">方法 : 変数に値を格納する、および変数から値を取得する</span><span class="sxs-lookup"><span data-stu-id="fd283-128">How to: Move Data Into and Out of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [<span data-ttu-id="fd283-129">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="fd283-129">Differences Between Properties and Variables in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [<span data-ttu-id="fd283-130">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="fd283-130">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
