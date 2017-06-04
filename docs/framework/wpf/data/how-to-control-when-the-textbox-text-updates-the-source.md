---
title: "方法 : TextBox テキストでソースを更新するタイミングを制御する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ バインディング, タイミング (ソースの更新の)"
  - "ソースの更新, タイミング"
  - "タイミング (ソースの更新の)"
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : TextBox テキストでソースを更新するタイミングを制御する
ここでは、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティを使用して、[バインディング ソース](GTMT)の更新のタイミングを制御する方法について説明します。  例として、ここでは <xref:System.Windows.Controls.TextBox> コントロールを使用します。  
  
## 使用例  
 <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> の既定値は <xref:System.Windows.Data.UpdateSourceTrigger> です。  つまり、アプリケーションに、データ バインドされていた <xref:System.Windows.Controls.TextBox>.<xref:System.Windows.Controls.TextBox.Text%2A> プロパティを持つ <xref:System.Windows.Controls.TextBox> がある場合、<xref:System.Windows.Controls.TextBox> に入力するテキストによってソースが更新されるのは、<xref:System.Windows.Controls.TextBox> にフォーカスがなくなったときです \(たとえば、<xref:System.Windows.Controls.TextBox> から離れた位置でクリックしたとき\)。  
  
 入力すると同時にソースを更新するには、バインディングの <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> を <xref:System.Windows.Data.UpdateSourceTrigger> に設定します。  次の例では、<xref:System.Windows.Controls.TextBox> および <xref:System.Windows.Controls.TextBlock> の両方の `Text` プロパティが同じソース プロパティにバインドされています。  <xref:System.Windows.Controls.TextBox> バインディングの <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティは、<xref:System.Windows.Data.UpdateSourceTrigger> に設定されています。  
  
 [!code-xml[SimpleBinding#USTHowTo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#usthowto)]  
  
 結果として、次のスクリーンショットの例に示すように、<xref:System.Windows.Controls.TextBlock> は、ユーザーが <xref:System.Windows.Controls.TextBox> に入力したのと同じテキストを表示します \(ソースが変更されるため\)。  
  
 ![単純なデータ バインディングのサンプルのスクリーンショット](../../../../docs/framework/wpf/data/media/databindingsimplebindingsample2.png "DataBindingSimpleBindingSample2")  
  
 ダイアログまたはユーザーが編集できるフォームがあり、ユーザーがフィールドの編集を終えて \[OK\] をクリックするまでソースの更新を遅延させる場合は、次の例のように、バインディングの <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値を <xref:System.Windows.Data.UpdateSourceTrigger> に設定します。  
  
 [!code-xml[UpdateSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値を <xref:System.Windows.Data.UpdateSourceTrigger> に設定すると、アプリケーションが <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> メソッドを呼び出す場合にのみソース値が変化します。  `itemNameTextBox` の <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> を呼び出す方法を次の例に示します。  
  
 [!code-csharp[UpdateSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]  
  
> [!NOTE]
>  同じ方法を他のコントロールのプロパティにも使用できますが、大多数の他のプロパティには <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> の既定値の <xref:System.Windows.Data.UpdateSourceTrigger> が設定されているので注意が必要です。  詳細については、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティのページを参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティはソースの更新を扱うため、<xref:System.Windows.Data.BindingMode> または <xref:System.Windows.Data.BindingMode> のバインディングにのみ関連します。  <xref:System.Windows.Data.BindingMode> バインディングと <xref:System.Windows.Data.BindingMode> バインディングが動作するには、ソース オブジェクトがプロパティ変更通知を提供する必要があります。  詳細については、このトピック内にあるサンプルを参照してください。  また、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」も参照してください。  
  
## 参照  
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)