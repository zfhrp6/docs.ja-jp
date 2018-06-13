---
title: '方法 : Visual Basic でオブジェクト変数を宣言し、オブジェクト変数にオブジェクトを代入する'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648877"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="d2226-102">方法 : Visual Basic でオブジェクト変数を宣言し、オブジェクト変数にオブジェクトを代入する</span><span class="sxs-lookup"><span data-stu-id="d2226-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="d2226-103">変数を宣言する、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)を指定して`As Object`で、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="d2226-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="d2226-104">等号の後、オブジェクトを配置することによってこのような変数にオブジェクトを割り当てる (`=`) 代入ステートメントまたは初期化句でします。</span><span class="sxs-lookup"><span data-stu-id="d2226-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2226-105">例</span><span class="sxs-lookup"><span data-stu-id="d2226-105">Example</span></span>  
 <span data-ttu-id="d2226-106">次の例で、`Object`変数と、現在のインスタンスに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d2226-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="d2226-107">宣言と割り当てを結合するには、宣言の一部として変数を初期化します。</span><span class="sxs-lookup"><span data-stu-id="d2226-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="d2226-108">次の例では、上記の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="d2226-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2226-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d2226-109">Compiling the Code</span></span>  
 <span data-ttu-id="d2226-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d2226-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d2226-111"><xref:System> 名前空間への参照</span><span class="sxs-lookup"><span data-stu-id="d2226-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="d2226-112">クラス、構造体、または配置するモジュール、`Dim`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d2226-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="d2226-113">代入ステートメントを記述するためのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d2226-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2226-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2226-114">See Also</span></span>  
 [<span data-ttu-id="d2226-115">変数宣言</span><span class="sxs-lookup"><span data-stu-id="d2226-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="d2226-116">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="d2226-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="d2226-117">オブジェクト変数の宣言</span><span class="sxs-lookup"><span data-stu-id="d2226-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="d2226-118">Object 型</span><span class="sxs-lookup"><span data-stu-id="d2226-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="d2226-119">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="d2226-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="d2226-120">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="d2226-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="d2226-121">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="d2226-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
