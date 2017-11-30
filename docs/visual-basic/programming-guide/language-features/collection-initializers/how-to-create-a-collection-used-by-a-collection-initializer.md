---
title: "方法: コレクション初期化子を使用してコレクションを作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cff862f16530bc268628d9406ae81d23f2761926
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="7b433-102">方法: コレクション初期化子を使用してコレクションを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b433-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="7b433-103">コレクション初期化子を使用してコレクションを作成するときに、Visual Basic コンパイラはの検索、`Add`対象のコレクション型のメソッドのパラメーター、`Add`メソッド、コレクション初期化子内の値の型に一致します。</span><span class="sxs-lookup"><span data-stu-id="7b433-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="7b433-104">これは、`Add`メソッドを使用して、コレクション初期化子から値を持つコレクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="7b433-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b433-105">例</span><span class="sxs-lookup"><span data-stu-id="7b433-105">Example</span></span>  
 <span data-ttu-id="7b433-106">次の例は、`OrderCollection`パブリックを含んだコレクション`Add`コレクション初期化子を使用して型のオブジェクトを追加するメソッド`Order`です。</span><span class="sxs-lookup"><span data-stu-id="7b433-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="7b433-107">`Add`メソッドでは、簡略化されたコレクションの初期化子構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="7b433-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7b433-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b433-108">See Also</span></span>  
 [<span data-ttu-id="7b433-109">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="7b433-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="7b433-110">方法: コレクション初期化子で使用される拡張メソッドを作成または追加する</span><span class="sxs-lookup"><span data-stu-id="7b433-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
