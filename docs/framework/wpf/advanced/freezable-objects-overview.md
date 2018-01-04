---
title: "Freezable オブジェクトの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7390181570c6deeea77e5e76493a62e84107286b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="freezable-objects-overview"></a><span data-ttu-id="d335f-102">Freezable オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="d335f-102">Freezable Objects Overview</span></span>
<span data-ttu-id="d335f-103">このトピックを効果的に使用して作成する方法について説明<xref:System.Windows.Freezable>オブジェクトで、アプリケーションのパフォーマンスを改善する特別な機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d335f-103">This topic describes how to effectively use and create <xref:System.Windows.Freezable> objects, which provide special features that can help improve application performance.</span></span> <span data-ttu-id="d335f-104">Freezable オブジェクトの例には、ブラシ、ペン、変換、ジオメトリ、およびアニメーションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d335f-104">Examples of freezable objects include brushes, pens, transformations, geometries, and animations.</span></span>  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a><span data-ttu-id="d335f-105">Freezable は何ですか。</span><span class="sxs-lookup"><span data-stu-id="d335f-105">What Is a Freezable?</span></span>  
 <span data-ttu-id="d335f-106">A<xref:System.Windows.Freezable>を 2 つの状態を持つオブジェクトの特別な種類: 固定おらず、固定されています。</span><span class="sxs-lookup"><span data-stu-id="d335f-106">A <xref:System.Windows.Freezable> is a special type of object that has two states: unfrozen and frozen.</span></span> <span data-ttu-id="d335f-107">マスクされていない、ときに、<xref:System.Windows.Freezable>するその他のオブジェクトと同様に動作が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d335f-107">When unfrozen, a <xref:System.Windows.Freezable> appears to behave like any other object.</span></span> <span data-ttu-id="d335f-108">固定されると、<xref:System.Windows.Freezable>変更不要になったことができます。</span><span class="sxs-lookup"><span data-stu-id="d335f-108">When frozen, a <xref:System.Windows.Freezable> can no longer be modified.</span></span>  
  
 <span data-ttu-id="d335f-109">A<xref:System.Windows.Freezable>提供、<xref:System.Windows.Freezable.Changed>オブジェクトに変更を加えるのオブザーバーに通知するイベントです。</span><span class="sxs-lookup"><span data-stu-id="d335f-109">A <xref:System.Windows.Freezable> provides a <xref:System.Windows.Freezable.Changed> event to notify observers of any modifications to the object.</span></span> <span data-ttu-id="d335f-110">固定すること、<xref:System.Windows.Freezable>変更通知にリソースを費やす必要がなくなったため、パフォーマンスを向上することができます。</span><span class="sxs-lookup"><span data-stu-id="d335f-110">Freezing a <xref:System.Windows.Freezable> can improve its performance, because it no longer needs to spend resources on change notifications.</span></span> <span data-ttu-id="d335f-111">固定された<xref:System.Windows.Freezable>、固定されていないときに、スレッド間で共有することも<xref:System.Windows.Freezable>ことはできません。</span><span class="sxs-lookup"><span data-stu-id="d335f-111">A frozen <xref:System.Windows.Freezable> can also be shared across threads, while an unfrozen <xref:System.Windows.Freezable> cannot.</span></span>  
  
 <span data-ttu-id="d335f-112"><xref:System.Windows.Freezable>クラスには多くのアプリケーションで最も<xref:System.Windows.Freezable>オブジェクト[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グラフィックス サブシステムに関連します。</span><span class="sxs-lookup"><span data-stu-id="d335f-112">Although the <xref:System.Windows.Freezable> class has many applications, most <xref:System.Windows.Freezable> objects in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] are related to the graphics sub-system.</span></span>  
  
 <span data-ttu-id="d335f-113"><xref:System.Windows.Freezable>クラスは、特定のグラフィックス システム オブジェクトを使用するが容易し、アプリケーションのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="d335f-113">The <xref:System.Windows.Freezable> class makes it easier to use certain graphics system objects and can help improve application performance.</span></span> <span data-ttu-id="d335f-114">継承する型の例については<xref:System.Windows.Freezable>含める、 <xref:System.Windows.Media.Brush>、 <xref:System.Windows.Media.Transform>、および<xref:System.Windows.Media.Geometry>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d335f-114">Examples of types that inherit from <xref:System.Windows.Freezable> include the <xref:System.Windows.Media.Brush>, <xref:System.Windows.Media.Transform>, and <xref:System.Windows.Media.Geometry> classes.</span></span> <span data-ttu-id="d335f-115">アンマネージ リソースを含んでいるため、システムがこれらのオブジェクトの変更を監視を更新した後、元のオブジェクトへの変更がある場合に、対応するアンマネージ リソースを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d335f-115">Because they contain unmanaged resources, the system must monitor these objects for modifications, and then update their corresponding unmanaged resources when there is a change to the original object.</span></span> <span data-ttu-id="d335f-116">場合でも、実際には、グラフィックス システム オブジェクトを変更しない、システム使う必要がありますが、オブジェクトの監視にリソースの一部これを変更する場合にします。</span><span class="sxs-lookup"><span data-stu-id="d335f-116">Even if you don't actually modify a graphics system object, the system must still spend some of its resources monitoring the object, in case you do change it.</span></span>  
  
 <span data-ttu-id="d335f-117">たとえば、作成する、<xref:System.Windows.Media.SolidColorBrush>ブラシし、ボタンの背景の描画に使用します。</span><span class="sxs-lookup"><span data-stu-id="d335f-117">For example, suppose you create a <xref:System.Windows.Media.SolidColorBrush> brush and use it to paint the background of a button.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 <span data-ttu-id="d335f-118">ボタンが表示されると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]グラフィックス サブ システム ボタンの外観を作成するピクセルのグループを描画する提供情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="d335f-118">When the button is rendered, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] graphics sub-system uses the information you provided to paint a group of pixels to create the appearance of a button.</span></span> <span data-ttu-id="d335f-119">純色のブラシを使用して、ボタンを描画する方法について説明した、純色のブラシしない描画を行う実際には。</span><span class="sxs-lookup"><span data-stu-id="d335f-119">Although you used a solid color brush to describe how the button should be painted, your solid color brush doesn't actually do the painting.</span></span> <span data-ttu-id="d335f-120">グラフィックス システムが、ボタンとブラシに高速で低レベルのオブジェクトを生成し、実際に画面に表示されるこれらのオブジェクトはします。</span><span class="sxs-lookup"><span data-stu-id="d335f-120">The graphics system generates fast, low-level objects for the button and the brush, and it is those objects that actually appear on the screen.</span></span>  
  
 <span data-ttu-id="d335f-121">ブラシを変更する場合は、それらの低レベルのオブジェクトが再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d335f-121">If you were to modify the brush, those low-level objects would have to be regenerated.</span></span> <span data-ttu-id="d335f-122">Freezable クラスは、どのようなことができます、ブラシが変更されたときに更新して、対応する生成され、低レベルのオブジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="d335f-122">The freezable class is what gives a brush the ability to find its corresponding generated, low-level objects and to update them when it changes.</span></span> <span data-ttu-id="d335f-123">この機能を有効にすると、ブラシが「固定」すると言います。</span><span class="sxs-lookup"><span data-stu-id="d335f-123">When this ability is enabled, the brush is said to be "unfrozen."</span></span>  
  
 <span data-ttu-id="d335f-124">フリーズの<xref:System.Windows.Freezable.Freeze%2A>メソッドでは、この自動更新機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d335f-124">A freezable's <xref:System.Windows.Freezable.Freeze%2A> method enables you to disable this self-updating ability.</span></span> <span data-ttu-id="d335f-125">このメソッドを使用すると、「固定」、または不可能な状態になるブラシを作成します。</span><span class="sxs-lookup"><span data-stu-id="d335f-125">You can use this method to make the brush become "frozen," or unmodifiable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d335f-126">Freezable オブジェクトすべてを固定することができます。</span><span class="sxs-lookup"><span data-stu-id="d335f-126">Not every Freezable object can be frozen.</span></span> <span data-ttu-id="d335f-127">スローされないようにする、 <xref:System.InvalidOperationException>、Freezable オブジェクトの値をチェックして<xref:System.Windows.Freezable.CanFreeze%2A>固定にする前に固定できるかどうかを決定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d335f-127">To avoid throwing an <xref:System.InvalidOperationException>, check the value of the Freezable object's <xref:System.Windows.Freezable.CanFreeze%2A> property to determine whether it can be frozen before attempting to freeze it.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 <span data-ttu-id="d335f-128">不要になった、フリーズを修正する必要がある場合は、パフォーマンス上の利点を提供固定します。</span><span class="sxs-lookup"><span data-stu-id="d335f-128">When you no longer need to modify a freezable, freezing it provides performance benefits.</span></span> <span data-ttu-id="d335f-129">この例では、ブラシを固定する場合は、グラフィックス システムは変更を監視する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="d335f-129">If you were to freeze the brush in this example, the graphics system would no longer need to monitor it for changes.</span></span> <span data-ttu-id="d335f-130">グラフィックス システムは、その他の最適化をブラシが変更されないに認識していることもできます。</span><span class="sxs-lookup"><span data-stu-id="d335f-130">The graphics system can also make other optimizations, because it knows the brush won't change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d335f-131">便宜上、freezable オブジェクトは、明示的に固定する場合を除き、固定されていない残ります。</span><span class="sxs-lookup"><span data-stu-id="d335f-131">For convenience, freezable objects remain unfrozen unless you explicitly freeze them.</span></span>  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a><span data-ttu-id="d335f-132">Freezable の使用</span><span class="sxs-lookup"><span data-stu-id="d335f-132">Using Freezables</span></span>  
 <span data-ttu-id="d335f-133">使用、固定されていない freezable は、その他の種類のオブジェクトを使用するなどです。</span><span class="sxs-lookup"><span data-stu-id="d335f-133">Using an unfrozen freezable is like using any other type of object.</span></span> <span data-ttu-id="d335f-134">次の例では、色、<xref:System.Windows.Media.SolidColorBrush>が黄色から赤に後に変更ボタンの背景の描画に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d335f-134">In the following example, the color of a <xref:System.Windows.Media.SolidColorBrush> is changed from yellow to red after it's used to paint the background of a button.</span></span> <span data-ttu-id="d335f-135">グラフィックス システムでは、バック グラウンドで自動的に変更するボタン黄色から赤に画面の [次へ] の更新では動作します。</span><span class="sxs-lookup"><span data-stu-id="d335f-135">The graphics system works behind the scenes to automatically change the button from yellow to red the next time the screen is refreshed.</span></span>  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a><span data-ttu-id="d335f-136">Freezable はフリーズ</span><span class="sxs-lookup"><span data-stu-id="d335f-136">Freezing a Freezable</span></span>  
 <span data-ttu-id="d335f-137">させる、<xref:System.Windows.Freezable>呼び出して、変更不可能になってその<xref:System.Windows.Freezable.Freeze%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-137">To make a <xref:System.Windows.Freezable> unmodifiable, you call its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span> <span data-ttu-id="d335f-138">Freezable オブジェクトを格納しているオブジェクトを固定すると、それらのオブジェクトが固定されているとします。</span><span class="sxs-lookup"><span data-stu-id="d335f-138">When you freeze an object that contains freezable objects, those objects are frozen as well.</span></span> <span data-ttu-id="d335f-139">保持する場合など、<xref:System.Windows.Media.PathGeometry>図形やが含まれているセグメントは固定すぎます。</span><span class="sxs-lookup"><span data-stu-id="d335f-139">For example, if you freeze a <xref:System.Windows.Media.PathGeometry>, the figures and segments it contains would be frozen too.</span></span>  
  
 <span data-ttu-id="d335f-140">Freezable**できません**次のいずれかに当てはまる場合に固定します。</span><span class="sxs-lookup"><span data-stu-id="d335f-140">A Freezable **can't** be frozen if any of the following are true:</span></span>  
  
