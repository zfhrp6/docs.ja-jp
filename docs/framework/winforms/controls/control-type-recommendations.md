---
title: "コントロールの種類に関するアドバイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a126d3b21ddd4bd31e168726c3538de21fb7d956
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="control-type-recommendations"></a><span data-ttu-id="e4b8f-102">コントロールの種類に関するアドバイス</span><span class="sxs-lookup"><span data-stu-id="e4b8f-102">Control Type Recommendations</span></span>
<span data-ttu-id="e4b8f-103">.NET Framework は、新しいコントロールを開発して実装する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-103">The .NET Framework gives you power to develop and implement new controls.</span></span> <span data-ttu-id="e4b8f-104">使い慣れたユーザー コントロールだけでなく、独自の描画を実行するカスタム コントロールを作成することも、継承によって既存のコントロールの機能を拡張することもできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-104">In addition to the familiar user control, you will now find that you are able to write custom controls that perform their own painting, and are even able to extend the functionality of existing controls through inheritance.</span></span> <span data-ttu-id="e4b8f-105">作成するコントロールの種類の決定が、混乱を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-105">Deciding which type of control to create can be confusing.</span></span> <span data-ttu-id="e4b8f-106">このセクションでは、継承できるさまざまな種類のコントロールの間の違いについて説明し、プロジェクトに合わせて選択する種類に関する注意点を示しています。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-106">This section highlights the differences between the various types of controls from which you can inherit, and gives considerations regarding the type to choose for your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4b8f-107">Web フォームで使用するコントロールを作成する場合は、「[カスタム ASP.NET サーバー コントロールの開発](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-107">If you want to author a control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="inheriting-from-a-windows-forms-control"></a><span data-ttu-id="e4b8f-108">Windows フォーム コントロールからの継承</span><span class="sxs-lookup"><span data-stu-id="e4b8f-108">Inheriting from a Windows Forms Control</span></span>  
 <span data-ttu-id="e4b8f-109">既存の Windows フォーム コントロールから継承されたコントロールを派生できます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-109">You can derive an inherited control from any existing Windows Forms control.</span></span> <span data-ttu-id="e4b8f-110">この方法では、すべての Windows フォーム コントロールの本質的な機能をすべて保持して、カスタム プロパティ、メソッド、またはその他の機能を追加することでその機能を拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-110">This approach allows you to retain all of the inherent functionality of a Windows Forms control, and to then extend that functionality by adding custom properties, methods, or other functionality.</span></span> <span data-ttu-id="e4b8f-111">たとえば、数値のみを受け付け、入力を自動的に値に変換できる <xref:System.Windows.Forms.TextBox> から派生したコントロールを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-111">For example, you might create a control derived from <xref:System.Windows.Forms.TextBox> that can accept only numbers and automatically converts input into a value.</span></span> <span data-ttu-id="e4b8f-112">このようなコントロールには、テキスト ボックスのテキストが変更されるたびに呼び出される検証コードが含まれ、値のプロパティを追加で持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-112">Such a control might contain validation code that was called whenever the text in the text box changed, and could have an additional property, Value.</span></span> <span data-ttu-id="e4b8f-113">一部のコントロールでは、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドをオーバーライドすることで、コントロールのグラフィカル インターフェイスにカスタムの外観を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-113">In some controls, you can also add a custom appearance to the graphical interface of your control by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>  
  
 <span data-ttu-id="e4b8f-114">次の場合に、Windows フォーム コントロールから継承します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-114">Inherit from a Windows Forms control if:</span></span>  
  
-   <span data-ttu-id="e4b8f-115">必要とする機能のほとんどが、既存の Windows フォーム コントロールと同じです。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-115">Most of the functionality you need is already identical to an existing Windows Forms control.</span></span>  
  
-   <span data-ttu-id="e4b8f-116">カスタムのグラフィカル インターフェイスが必要ないか、または既存のコントロールに対して新しいグラフィカルのフロント エンドをデザインします。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-116">You do not need a custom graphical interface, or you want to design a new graphical front end for an existing control.</span></span>  
  
## <a name="inheriting-from-the-usercontrol-class"></a><span data-ttu-id="e4b8f-117">UserControl クラスを継承する</span><span class="sxs-lookup"><span data-stu-id="e4b8f-117">Inheriting from the UserControl Class</span></span>  
 <span data-ttu-id="e4b8f-118">ユーザー コントロールは、共通のコンテナー内にカプセル化された Windows フォーム コントロールのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-118">A user control is a collection of Windows Forms controls encapsulated into a common container.</span></span> <span data-ttu-id="e4b8f-119">コンテナーは、各 Windows フォーム コントロールに関連付けられている固有の機能をすべて保持し、それらのプロパティを選択的に公開してバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-119">The container holds all of the inherent functionality associated with each of the Windows Forms controls and allows you to selectively expose and bind their properties.</span></span> <span data-ttu-id="e4b8f-120">ユーザー コントロールの例として、データベースから顧客の住所データを表示する貯めに作成されたコントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-120">An example of a user control might be a control built to display customer address data from a database.</span></span> <span data-ttu-id="e4b8f-121">このコントロールには、各フィールドを表示するいくつかのテキスト ボックスと、レコード間を移動するボタン コントロールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-121">This control would include several textboxes to display each field, and button controls to navigate through the records.</span></span> <span data-ttu-id="e4b8f-122">データ バインドのプロパティは選択的に公開することができ、コントロール全体は、パッケージしてアプリケーション間で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-122">Data-binding properties could be selectively exposed, and the entire control could be packaged and reused from application to application.</span></span>  
  
 <span data-ttu-id="e4b8f-123">次の場合に、<xref:System.Windows.Forms.UserControl> クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-123">Inherit from the <xref:System.Windows.Forms.UserControl> class if:</span></span>  
  
