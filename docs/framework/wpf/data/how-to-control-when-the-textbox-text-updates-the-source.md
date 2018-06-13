---
title: '方法 : TextBox テキストでソースを更新するタイミングを制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 52f3a8d3a5d78a211367722b3042eb50f6ac36d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557226"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a>方法 : TextBox テキストでソースを更新するタイミングを制御する
このトピックを使用する方法について説明、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>バインディング ソースを更新するタイミングを制御するプロパティです。 トピックを使用して、<xref:System.Windows.Controls.TextBox>例と同様に制御します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> プロパティは、既定値を持つ<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値<xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>です。 つまり、アプリケーション、<xref:System.Windows.Controls.TextBox>データ バインドで<xref:System.Windows.Controls.TextBox>です。<xref:System.Windows.Controls.TextBox.Text%2A> プロパティに入力したテキスト、<xref:System.Windows.Controls.TextBox>までソースを更新できません、<xref:System.Windows.Controls.TextBox>がフォーカスを失った (から離れていてもクリックすると、インスタンスの<xref:System.Windows.Controls.TextBox>)。  
  
 入力と同時に更新するのには、ソースにする場合は、設定、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>へのバインドの<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>します。 次の例では、コードの強調表示された行を表示する、`Text`両方のプロパティ、<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.TextBlock>同じソース プロパティにバインドします。 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>に設定されているバインド<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>です。  
  
 [!code-xaml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]  
  
 その結果、<xref:System.Windows.Controls.TextBlock>にテキストを入力すると (変更) ために、同じテキストを示しています、<xref:System.Windows.Controls.TextBox>サンプルの次のスクリーン ショットに示すように、します。  
  
 ![単純なデータ バインディングのサンプルのスクリーンショット](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 ダイアログまたはユーザーが編集できるフォームがあると、ユーザーがフィールドの編集が完了し、[OK] をクリックするまで、ソースの更新を遅延させる場合は、設定することができる場合、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>に、バインディングの<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>次の例のように、します。  
  
 [!code-xaml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 設定すると、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値<xref:System.Windows.Data.UpdateSourceTrigger.Explicit>、元の値は、アプリケーションを呼び出すときにのみ変更、<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>メソッドです。 次の例を呼び出す方法を示します<xref:System.Windows.Data.BindingExpression.UpdateSource%2A>の`itemNameTextBox`:  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  その他のコントロールのプロパティの同じテクニックを使用できますが、その他のほとんどのプロパティに既定値を持つことに注意してください<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>値<xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>です。 詳細については、次を参照してください。、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ ページ。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティ ソースの更新を扱うためだけに関連しています<xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドします。 <xref:System.Windows.Data.BindingMode.TwoWay>と<xref:System.Windows.Data.BindingMode.OneWayToSource>するには、プロパティの変更通知を提供するソース オブジェクトの要件にバインドします。 詳しくは、このトピック内にあるサンプルをご覧ください。 また、「[方法 : プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」もご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
