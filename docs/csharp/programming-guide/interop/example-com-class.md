---
title: "COM クラスの例 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad14b414c037d38da55ce0ec82685b790cc46d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="8ae6e-102">COM クラスの例 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8ae6e-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="8ae6e-103">ここでは、COM オブジェクトとして公開されるクラスの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="8ae6e-104">このコードを .cs ファイルに保存して、プロジェクトに追加したあと、**[COM の相互運用機能に登録]** プロパティを **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="8ae6e-105">詳細については、「[NIB: 方法: コンポーネントを COM 相互運用機能に登録する](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="8ae6e-106">Visual C# オブジェクトを COM に公開するには、クラス インターフェイス、イベント インターフェイス (必要な場合)、クラス自体を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="8ae6e-107">クラスのメンバーを COM で参照するには、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="8ae6e-108">クラスはパブリックであること。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="8ae6e-109">プロパティ、メソッド、およびイベントがパブリックであること。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="8ae6e-110">プロパティとメソッドがクラス インターフェイスで宣言されていること。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="8ae6e-111">イベントがイベント インターフェイスで宣言されていること。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="8ae6e-112">これらのインターフェイスで宣言されていない、クラス内の他のパブリック メンバーは、COM から参照されませんが、他の .NET Framework オブジェクトからは参照されます。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="8ae6e-113">プロパティとメソッドを COM に公開するには、それらをクラス インターフェイスで宣言し、`DispId` 属性でマークを付けて、クラスに実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="8ae6e-114">メンバーをインターフェイスで宣言する順序は、COM vtable で使用される順序になります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="8ae6e-115">クラスのイベントを公開するには、それらをイベント インターフェイスで宣言し、`DispId` 属性でマークを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="8ae6e-116">クラスでこのインターフェイスを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="8ae6e-117">クラスでは、クラス インターフェイスが実装されます。複数のインターフェイスを実装できますが、最初に実装されるのは、既定のクラス インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="8ae6e-118">ここで、COM に対して公開するプロパティとメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="8ae6e-119">プロパティとメソッドは、パブリックとしてマークされており、クラス インターフェイスの宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="8ae6e-120">また、ここでクラスから発生するイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="8ae6e-121">イベントは、パブリックとしてマークされており、イベント インターフェイスの宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae6e-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ae6e-122">例</span><span class="sxs-lookup"><span data-stu-id="8ae6e-122">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8ae6e-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ae6e-123">See Also</span></span>  
 [<span data-ttu-id="8ae6e-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8ae6e-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8ae6e-125">相互運用性</span><span class="sxs-lookup"><span data-stu-id="8ae6e-125">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)  
 <span data-ttu-id="8ae6e-126">[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)</span><span class="sxs-lookup"><span data-stu-id="8ae6e-126">[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)</span></span>
