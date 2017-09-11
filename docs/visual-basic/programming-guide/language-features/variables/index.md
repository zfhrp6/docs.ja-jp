---
title: "Visual Basic における変数"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2fdc670bf4f17000809e75e32c32edb39abf0fed
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="cd651-102">Visual Basic における変数</span><span class="sxs-lookup"><span data-stu-id="cd651-102">Variables in Visual Basic</span></span>
<span data-ttu-id="cd651-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で計算を行う場合、しばしば値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd651-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="cd651-104">たとえば、いくつかの値を計算し、比較し、比較の結果に応じて、さまざまな操作を実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="cd651-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="cd651-105">比較する場合には、その値を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd651-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="cd651-106">使用方法</span><span class="sxs-lookup"><span data-stu-id="cd651-106">Usage</span></span>  
 <span data-ttu-id="cd651-107">他のほとんどのプログラミング言語と同じように、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] では値の格納に変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd651-107">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="cd651-108">*変数*には (変数に含まれる値を参照するために使用する語である) 名前があります。</span><span class="sxs-lookup"><span data-stu-id="cd651-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="cd651-109">変数には、(変数に格納できるデータの種類を決定する) データ型もあります。</span><span class="sxs-lookup"><span data-stu-id="cd651-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="cd651-110">密接に関連するデータ項目のインデックス セットを格納する必要がある場合、変数で配列を表現することもできます。</span><span class="sxs-lookup"><span data-stu-id="cd651-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="cd651-111">ローカル型推論では、データ型を明示的に指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="cd651-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="cd651-112">代わりに、コンパイラは、初期化式の型から変数の型を推測します。</span><span class="sxs-lookup"><span data-stu-id="cd651-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="cd651-113">詳細については、「[ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」と「[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd651-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="cd651-114">値の代入</span><span class="sxs-lookup"><span data-stu-id="cd651-114">Assigning Values</span></span>  
 <span data-ttu-id="cd651-115">次の例のように、計算を実行し、結果を変数に割り当てるために、代入ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd651-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 <span data-ttu-id="cd651-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cd651-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd651-117">この例の等号 (`=`) は、等値演算子ではなく代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="cd651-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="cd651-118">この値は、変数 `applesSold` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cd651-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="cd651-119">詳細については、「[方法 : 変数に値を格納する、および変数から値を取得する](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd651-119">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="cd651-120">変数とプロパティ</span><span class="sxs-lookup"><span data-stu-id="cd651-120">Variables and Properties</span></span>  
 <span data-ttu-id="cd651-121">変数と同様に、*プロパティ*はアクセス可能な値です。</span><span class="sxs-lookup"><span data-stu-id="cd651-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="cd651-122">ただし、変数よりも複雑です。</span><span class="sxs-lookup"><span data-stu-id="cd651-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="cd651-123">プロパティは、その値を設定し取得する方法を制御するコード ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd651-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="cd651-124">詳細については、「[Visual Basic のプロパティと変数の違い](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd651-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd651-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd651-125">See Also</span></span>  
 <span data-ttu-id="cd651-126">[変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="cd651-126">[Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
 <span data-ttu-id="cd651-127">[オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="cd651-127">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
 <span data-ttu-id="cd651-128">[変数のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="cd651-128">[Troubleshooting Variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span></span>  
 <span data-ttu-id="cd651-129">[方法 : 変数に値を格納する、および変数から値を取得する](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="cd651-129">[How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
 <span data-ttu-id="cd651-130">[Visual Basic のプロパティと変数の違い](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="cd651-130">[Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span></span>  
 [<span data-ttu-id="cd651-131">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="cd651-131">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

