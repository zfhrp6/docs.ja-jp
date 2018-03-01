---
title: "ループ コントロール変数として宣言された配列を初期サイズで宣言することはできません"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef36f14d5323a4592afe59573e249d8cfb218df9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="268b3-102">ループ コントロール変数として宣言された配列を初期サイズで宣言することはできません</span><span class="sxs-lookup"><span data-stu-id="268b3-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="268b3-103">A`For Each`ループとして配列を使用してその*要素*繰り返し変数がその配列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="268b3-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="268b3-104">次のステートメントでは、このエラーを生成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="268b3-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="268b3-105">最初の`For Each`ステートメントの要素にアクセスするための正しい方法は、`arrayList`です。</span><span class="sxs-lookup"><span data-stu-id="268b3-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="268b3-106">2 番目`For Each`ステートメントは、このエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="268b3-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="268b3-107">**エラー ID:** BC32039</span><span class="sxs-lookup"><span data-stu-id="268b3-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="268b3-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="268b3-108">To correct this error</span></span>  
  
-   <span data-ttu-id="268b3-109">宣言から初期化を削除、*要素*繰り返し変数。</span><span class="sxs-lookup"><span data-stu-id="268b3-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="268b3-110">参照</span><span class="sxs-lookup"><span data-stu-id="268b3-110">See Also</span></span>  
 [<span data-ttu-id="268b3-111">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="268b3-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="268b3-112">配列</span><span class="sxs-lookup"><span data-stu-id="268b3-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="268b3-113">コレクション</span><span class="sxs-lookup"><span data-stu-id="268b3-113">Collections</span></span>](../../../standard/collections/index.md)