-   <span data-ttu-id="d335f-141">アニメーション化されたか、データ バインドされたプロパティ。</span><span class="sxs-lookup"><span data-stu-id="d335f-141">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="d335f-142">動的リソースによって設定されるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d335f-142">It has properties set by a dynamic resource.</span></span> <span data-ttu-id="d335f-143">(を参照してください、 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)動的なリソースの詳細についてはします)。</span><span class="sxs-lookup"><span data-stu-id="d335f-143">(See the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information about dynamic resources.)</span></span>  
  
-   <span data-ttu-id="d335f-144">含まれている<xref:System.Windows.Freezable>サブオブジェクトを固定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d335f-144">It contains <xref:System.Windows.Freezable> sub-objects that can't be frozen.</span></span>  
  
 <span data-ttu-id="d335f-145">これらの条件が false の場合、および変更にしないかどうか、 <xref:System.Windows.Freezable>、その前に説明したパフォーマンス メリットを得られることを固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d335f-145">If these conditions are false, and you don't intend to modify the <xref:System.Windows.Freezable>, then you should freeze it to gain the performance benefits described earlier.</span></span>  
  
 <span data-ttu-id="d335f-146">呼び出す、freezable の<xref:System.Windows.Freezable.Freeze%2A>メソッドを変更できません。</span><span class="sxs-lookup"><span data-stu-id="d335f-146">Once you call a freezable's <xref:System.Windows.Freezable.Freeze%2A> method, it can no longer be modified.</span></span> <span data-ttu-id="d335f-147">固定された変更しようとしています。 オブジェクトの原因として、<xref:System.InvalidOperationException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d335f-147">Attempting to modify a frozen object causes an <xref:System.InvalidOperationException> to be thrown.</span></span> <span data-ttu-id="d335f-148">次のコードでは、フリーズした後にブラシを変更するために、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d335f-148">The following code throws an exception, because we attempt to modify the brush after it's been frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 <span data-ttu-id="d335f-149">この例外がスローされることを避けるためには、使用することができます、<xref:System.Windows.Freezable.IsFrozen%2A>メソッドを呼び出せば確認するかどうか、<xref:System.Windows.Freezable>が固定されています。</span><span class="sxs-lookup"><span data-stu-id="d335f-149">To avoid throwing this exception, you can use the <xref:System.Windows.Freezable.IsFrozen%2A> method to determine whether a <xref:System.Windows.Freezable> is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="d335f-150">前のコード例では、変更可能なコピーが行われたの固定されたオブジェクトを使用して、<xref:System.Windows.Freezable.Clone%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-150">In the preceding code example, a modifiable copy was made of a frozen object using the <xref:System.Windows.Freezable.Clone%2A> method.</span></span> <span data-ttu-id="d335f-151">次のセクションでは、さらに詳しくクローン作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="d335f-151">The next section discusses cloning in more detail.</span></span>  
  
 <span data-ttu-id="d335f-152">**注**ため固定された freezable できませんアニメーション化、アニメーションは自動的に作成の変更可能な複製固定された<xref:System.Windows.Freezable>オブジェクトをアニメーション化をしようとすると、<xref:System.Windows.Media.Animation.Storyboard>です。</span><span class="sxs-lookup"><span data-stu-id="d335f-152">**Note** Because a frozen freezable cannot be animated, the animation system will automatically create modifiable clones of frozen <xref:System.Windows.Freezable> objects when you try to animate them with a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="d335f-153">によるパフォーマンスのオーバーヘッドが複製をなくすためには、アニメーション化する場合にマスクされていないオブジェクトのままにします。</span><span class="sxs-lookup"><span data-stu-id="d335f-153">To eliminate the performance overhead caused by cloning, leave an object unfrozen if you intend to animate it.</span></span> <span data-ttu-id="d335f-154">ストーリー ボードでのアニメーション化の詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="d335f-154">For more information about animating with storyboards, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
