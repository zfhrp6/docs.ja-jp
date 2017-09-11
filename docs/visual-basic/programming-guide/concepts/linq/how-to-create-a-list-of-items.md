---
title: "方法: 項目のリストを作成する |Microsoft ドキュメント"
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
- list [LINQ in Visual Basic]
- objects [Visual Basic], list of items
ms.assetid: fe941aba-6340-455c-8b1f-ffd9c3eb1ac5
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ad0d2dfd38e30ddff1a5b030ec1ace884539d134
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-list-of-items"></a><span data-ttu-id="26c26-102">方法: 項目のリストを作成する</span><span class="sxs-lookup"><span data-stu-id="26c26-102">How to: Create a List of Items</span></span>
<span data-ttu-id="26c26-103">このトピックのコードでは、`Student` クラスを定義し、クラスのインスタンスのリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c26-103">The code in this topic defines a `Student` class and creates a list of instances of the class.</span></span> <span data-ttu-id="26c26-104">リストは、トピックをサポートするために、[チュートリアル: Visual Basic でクエリを記述](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)します。</span><span class="sxs-lookup"><span data-stu-id="26c26-104">The list is designed to support the topic [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span> <span data-ttu-id="26c26-105">これは、オブジェクトのリストを必要とする任意のアプリケーションにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="26c26-105">It also can be used for any application that requires a list of objects.</span></span> <span data-ttu-id="26c26-106">このコードでは、オブジェクト初期化子を使用することで、学生のリスト内の各項目を定義します。</span><span class="sxs-lookup"><span data-stu-id="26c26-106">The code defines the items in the list of students by using object initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26c26-107">例</span><span class="sxs-lookup"><span data-stu-id="26c26-107">Example</span></span>  
 <span data-ttu-id="26c26-108">チュートリアルを実行している場合は、そのチュートリアルで作成するプロジェクトの Module1.vb ファイルとして、このコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="26c26-108">If you are working on the walkthrough, you can use this code for the Module1.vb file of the project that is created there.</span></span> <span data-ttu-id="26c26-109">`Main` メソッドの **** でマークされた行を、チュートリアルで指定されたクエリとクエリ実行に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="26c26-109">Just replace the lines marked with **** in the `Main` method with the queries and query executions that are provided in the walkthrough.</span></span>  
  
 <span data-ttu-id="26c26-110">[!code-vb[VbLINQHowToCreateList&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/how-to-create-a-list-of-items_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="26c26-110">[!code-vb[VbLINQHowToCreateList#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/how-to-create-a-list-of-items_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c26-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="26c26-111">See Also</span></span>  
 <span data-ttu-id="26c26-112">[チュートリアル: Visual Basic でのクエリの作成](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md) </span><span class="sxs-lookup"><span data-stu-id="26c26-112">[Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md) </span></span>  
<span data-ttu-id="26c26-113"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="26c26-113"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="26c26-114"> [オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="26c26-114"> [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="26c26-115"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="26c26-115"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="26c26-116"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="26c26-116"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="26c26-117"> [クエリ](../../../../visual-basic/language-reference/queries/queries.md)</span><span class="sxs-lookup"><span data-stu-id="26c26-117"> [Queries](../../../../visual-basic/language-reference/queries/queries.md)</span></span>
