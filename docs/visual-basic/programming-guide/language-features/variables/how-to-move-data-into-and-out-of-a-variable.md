---
title: '方法: 変数に値を格納する、および変数から値を取得する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bfda451cefff699561253910715d8450414b00ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650869"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="7f044-102">方法: 変数に値を格納する、および変数から値を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f044-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="7f044-103">変数に値を格納するには、代入ステートメントの左側にある変数名を置きます。</span><span class="sxs-lookup"><span data-stu-id="7f044-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="7f044-104">変数にデータを配置します。</span><span class="sxs-lookup"><span data-stu-id="7f044-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="7f044-105">変数に値を格納するには</span><span class="sxs-lookup"><span data-stu-id="7f044-105">To store a value in a variable</span></span>  
  
-   <span data-ttu-id="7f044-106">代入ステートメントの左側にある変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f044-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="7f044-107">次の例は、変数の値を設定`alpha`です。</span><span class="sxs-lookup"><span data-stu-id="7f044-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="7f044-108">代入ステートメントの右側にある生成された値は、変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="7f044-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="7f044-109">変数からのデータの取得</span><span class="sxs-lookup"><span data-stu-id="7f044-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="7f044-110">変数の値を取得するには、式の中で変数名を含めます。</span><span class="sxs-lookup"><span data-stu-id="7f044-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="7f044-111">変数から値を取得するには</span><span class="sxs-lookup"><span data-stu-id="7f044-111">To retrieve a value from a variable</span></span>  
  
-   <span data-ttu-id="7f044-112">式の中で、変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f044-112">Use the variable name in an expression.</span></span> <span data-ttu-id="7f044-113">変数を使用する任意の場所で使用できる、定数またはリテラルを除き、定数の値を定義する式。</span><span class="sxs-lookup"><span data-stu-id="7f044-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="7f044-114">- または -</span><span class="sxs-lookup"><span data-stu-id="7f044-114">-or-</span></span>  
  
-   <span data-ttu-id="7f044-115">等号の後、変数名を使用して (`=`) 代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="7f044-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="7f044-116">次の例は、変数の値を読み取ります`startValue`し、変数の値を使用して`counter`式でします。</span><span class="sxs-lookup"><span data-stu-id="7f044-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="7f044-117">変数の値は、のみと同じよう、定数、変数または代入ステートメントの左側にあるプロパティに格納し、式に参加します。</span><span class="sxs-lookup"><span data-stu-id="7f044-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f044-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f044-118">See Also</span></span>  
 [<span data-ttu-id="7f044-119">変数</span><span class="sxs-lookup"><span data-stu-id="7f044-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="7f044-120">変数宣言</span><span class="sxs-lookup"><span data-stu-id="7f044-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="7f044-121">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="7f044-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