### <a name="freezing-from-markup"></a><span data-ttu-id="d335f-155">マークアップからのフリーズ</span><span class="sxs-lookup"><span data-stu-id="d335f-155">Freezing from Markup</span></span>  
 <span data-ttu-id="d335f-156">固定するのには、<xref:System.Windows.Freezable>オブジェクトを使用するマークアップで宣言された、`PresentationOptions:Freeze`属性。</span><span class="sxs-lookup"><span data-stu-id="d335f-156">To freeze a <xref:System.Windows.Freezable> object declared in markup, you use the `PresentationOptions:Freeze` attribute.</span></span> <span data-ttu-id="d335f-157">次の例で、<xref:System.Windows.Media.SolidColorBrush>はページ リソースとして宣言されており、固定されています。</span><span class="sxs-lookup"><span data-stu-id="d335f-157">In the following example, a <xref:System.Windows.Media.SolidColorBrush> is declared as a page resource and frozen.</span></span> <span data-ttu-id="d335f-158">ボタンの背景を設定するのには使用されます。</span><span class="sxs-lookup"><span data-stu-id="d335f-158">It is then used to set the background of a button.</span></span>  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 <span data-ttu-id="d335f-159">使用する、`Freeze`属性、プレゼンテーションのオプションの名前空間にマップする必要があります:`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`です。</span><span class="sxs-lookup"><span data-stu-id="d335f-159">To use the `Freeze` attribute, you must map to the presentation options namespace: `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`.</span></span> <span data-ttu-id="d335f-160">`PresentationOptions`この名前空間のマッピングの推奨されるプレフィックスを示します。</span><span class="sxs-lookup"><span data-stu-id="d335f-160">`PresentationOptions` is the recommended prefix for mapping this namespace:</span></span>  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 <span data-ttu-id="d335f-161">すべての XAML リーダーは、この属性を認識、ためにを使用することをお勧めしますが、 [mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)をマークする、`Presentation:Freeze`属性を無視できます。</span><span class="sxs-lookup"><span data-stu-id="d335f-161">Because not all XAML readers recognize this attribute, it's recommended that you use the [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) to mark the `Presentation:Freeze` attribute as ignorable:</span></span>  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 <span data-ttu-id="d335f-162">詳細については、次を参照してください。、 [mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)ページ。</span><span class="sxs-lookup"><span data-stu-id="d335f-162">For more information, see the [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) page.</span></span>  
  
