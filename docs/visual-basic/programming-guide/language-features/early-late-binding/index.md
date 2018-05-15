---
title: 事前バインディングと遅延バインディング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: 8426899b0c0d3649f47cbd6ad5383dd3c95b9499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="93b45-102">事前バインディングと遅延バインディング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93b45-102">Early and Late Binding (Visual Basic)</span></span>
<span data-ttu-id="93b45-103">Visual Basic コンパイラの実行と呼ばれるプロセス`binding`オブジェクトが、オブジェクト変数に割り当てられている場合。</span><span class="sxs-lookup"><span data-stu-id="93b45-103">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="93b45-104">オブジェクトが特定のオブジェクト型として宣言された変数に代入される場合、オブジェクトは*事前バインディング*されます。</span><span class="sxs-lookup"><span data-stu-id="93b45-104">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="93b45-105">事前バインディングされたオブジェクトを使用すると、コンパイラは、アプリケーションを実行する前に、メモリの割り当てとその他の最適化を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="93b45-105">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="93b45-106">たとえば、次のコードは、<xref:System.IO.FileStream> 型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="93b45-106">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 <span data-ttu-id="93b45-107"><xref:System.IO.FileStream> は特定のオブジェクト型であるため、`FS` に代入されるインスタンスは事前バインディングされます。</span><span class="sxs-lookup"><span data-stu-id="93b45-107">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="93b45-108">対照的に、オブジェクトが `Object` 型として宣言された変数に代入される場合、オブジェクトは*遅延バインディング*されます。</span><span class="sxs-lookup"><span data-stu-id="93b45-108">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="93b45-109">この型のオブジェクトは、任意のオブジェクトへの参照を保持できますが、事前バインディングされたオブジェクトが持っている多くの利点を欠いています。</span><span class="sxs-lookup"><span data-stu-id="93b45-109">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="93b45-110">たとえば、次のコードは、`CreateObject` 関数によって返されたオブジェクトを保持するオブジェクト変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="93b45-110">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="93b45-111">事前バインディングの利点</span><span class="sxs-lookup"><span data-stu-id="93b45-111">Advantages of Early Binding</span></span>  
 <span data-ttu-id="93b45-112">コンパイラが効率の高いアプリケーションを生成するための重要な最適化を行うことができるため、可能であれば、事前バインディングされたオブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93b45-112">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="93b45-113">事前バインディングされたオブジェクトは遅延バインディング オブジェクトよりもはるかに高速であり、使用されるオブジェクトの種類を正確に記述することでコードを読みやすくして管理を容易にします。</span><span class="sxs-lookup"><span data-stu-id="93b45-113">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="93b45-114">事前バインディングをもう 1 つの利点は、Visual Studio 統合開発環境 (IDE) に正確にどのようなオブジェクトの型を扱うを編集すると判断できるので自動コード補完機能とダイナミック ヘルプなどの便利な機能を使用できること、コードです。</span><span class="sxs-lookup"><span data-stu-id="93b45-114">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="93b45-115">事前バインディングを使用すると、コンパイラがプログラムのコンパイル時にエラーを報告できるため、ランタイム エラーの数が減少し、重大度が低下します。</span><span class="sxs-lookup"><span data-stu-id="93b45-115">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93b45-116">遅延バインディングは、`Public` として宣言されている型メンバーにアクセスするためにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="93b45-116">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="93b45-117">`Friend` または `Protected Friend` として宣言されているメンバーにアクセスすると、ランタイム エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="93b45-117">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b45-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="93b45-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>  
 [<span data-ttu-id="93b45-119">オブジェクトの有効期間 : オブジェクトの作成と破棄</span><span class="sxs-lookup"><span data-stu-id="93b45-119">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [<span data-ttu-id="93b45-120">Object 型</span><span class="sxs-lookup"><span data-stu-id="93b45-120">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
