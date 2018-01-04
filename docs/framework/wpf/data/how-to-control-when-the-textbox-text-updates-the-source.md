---
title: "方法 : TextBox テキストでソースを更新するタイミングを制御する"
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
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c503eb3300aba4a44c5a013c62942e7a171ae96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="8e764-102">方法 : TextBox テキストでソースを更新するタイミングを制御する</span><span class="sxs-lookup"><span data-stu-id="8e764-102">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="8e764-103">このトピックを使用する方法について説明、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>バインディング ソースを更新するタイミングを制御するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8e764-103">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="8e764-104">トピックを使用して、<xref:System.Windows.Controls.TextBox>例と同様に制御します。</span><span class="sxs-lookup"><span data-stu-id="8e764-104">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e764-105">例</span><span class="sxs-lookup"><span data-stu-id="8e764-105">Example</span></span>  
 <span data-ttu-id="8e764-106"><xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A>プロパティは、既定値を持つ<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>の値<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>です。</span><span class="sxs-lookup"><span data-stu-id="8e764-106">The <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="8e764-107">つまり、アプリケーション、<xref:System.Windows.Controls.TextBox>データ バインドで<xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A>プロパティに入力したテキスト、<xref:System.Windows.Controls.TextBox>までソースを更新できません、<xref:System.Windows.Controls.TextBox>がフォーカスを失った (たとえばをクリックすると、から離れた場所<xref:System.Windows.Controls.TextBox>).</span><span class="sxs-lookup"><span data-stu-id="8e764-107">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>  
  
 <span data-ttu-id="8e764-108">入力する場合は、ソースとして更新されるを設定、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>へのバインドの<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>します。</span><span class="sxs-lookup"><span data-stu-id="8e764-108">If you want the source to get updated as you are typing, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="8e764-109">次の例で、`Text`両方のプロパティ、<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.TextBlock>同じソース プロパティにバインドします。</span><span class="sxs-lookup"><span data-stu-id="8e764-109">In the following example, the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="8e764-110"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>に設定されているバインド<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>です。</span><span class="sxs-lookup"><span data-stu-id="8e764-110">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 <span data-ttu-id="8e764-111">その結果、<xref:System.Windows.Controls.TextBlock>にテキストを入力すると (変更) ために、同じテキストを示しています、<xref:System.Windows.Controls.TextBox>サンプルの次のスクリーン ショットに示すように、します。</span><span class="sxs-lookup"><span data-stu-id="8e764-111">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>  
  
 <span data-ttu-id="8e764-112">![単純なデータ バインディングのサンプルのスクリーンショット](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span><span class="sxs-lookup"><span data-stu-id="8e764-112">![Simple data binding sample screen shot](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")</span></span>  
  
 <span data-ttu-id="8e764-113">ダイアログまたはユーザーが編集できるフォームがあると、ユーザーがフィールドの編集が完了し、[OK] をクリックするまで、ソースの更新を遅延させる場合は、設定することができる場合、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>に、バインディングの<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>次の例のように、します。</span><span class="sxs-lookup"><span data-stu-id="8e764-113">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="8e764-114">設定すると、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>、元の値は、アプリケーションを呼び出すときにのみ変更、<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8e764-114">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="8e764-115">次の例を呼び出す方法を示します<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>の`itemNameTextBox`:</span><span class="sxs-lookup"><span data-stu-id="8e764-115">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="8e764-116">その他のコントロールのプロパティの同じテクニックを使用できますが、その他のほとんどのプロパティに既定値を持つことに注意してください<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>です。</span><span class="sxs-lookup"><span data-stu-id="8e764-116">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="8e764-117">詳細については、次を参照してください。、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ ページ。</span><span class="sxs-lookup"><span data-stu-id="8e764-117">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e764-118"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ ソースの更新を扱うためだけに関連しています<xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドします。</span><span class="sxs-lookup"><span data-stu-id="8e764-118">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="8e764-119"><xref:System.Windows.Data.BindingMode.TwoWay>と<xref:System.Windows.Data.BindingMode.OneWayToSource>するには、プロパティの変更通知を提供するソース オブジェクトの要件にバインドします。</span><span class="sxs-lookup"><span data-stu-id="8e764-119">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="8e764-120">詳しくは、このトピック内にあるサンプルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8e764-120">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="8e764-121">また、「[方法 : プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」もご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8e764-121">In addition, you can look at [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e764-122">参照</span><span class="sxs-lookup"><span data-stu-id="8e764-122">See Also</span></span>  
 [<span data-ttu-id="8e764-123">データ バインドに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="8e764-123">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
