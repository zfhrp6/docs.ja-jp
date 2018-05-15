---
title: 初期化子が必要です
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 9d786fd1e929129c420b7bec62efd0bd445d85eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="initializer-expected"></a><span data-ttu-id="49348-102">初期化子が必要です</span><span class="sxs-lookup"><span data-stu-id="49348-102">Initializer expected</span></span>
<span data-ttu-id="49348-103">初期化リストが空で、次の例で示すように、オブジェクト初期化子を使用して、クラスのインスタンスを宣言しようとしました。</span><span class="sxs-lookup"><span data-stu-id="49348-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="49348-104">次の例で示すように、少なくとも 1 つのフィールドまたはプロパティは初期化子リストで初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49348-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="49348-105">**エラー ID:** BC30996</span><span class="sxs-lookup"><span data-stu-id="49348-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49348-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="49348-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="49348-107">少なくとも 1 つのフィールドまたはプロパティの初期化子で初期化またはオブジェクト初期化子を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="49348-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49348-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="49348-108">See Also</span></span>  
 [<span data-ttu-id="49348-109">オブジェクト初期化子 : 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="49348-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="49348-110">方法 : オブジェクト初期化子を使用してオブジェクトを宣言する</span><span class="sxs-lookup"><span data-stu-id="49348-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
