---
title: '方法: コレクション初期化子で使用される拡張メソッドを作成または追加する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 5e35ad80037e843fd3cbd9caa68dcb2a09d707e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646241"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="d70f0-102">方法: コレクション初期化子で使用される拡張メソッドを作成または追加する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d70f0-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="d70f0-103">コレクション初期化子を使用してコレクションを作成するときに、Visual Basic コンパイラはの検索、`Add`対象のコレクション型のメソッドのパラメーター、`Add`メソッド、コレクション初期化子内の値の型に一致します。</span><span class="sxs-lookup"><span data-stu-id="d70f0-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="d70f0-104">これは、`Add`メソッドを使用して、コレクション初期化子から値を持つコレクションを設定します。</span><span class="sxs-lookup"><span data-stu-id="d70f0-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="d70f0-105">一致する場合`Add`メソッドが存在して、コレクションのコードを変更することはできません、という拡張メソッドを追加する`Add`コレクション初期化子で必要とされるパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d70f0-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="d70f0-106">これは、通常ジェネリック コレクションに対するコレクション初期化子を使用する場合に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d70f0-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d70f0-107">例</span><span class="sxs-lookup"><span data-stu-id="d70f0-107">Example</span></span>  
 <span data-ttu-id="d70f0-108">次の例は、ジェネリック拡張メソッドを追加する方法を示します<xref:System.Collections.Generic.List%601>入力型のオブジェクトを追加する、コレクション初期化子を使用できるようにする`Employee`です。</span><span class="sxs-lookup"><span data-stu-id="d70f0-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="d70f0-109">拡張メソッドでは、簡略化されたコレクションの初期化子構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d70f0-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d70f0-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d70f0-110">See Also</span></span>  
 [<span data-ttu-id="d70f0-111">コレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="d70f0-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="d70f0-112">方法: コレクション初期化子を使用してコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="d70f0-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
