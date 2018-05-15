---
title: '方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: c1b79f1b6a9768941d6fe966c5b5886ea742f808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="7da42-102">方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7da42-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="7da42-103">*現在のインスタンス*オブジェクトが現在のコードが実行されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="7da42-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="7da42-104">使用する、`Me`キーワードを現在のインスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="7da42-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="7da42-105">現在のインスタンスを参照するには</span><span class="sxs-lookup"><span data-stu-id="7da42-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="7da42-106">使用して、`Me`オブジェクト変数の名前をここで通常使用するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="7da42-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="7da42-107">`Me`オブジェクトのように動作変数、宣言またはできませんに割り当てるものです。</span><span class="sxs-lookup"><span data-stu-id="7da42-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="7da42-108">`Me` 現在のインスタンスを指します。</span><span class="sxs-lookup"><span data-stu-id="7da42-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da42-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="7da42-109">See Also</span></span>  
 [<span data-ttu-id="7da42-110">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="7da42-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="7da42-111">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="7da42-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="7da42-112">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="7da42-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
