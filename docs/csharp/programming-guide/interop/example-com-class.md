---
title: "COM クラスの例 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a759a7dcd211207c8740dd99d592daa509ddec47
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="ea95a-102">COM クラスの例 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ea95a-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="ea95a-103">ここでは、COM オブジェクトとして公開されるクラスの例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="ea95a-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="ea95a-104">このコードを .cs ファイルに保存して、プロジェクトに追加したあと、[**COM の相互運用機能に登録**] プロパティを [**True**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="ea95a-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="ea95a-105">詳細については、「[NIB: 方法: コンポーネントを COM 相互運用機能に登録する](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea95a-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="ea95a-106">Visual C# オブジェクトを COM に公開するには、クラス インターフェイス、イベント インターフェイス (必要な場合)、クラス自体を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="ea95a-107">クラスのメンバーを COM で参照するには、次の規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="ea95a-108">クラスはパブリックであること。</span><span class="sxs-lookup"><span data-stu-id="ea95a-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="ea95a-109">プロパティ、メソッド、およびイベントがパブリックであること。</span><span class="sxs-lookup"><span data-stu-id="ea95a-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="ea95a-110">プロパティとメソッドがクラス インターフェイスで宣言されていること。</span><span class="sxs-lookup"><span data-stu-id="ea95a-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="ea95a-111">イベントがイベント インターフェイスで宣言されていること。</span><span class="sxs-lookup"><span data-stu-id="ea95a-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="ea95a-112">これらのインターフェイスで宣言されていない、クラス内の他のパブリック メンバーは、COM から参照されませんが、他の .NET Framework オブジェクトからは参照されます。</span><span class="sxs-lookup"><span data-stu-id="ea95a-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="ea95a-113">プロパティとメソッドを COM に公開するには、それらをクラス インターフェイスで宣言し、`DispId` 属性でマークを付けて、クラスに実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="ea95a-114">メンバーをインターフェイスで宣言する順序は、COM vtable で使用される順序になります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="ea95a-115">クラスのイベントを公開するには、それらをイベント インターフェイスで宣言し、`DispId` 属性でマークを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="ea95a-116">クラスでこのインターフェイスを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea95a-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="ea95a-117">クラスでは、クラス インターフェイスが実装されます。複数のインターフェイスを実装できますが、最初に実装されるのは、既定のクラス インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ea95a-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="ea95a-118">ここで、COM に対して公開するプロパティとメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="ea95a-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="ea95a-119">プロパティとメソッドは、パブリックとしてマークされており、クラス インターフェイスの宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="ea95a-120">また、ここでクラスから発生するイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ea95a-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="ea95a-121">イベントは、パブリックとしてマークされており、イベント インターフェイスの宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea95a-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea95a-122">例</span><span class="sxs-lookup"><span data-stu-id="ea95a-122">Example</span></span>  
 <span data-ttu-id="ea95a-123">[!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea95a-123">[!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea95a-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea95a-124">See Also</span></span>  
 <span data-ttu-id="ea95a-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea95a-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ea95a-126">[相互運用性](../../../csharp/programming-guide/interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea95a-126">[Interoperability](../../../csharp/programming-guide/interop/index.md) </span></span>  
 <span data-ttu-id="ea95a-127">[[ビルド] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)</span><span class="sxs-lookup"><span data-stu-id="ea95a-127">[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)</span></span>

