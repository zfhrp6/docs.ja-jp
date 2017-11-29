---
title: "方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="0a2f1-102">方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a2f1-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="0a2f1-103">*現在のインスタンス*オブジェクトが現在のコードが実行されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="0a2f1-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="0a2f1-104">使用する、`Me`キーワードを現在のインスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="0a2f1-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="0a2f1-105">現在のインスタンスを参照するには</span><span class="sxs-lookup"><span data-stu-id="0a2f1-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="0a2f1-106">使用して、`Me`オブジェクト変数の名前をここで通常使用するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="0a2f1-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="0a2f1-107">`Me`オブジェクトのように動作変数、宣言またはできませんに割り当てるものです。</span><span class="sxs-lookup"><span data-stu-id="0a2f1-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="0a2f1-108">`Me`現在のインスタンスを指します。</span><span class="sxs-lookup"><span data-stu-id="0a2f1-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2f1-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a2f1-109">See Also</span></span>  
 [<span data-ttu-id="0a2f1-110">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="0a2f1-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="0a2f1-111">オブジェクト変数の代入</span><span class="sxs-lookup"><span data-stu-id="0a2f1-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="0a2f1-112">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="0a2f1-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