-   <span data-ttu-id="e4b8f-124">いくつかの Windows フォーム コントロールの機能を再利用可能な 1 つの単位に結合します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-124">You want to combine the functionality of several Windows Forms controls into a single reusable unit.</span></span>  
  
## <a name="inheriting-from-the-control-class"></a><span data-ttu-id="e4b8f-125">Control クラスからの継承</span><span class="sxs-lookup"><span data-stu-id="e4b8f-125">Inheriting from the Control Class</span></span>  
 <span data-ttu-id="e4b8f-126">コントロールを作成する別の方法は、<xref:System.Windows.Forms.Control> から継承することで、実質的に一から作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-126">Another way to create a control is to create one substantially from scratch by inheriting from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="e4b8f-127"><xref:System.Windows.Forms.Control> クラスは、コントロール (イベントなど) によって必要とされる基本的な機能をすべて提供しますが、コントロール固有の機能やグラフィカル インターフェイスは提供しません。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-127">The <xref:System.Windows.Forms.Control> class provides all of the basic functionality required by controls (for example, events), but no control-specific functionality or graphical interface.</span></span> <span data-ttu-id="e4b8f-128"><xref:System.Windows.Forms.Control> クラスから継承することでコントロールを作成する場合は、ユーザー コントロールや既存の Windows フォーム コントロールから継承する場合よりも、はるかに多くの配慮と労力が必要です。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-128">Creating a control by inheriting from the <xref:System.Windows.Forms.Control> class requires a lot more thought and effort than inheriting from user control or an existing Windows Forms control.</span></span> <span data-ttu-id="e4b8f-129">作成者は、コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> イベントのコード、および必要とされる機能固有のコードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-129">The author must write code for the <xref:System.Windows.Forms.Control.OnPaint%2A> event of the control, as well as any functionality specific code that is needed.</span></span> <span data-ttu-id="e4b8f-130">ただし、より大きな柔軟性が可能になり、正確なニーズに合わせてコントロールをカスタムに調整することができます。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-130">Greater flexibility is allowed, however, and you can custom tailor a control to suit your exact needs.</span></span> <span data-ttu-id="e4b8f-131">カスタム コントロールの例は、アナログ時計の外観や動作を複製する時計コントロールです。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-131">An example of a custom control is a clock control that duplicates the look and action of an analog clock.</span></span> <span data-ttu-id="e4b8f-132">内部タイマー コンポーネントからの <xref:System.Windows.Forms.Timer.Tick> イベントに応答してカスタム描画が呼び出されて、時計の針が移動します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-132">Custom painting would be invoked to cause the hands of the clock to move in response to <xref:System.Windows.Forms.Timer.Tick> events from an internal timer component.</span></span>  
  
 <span data-ttu-id="e4b8f-133">次の場合に、<xref:System.Windows.Forms.Control> クラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-133">Inherit from the <xref:System.Windows.Forms.Control> class if:</span></span>  
  
-   <span data-ttu-id="e4b8f-134">コントロールのカスタムのグラフィカル表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-134">You want to provide a custom graphical representation of your control.</span></span>  
  
-   <span data-ttu-id="e4b8f-135">標準コントロールでは使用できないカスタムの機能を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4b8f-135">You need to implement custom functionality that is not available through standard controls.</span></span>  
  
-   <span data-ttu-id="e4b8f-136">[方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-137">[チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-137">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-138">[チュートリアル : Visual C# による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-138">[Walkthrough: Inheriting from a Windows Forms Control with Visual C#](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-139">[方法 : コントロールにツールボックス ビットマップを指定する](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-139">[How to: Provide a Toolbox Bitmap for a Control](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-140">[方法: 既存の Windows フォーム コントロールから継承する](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-140">[How to: Inherit from Existing Windows Forms Controls](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-141">[チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-141">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-142">[方法: コントロール クラスを継承する](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-142">[How to: Inherit from the Control Class](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-143">[方法: UserControl の実行時の動作をテストする](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-143">[How to: Test the Run-Time Behavior of a UserControl](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-144">[方法: デザイン時にフォームの端に合わせてコントロールを配置する](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-144">[How to: Align a Control to the Edges of Forms at Design Time](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-145">[方法: UserControl クラスを継承する](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-145">[How to: Inherit from the UserControl Class](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-146">[方法: Windows フォームのコントロールを作成する](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-146">[How to: Author Controls for Windows Forms](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-147">[方法: 複合コントロールを作成する](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-147">[How to: Author Composite Controls](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-148">[チュートリアル : Visual Basic による複合コントロールの作成](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-148">[Walkthrough: Authoring a Composite Control with Visual Basic](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-149">[チュートリアル: Visual C# による複合コントロールの作成](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-149">[Walkthrough: Authoring a Composite Control with Visual C#](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-150">[チュートリアル : Visual Basic による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-150">[Walkthrough: Inheriting from a Windows Forms Control with Visual Basic](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-151">[方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-151">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="e4b8f-152">[方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span><span class="sxs-lookup"><span data-stu-id="e4b8f-152">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b8f-153">参照</span><span class="sxs-lookup"><span data-stu-id="e4b8f-153">See Also</span></span>  
 [<span data-ttu-id="e4b8f-154">方法: シンプルな Windows フォーム コントロールを開発する</span><span class="sxs-lookup"><span data-stu-id="e4b8f-154">How to: Develop a Simple Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [<span data-ttu-id="e4b8f-155">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="e4b8f-155">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