### <a name="unfreezing-a-freezable"></a><span data-ttu-id="d335f-163">「固定解除」フリーズ</span><span class="sxs-lookup"><span data-stu-id="d335f-163">"Unfreezing" a Freezable</span></span>  
 <span data-ttu-id="d335f-164">1 回凍結されている場合、<xref:System.Windows.Freezable>決してを変更または固定です。 ただし、を使用して、固定されていない複製を作成することができます、<xref:System.Windows.Freezable.Clone%2A>または<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-164">Once frozen, a <xref:System.Windows.Freezable> can never be modified or unfrozen; however, you can create an unfrozen clone using the <xref:System.Windows.Freezable.Clone%2A> or <xref:System.Windows.Freezable.CloneCurrentValue%2A> method.</span></span>  
  
 <span data-ttu-id="d335f-165">次の例では、ブラシを使用してボタンの背景が設定され、そのブラシは、固定されています。</span><span class="sxs-lookup"><span data-stu-id="d335f-165">In the following example, the button's background is set with a brush and that brush is then frozen.</span></span> <span data-ttu-id="d335f-166">ブラシを使用して、固定されていないコピーされる、<xref:System.Windows.Freezable.Clone%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-166">An unfrozen copy is made of the brush using the <xref:System.Windows.Freezable.Clone%2A> method.</span></span> <span data-ttu-id="d335f-167">クローンが変更し、赤、黄色からボタンの背景を変更するために使用します。</span><span class="sxs-lookup"><span data-stu-id="d335f-167">The clone is modified and used to change the button's background from yellow to red.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  <span data-ttu-id="d335f-168">アニメーションを決してを新しいコピーを使用するどの複製方法に関係なく<xref:System.Windows.Freezable>です。</span><span class="sxs-lookup"><span data-stu-id="d335f-168">Regardless of which clone method you use, animations are never copied to the new <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="d335f-169"><xref:System.Windows.Freezable.Clone%2A>と<xref:System.Windows.Freezable.CloneCurrentValue%2A>メソッドが、freezable のディープ コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="d335f-169">The <xref:System.Windows.Freezable.Clone%2A> and <xref:System.Windows.Freezable.CloneCurrentValue%2A> methods produce deep copies of the freezable.</span></span> <span data-ttu-id="d335f-170">場合は、格納されているその他の固定 freezable オブジェクトも複製され変更可能です。</span><span class="sxs-lookup"><span data-stu-id="d335f-170">If the freezable contains other frozen freezable objects, they are also cloned and made modifiable.</span></span> <span data-ttu-id="d335f-171">たとえば、固定された複製する<xref:System.Windows.Media.PathGeometry>を変更可能なため、図とが含まれているセグメントもコピーされ変更可能です。</span><span class="sxs-lookup"><span data-stu-id="d335f-171">For example, if you clone a frozen <xref:System.Windows.Media.PathGeometry> to make it modifiable, the figures and segments it contains are also copied and made modifiable.</span></span>  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a><span data-ttu-id="d335f-172">Freezable クラスの作成</span><span class="sxs-lookup"><span data-stu-id="d335f-172">Creating Your Own Freezable Class</span></span>  
 <span data-ttu-id="d335f-173">派生したクラス<xref:System.Windows.Freezable>次の機能を取得します。</span><span class="sxs-lookup"><span data-stu-id="d335f-173">A class that derives from <xref:System.Windows.Freezable> gains the following features.</span></span>  
  
