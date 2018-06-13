---
title: .NET Framework を使用したカスタム Windows フォーム コントロールの開発
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], developing using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 236cebc0-bd71-4f18-9fd6-5d0e592375df
ms.openlocfilehash: 935358664f93b6428b9153a9bcbed862aeee07ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528669"
---
# <a name="developing-custom-windows-forms-controls-with-the-net-framework"></a><span data-ttu-id="a2dde-102">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="a2dde-102">Developing Custom Windows Forms Controls with the .NET Framework</span></span>
<span data-ttu-id="a2dde-103">Windows フォーム コントロールは、ユーザー インターフェイスの機能をカプセル化して、クライアント側の Windows ベースのアプリケーションで使用される再利用可能なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a2dde-103">Windows Forms controls are reusable components that encapsulate user interface functionality and are used in client-side Windows-based applications.</span></span> <span data-ttu-id="a2dde-104">Windows フォームは、すぐに使用できる多数のコントロールを提供するだけでなく、独自のコントロールを開発するためのインフラストラクチャも提供します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-104">Not only does Windows Forms provide many ready-to-use controls, it also provides the infrastructure for developing your own controls.</span></span> <span data-ttu-id="a2dde-105">既存のコントロールの結合、既存のコントロールの拡張、または独自のカスタム コントロールの記述ができます。</span><span class="sxs-lookup"><span data-stu-id="a2dde-105">You can combine existing controls, extend existing controls, or author your own custom controls.</span></span> <span data-ttu-id="a2dde-106">このセクションでは、Windows フォーム コントロールの開発に役立つ背景情報とサンプルを提供します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-106">This section provides background information and samples to help you develop Windows Forms controls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2dde-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a2dde-107">In This Section</span></span>  
 [<span data-ttu-id="a2dde-108">Windows フォームでのコントロールの使用方法の概要</span><span class="sxs-lookup"><span data-stu-id="a2dde-108">Overview of Using Controls in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/overview-of-using-controls-in-windows-forms.md)  
 <span data-ttu-id="a2dde-109">Windows フォーム アプリケーションでのコントロールの使用の重要な要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="a2dde-109">Highlights the essential elements of using controls in Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="a2dde-110">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="a2dde-110">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="a2dde-111"><xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間を使用して作成できる様々な種類のカスタム コントロールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-111">Describes the different kinds of custom controls you can author with the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="a2dde-112">Windows フォーム コントロール開発の基本概念</span><span class="sxs-lookup"><span data-stu-id="a2dde-112">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)  
 <span data-ttu-id="a2dde-113">Windows フォーム コントロールの開発の最初の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-113">Discusses the first steps in developing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="a2dde-114">Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="a2dde-114">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 <span data-ttu-id="a2dde-115">Windows フォーム コントロールのプロパティを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-115">Shows how to add to properties to Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a2dde-116">Windows フォーム コントロールのイベント</span><span class="sxs-lookup"><span data-stu-id="a2dde-116">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 <span data-ttu-id="a2dde-117">Windows フォーム コントロールのイベントを処理して定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-117">Shows how to handle and define events in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="a2dde-118">Windows フォーム コントロールの属性</span><span class="sxs-lookup"><span data-stu-id="a2dde-118">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="a2dde-119">カスタム コントロールとコンポーネントのプロパティや他のメンバーに適用できる属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-119">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="a2dde-120">コントロールのカスタム描画およびレンダリング</span><span class="sxs-lookup"><span data-stu-id="a2dde-120">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="a2dde-121">コントロールの外観をカスタマイズする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-121">Shows how to customize the appearance of your controls.</span></span>  
  
 [<span data-ttu-id="a2dde-122">Windows フォーム コントロールのレイアウト</span><span class="sxs-lookup"><span data-stu-id="a2dde-122">Layout in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/layout-in-windows-forms-controls.md)  
 <span data-ttu-id="a2dde-123">コントロールとフォームの高度なレイアウトを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-123">Shows how to create sophisticated layouts for your controls and forms.</span></span>  
  
 [<span data-ttu-id="a2dde-124">Windows フォーム コントロールのマルチスレッド処理</span><span class="sxs-lookup"><span data-stu-id="a2dde-124">Multithreading in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/multithreading-in-windows-forms-controls.md)  
 <span data-ttu-id="a2dde-125">マルチスレッド コントロールを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-125">Shows how to implement multithreaded controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a2dde-126">参照</span><span class="sxs-lookup"><span data-stu-id="a2dde-126">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="a2dde-127">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="a2dde-128">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-128">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2dde-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2dde-129">Related Sections</span></span>  
 [<span data-ttu-id="a2dde-130">コンポーネントのデザイン時属性</span><span class="sxs-lookup"><span data-stu-id="a2dde-130">Design-Time Attributes for Components</span></span>](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="a2dde-131">ビジュアル デザイナーでデザインするときに正しく表示されるようにコンポーネントとコントロールに適用するメタデータ属性の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-131">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="a2dde-132">デザイン時サポートの拡張</span><span class="sxs-lookup"><span data-stu-id="a2dde-132">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="a2dde-133">デザイン時サポートを提供するエディターやデザイナーなどのクラスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-133">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>  
  
 [<span data-ttu-id="a2dde-134">方法 : コンポーネントおよびコントロールのライセンス処理を行う</span><span class="sxs-lookup"><span data-stu-id="a2dde-134">How to: License Components and Controls</span></span>](http://msdn.microsoft.com/library/8e66c1ed-a445-4b26-8185-990b6e2bbd57)  
 <span data-ttu-id="a2dde-135">コントロールやコンポーネントのライセンスを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a2dde-135">Describes how to implement licensing in your control or component.</span></span>  
  
 <span data-ttu-id="a2dde-136">「[デザイン時の Windows フォーム コントロールの開発](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2dde-136">Also see [Developing Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/w29y3h59\(v=vs.110\)).</span></span>
