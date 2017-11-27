---
title: "匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords: BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7068928a17ee5fdb7bf6b5e0a40aaa7e5ef32f11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="b2157-102">匿名型メンバーの名前は、引数なしの簡易名または修飾名からのみ推論できます</span><span class="sxs-lookup"><span data-stu-id="b2157-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="b2157-103">複雑な式からは、匿名型メンバーの名前を推論することはできません。</span><span class="sxs-lookup"><span data-stu-id="b2157-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="b2157-104">匿名型元となることができます、メンバー名と型を推論できませんソースの詳細については、次を参照してください。[する方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2157-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="b2157-105">**エラー ID:** BC36556</span><span class="sxs-lookup"><span data-stu-id="b2157-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b2157-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="b2157-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b2157-107">次のコードに示すように、メンバー名に式を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b2157-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b2157-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2157-108">See Also</span></span>  
 [<span data-ttu-id="b2157-109">匿名型</span><span class="sxs-lookup"><span data-stu-id="b2157-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="b2157-110">方法 : 匿名型の宣言におけるプロパティ名と型を推論する</span><span class="sxs-lookup"><span data-stu-id="b2157-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