-   <span data-ttu-id="d335f-174">特殊な状態: 読み取り専用 (固定)、書き込み可能な状態です。</span><span class="sxs-lookup"><span data-stu-id="d335f-174">Special states: a read-only (frozen) and a writable state.</span></span>  
  
-   <span data-ttu-id="d335f-175">スレッド セーフ: 固定された<xref:System.Windows.Freezable>スレッド間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="d335f-175">Thread safety: a frozen <xref:System.Windows.Freezable> can be shared across threads.</span></span>  
  
-   <span data-ttu-id="d335f-176">変更通知の詳細: その他のとは異なり<xref:System.Windows.DependencyObject>s、Freezable オブジェクトでは、変更通知サブ プロパティの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d335f-176">Detailed change notification: Unlike other <xref:System.Windows.DependencyObject>s, Freezable objects provide change notifications when sub-property values change.</span></span>  
  
-   <span data-ttu-id="d335f-177">簡単な複製: Freezable のクラスが既にディープ クローンを生成するいくつかのメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="d335f-177">Easy cloning: the Freezable class has already implemented several methods that produce deep clones.</span></span>  
  
 <span data-ttu-id="d335f-178">A<xref:System.Windows.Freezable>の種類は、 <xref:System.Windows.DependencyObject>、ため、依存関係プロパティ システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="d335f-178">A <xref:System.Windows.Freezable> is a type of <xref:System.Windows.DependencyObject>, and therefore uses the dependency property system.</span></span> <span data-ttu-id="d335f-179">クラスのプロパティの依存関係プロパティを指定する必要はありませんが、依存関係プロパティを使用する必要のあるコードを記述するための量を削減は、<xref:System.Windows.Freezable>注意の依存関係プロパティをクラスが設計されています。</span><span class="sxs-lookup"><span data-stu-id="d335f-179">Your class properties don't have to be dependency properties, but using dependency properties will reduce the amount of code you have to write, because the <xref:System.Windows.Freezable> class was designed with dependency properties in mind.</span></span> <span data-ttu-id="d335f-180">依存関係プロパティ システムの詳細については、次を参照してください。、[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="d335f-180">For more information about the dependency property system, see the [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="d335f-181">各<xref:System.Windows.Freezable>サブクラスをオーバーライドする必要があります、<xref:System.Windows.Freezable.CreateInstanceCore%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-181">Every <xref:System.Windows.Freezable> subclass must override the <xref:System.Windows.Freezable.CreateInstanceCore%2A> method.</span></span> <span data-ttu-id="d335f-182">クラスは、そのすべてのデータの依存関係プロパティを使用している場合は、作業が終了します。</span><span class="sxs-lookup"><span data-stu-id="d335f-182">If your class uses dependency properties for all its data, you're finished.</span></span>  
  
 <span data-ttu-id="d335f-183">クラスに依存関係のないプロパティのデータ メンバーが含まれている場合も、次のメソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d335f-183">If your class contains non-dependency property data members, you must also override the following methods:</span></span>  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 <span data-ttu-id="d335f-184">次のルールにアクセスして、依存関係プロパティではないデータ メンバーへの書き込みを確認する必要がも。</span><span class="sxs-lookup"><span data-stu-id="d335f-184">You must also observe the following rules for accessing and writing to data members that are not dependency properties:</span></span>  
  
