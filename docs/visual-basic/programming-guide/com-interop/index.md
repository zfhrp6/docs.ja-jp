---
title: "COM 相互運用 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a64eaba75128a3844847fbf803c86c2d700db72
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="4c151-102">COM 相互運用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c151-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="4c151-103">コンポーネント オブジェクト モデル (COM) では、オブジェクトがその機能を他のコンポーネントに公開し、アプリケーションをホストすることを許可します。</span><span class="sxs-lookup"><span data-stu-id="4c151-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="4c151-104">今日のソフトウェアのほとんどに、COM オブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c151-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="4c151-105">.NET アセンブリは新しいアプリケーションに最適ですが、時には COM オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c151-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="4c151-106">このセクションには、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] での COM オブジェクトの作成と使用に関連するいくつかの問題も含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c151-106">This section covers some of the issues associated with creating and using COM objects with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c151-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c151-107">In This Section</span></span>  
 [<span data-ttu-id="4c151-108">COM 相互運用の概要</span><span class="sxs-lookup"><span data-stu-id="4c151-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="4c151-109">COM 相互運用の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="4c151-110">方法: Visual Basic から COM オブジェクトを参照する</span><span class="sxs-lookup"><span data-stu-id="4c151-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="4c151-111">タイプ ライブラリがある COM オブジェクトへの参照を追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="4c151-112">方法 : ActiveX コントロールを操作する</span><span class="sxs-lookup"><span data-stu-id="4c151-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="4c151-113">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ツールボックスに機能を追加するために、既存の ActiveX コントロールを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-113">Demonstrates how to use existing ActiveX controls to add features to the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Toolbox.</span></span>  
  
 [<span data-ttu-id="4c151-114">チュートリアル : Windows API の呼び出し</span><span class="sxs-lookup"><span data-stu-id="4c151-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="4c151-115">Windows オペレーティング システムの一部である API を呼び出すプロセスの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="4c151-116">方法: Windows API を呼び出す</span><span class="sxs-lookup"><span data-stu-id="4c151-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="4c151-117">User32.dll で `MessageBox` 関数を定義して呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="4c151-118">方法 : 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="4c151-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="4c151-119">符号なしの型のパラメーターを持つ Windows 関数を呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="4c151-120">チュートリアル: Visual Basic での COM オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="4c151-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="4c151-121">COM クラス テンプレートを使用した場合と使用しない場合の COM オブジェクトを作成するプロセスの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="4c151-122">相互運用性のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4c151-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="4c151-123">COM を使用するときに発生する問題の一部について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="4c151-124">.NET Framework アプリケーションにおける COM 相互運用性</span><span class="sxs-lookup"><span data-stu-id="4c151-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="4c151-125">同じアプリケーションで COM オブジェクトと .NET Framework オブジェクトを使用する方法の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="4c151-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="4c151-126">チュートリアル : COM オブジェクトによる継承の実装</span><span class="sxs-lookup"><span data-stu-id="4c151-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="4c151-127">新しいオブジェクトの基本として既存の COM オブジェクトを使用する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4c151-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c151-128">Related Sections</span></span>  
 [<span data-ttu-id="4c151-129">アンマネージ コードとの相互運用</span><span class="sxs-lookup"><span data-stu-id="4c151-129">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 <span data-ttu-id="4c151-130">共通言語ランタイムが提供する相互運用サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="4c151-131">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="4c151-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="4c151-132">COM 相互運用を使って COM タイプを呼び出すプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="4c151-133">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="4c151-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="4c151-134">COM からのマネージ型の準備と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="4c151-135">相互運用固有の属性の適用</span><span class="sxs-lookup"><span data-stu-id="4c151-135">Applying Interop Attributes</span></span>](../../../../docs/framework/interop/applying-interop-attributes.md)  
 <span data-ttu-id="4c151-136">アンマネージ コードを操作するときに使用できる属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c151-136">Covers attributes you can use when working with unmanaged code.</span></span>
