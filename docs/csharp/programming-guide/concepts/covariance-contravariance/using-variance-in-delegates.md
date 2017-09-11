---
title: "デリゲートの分散の使用 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 9f2128080d34e78733cec926e59ee5dbe9b98a0d
ms.openlocfilehash: 83bef688a9d40c08f7a8280309ea5b607a9b06f0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/07/2017

---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="2182c-102">デリゲートの分散の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="2182c-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="2182c-103">メソッドをデリゲートに割り当てると、"*共変性*" と "*反変性*" により、デリゲート型をメソッドのシグネチャに柔軟に一致させることができます。</span><span class="sxs-lookup"><span data-stu-id="2182c-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="2182c-104">共変性により、メソッドの戻り値の型の派生を、デリゲートに定義されている型よりも強くできます。</span><span class="sxs-lookup"><span data-stu-id="2182c-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="2182c-105">また、反変性により、メソッドのパラメーター型の派生をデリゲート型よりも弱くできます。</span><span class="sxs-lookup"><span data-stu-id="2182c-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="2182c-106">例 1: 共変性</span><span class="sxs-lookup"><span data-stu-id="2182c-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="2182c-107">説明</span><span class="sxs-lookup"><span data-stu-id="2182c-107">Description</span></span>  
 <span data-ttu-id="2182c-108">この例は、デリゲート シグネチャ内の戻り値の型から派生した戻り値の型を持つメソッドで、デリゲートをどのように使用できるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="2182c-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="2182c-109">`DogsHandler` が返すデータ型は `Dogs` です。これは、デリゲートに定義された `Mammals` 型の派生型です。</span><span class="sxs-lookup"><span data-stu-id="2182c-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2182c-110">コード</span><span class="sxs-lookup"><span data-stu-id="2182c-110">Code</span></span>  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="2182c-111">例 2: 反変性</span><span class="sxs-lookup"><span data-stu-id="2182c-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="2182c-112">説明</span><span class="sxs-lookup"><span data-stu-id="2182c-112">Description</span></span>  
 <span data-ttu-id="2182c-113">この例は、パラメーターの型がデリゲート シグネチャ パラメーター型の基本データ型であるメソッドで、デリゲートをどのように使用できるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="2182c-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="2182c-114">反変性により、複数のハンドラーの代わりに単一のイベント ハンドラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2182c-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="2182c-115">たとえば、`EventArgs` 入力パラメーターを受け取るイベント ハンドラーを作成し、そのイベント ハンドラーを、`MouseEventArgs` 型をパラメーターとして送信する `Button.MouseClick` イベントや `KeyEventArgs` パラメーターを送信する `TextBox.KeyDown` イベントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2182c-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2182c-116">コード</span><span class="sxs-lookup"><span data-stu-id="2182c-116">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2182c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2182c-117">See Also</span></span>  
 <span data-ttu-id="2182c-118">[デリゲートの分散 (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="2182c-118">[Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span></span>  
 [<span data-ttu-id="2182c-119">Func および Action 汎用デリゲートでの分散の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="2182c-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