-   <span data-ttu-id="d335f-185">いずれかの先頭に[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]依存関係のないプロパティのデータ メンバーを読み取る、呼び出し、<xref:System.Windows.Freezable.ReadPreamble%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-185">At the beginning of any [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] that reads non-dependency property data members, call the <xref:System.Windows.Freezable.ReadPreamble%2A> method.</span></span>  
  
-   <span data-ttu-id="d335f-186">依存関係のないプロパティのデータ メンバーの書き込みをすべての API の先頭には、呼び出し、<xref:System.Windows.Freezable.WritePreamble%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-186">At the beginning of any API that writes non-dependency property data members, call the <xref:System.Windows.Freezable.WritePreamble%2A> method.</span></span> <span data-ttu-id="d335f-187">(呼び出した後<xref:System.Windows.Freezable.WritePreamble%2A>で、 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]、追加の呼び出しを行う必要はありません<xref:System.Windows.Freezable.ReadPreamble%2A>も依存関係のないプロパティのデータ メンバーを読み取るかどうかです)。</span><span class="sxs-lookup"><span data-stu-id="d335f-187">(Once you've called <xref:System.Windows.Freezable.WritePreamble%2A> in an [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], you don't need to make an additional call to <xref:System.Windows.Freezable.ReadPreamble%2A> if you also read non-dependency property data members.)</span></span>  
  
