---
title: "省略可能な引数には、既定値を指定する必要があります。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords: BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9ec6d044ba0a1bb904030ddbb4c4fa406c3ba63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="7af19-102">省略可能な引数には、既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af19-102">Optional parameters must specify a default value</span></span>
<span data-ttu-id="7af19-103">省略可能なパラメーターは、呼び出し元のプロシージャでパラメーターが指定されていない場合に使用できる既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7af19-103">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>  
  
 <span data-ttu-id="7af19-104">**エラー ID:** BC30812</span><span class="sxs-lookup"><span data-stu-id="7af19-104">**Error ID:** BC30812</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7af19-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7af19-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7af19-106">省略可能なパラメーターの既定値を指定します例えば：</span><span class="sxs-lookup"><span data-stu-id="7af19-106">Specify default values for optional parameters; for example:</span></span>  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7af19-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="7af19-107">See Also</span></span>  
 [<span data-ttu-id="7af19-108">Optional</span><span class="sxs-lookup"><span data-stu-id="7af19-108">Optional</span></span>](../../../visual-basic/language-reference/modifiers/optional.md)