-   <span data-ttu-id="d335f-188">呼び出す、<xref:System.Windows.Freezable.WritePostscript%2A>依存関係のないプロパティのデータ メンバーへの書き込みメソッドを終了する前にメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d335f-188">Call the <xref:System.Windows.Freezable.WritePostscript%2A> method before exiting methods that write to non-dependency property data members.</span></span>  
  
 <span data-ttu-id="d335f-189">クラスにある非依存関係プロパティのデータ メンバーが含まれて かどうか<xref:System.Windows.DependencyObject>オブジェクトも呼び出す必要があります、<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A>メソッド メンバーを設定している場合でもでは、これらの値、変更のするたびに`null`です。</span><span class="sxs-lookup"><span data-stu-id="d335f-189">If your class contains non-dependency-property data members that are <xref:System.Windows.DependencyObject> objects, you must also call the <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> method each time you change on of their values, even if you're setting the member to `null`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d335f-190">各を開始することが非常に重要<xref:System.Windows.Freezable>呼び出し基本実装をオーバーライドするメソッド。</span><span class="sxs-lookup"><span data-stu-id="d335f-190">It's very important that you begin each <xref:System.Windows.Freezable> method you override with a call to the base implementation.</span></span>  
  
 <span data-ttu-id="d335f-191">カスタムの例については<xref:System.Windows.Freezable>クラスを参照してください、[カスタム アニメーション サンプル](http://go.microsoft.com/fwlink/?LinkID=159981)です。</span><span class="sxs-lookup"><span data-stu-id="d335f-191">For an example of a custom <xref:System.Windows.Freezable> class, see the [Custom Animation Sample](http://go.microsoft.com/fwlink/?LinkID=159981).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d335f-192">参照</span><span class="sxs-lookup"><span data-stu-id="d335f-192">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 [<span data-ttu-id="d335f-193">カスタム アニメーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="d335f-193">Custom Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159981)  
 [<span data-ttu-id="d335f-194">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="d335f-194">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="d335f-195">カスタム依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="d335f-195">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
