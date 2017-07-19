---
title: "方法 : PriorityBinding を実装する | Microsoft Docs"
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
  - "クラス, PriorityBinding"
  - "データ バインディング, PriorityBinding クラス"
  - "PriorityBinding クラス"
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : PriorityBinding を実装する
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] における <xref:System.Windows.Data.PriorityBinding> は、バインディング リストの指定により機能します。  バインディング リストは、優先順位の高いものから低いものに順番に並べられています。  優先順位の最も高いバインディングが処理された際に値を正常に返した場合は、リスト内の他のバインディングを処理する必要はありません。  優先順位の最も高いバインディングの評価に時間がかかる場合は、そのバインディングが値を正常に返すまで、正常に値を返した 2 番目に優先順位の高いバインディングが使用されることがあります。  
  
## 使用例  
 <xref:System.Windows.Data.PriorityBinding> の動作を示すため、`FastDP`、`SlowerDP`、および `SlowestDP` という 3 つのプロパティを持つ `AsyncDataSource` オブジェクトを作成しています。  
  
 `FastDP` の get アクセサーは、`_fastDP` データ メンバーの値を返します。  
  
 `SlowerDP` の get アクセサーは、3 秒待機してから `_slowerDP` データ メンバーの値を返します。  
  
 `SlowestDP` の get アクセサーは、5 秒待機してから `_slowestDP` データ メンバーの値を返します。  
  
> [!NOTE]
>  この例は、デモンストレーションのためだけに作成されています。  フィールド セットよりもはるかに時間がかかるため、[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] ガイドラインではプロパティを定義しないように推奨しています。  詳細については、「[NIB: Choosing Between Properties and Methods](http://msdn.microsoft.com/ja-jp/55825e8f-7e2e-448a-9505-7217cc91b1af)」を参照してください。  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A> プロパティは、<xref:System.Windows.Data.PriorityBinding> を次のように使用して、上の `AsyncDS` にバインドされます。  
  
 [!code-xml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 バインディング エンジンが <xref:System.Windows.Data.Binding> オブジェクトを処理する場合は、最初の <xref:System.Windows.Data.Binding> から処理を開始しますが、これは `SlowestDP` プロパティにバインドされています。  この <xref:System.Windows.Data.Binding> は 5 秒間スリープするため、処理された時点では正常に値を返しません。そのため、次の <xref:System.Windows.Data.Binding> 要素が処理されます。  次の <xref:System.Windows.Data.Binding> も 3 秒間スリープするため、正常に値を返しません。  そのため、バインディング エンジンは次の <xref:System.Windows.Data.Binding> 要素に移動します。この要素は `FastDP` プロパティにバインドされています。  この <xref:System.Windows.Data.Binding> は、値 "Fast Value" を返します。  <xref:System.Windows.Controls.TextBlock> には、値 "Fast Value" が表示されます。  
  
 3 秒経過すると、`SlowerDP` プロパティから値 "Slower Value" が返されます。  <xref:System.Windows.Controls.TextBlock> には、値 "Slower Value" が表示されます。  
  
 5 秒経過すると、`SlowestDP` プロパティから値 "Slowest Value" が返されます。  このバインディングは、リストの先頭に表示されているため、優先順位が最も高くなります。  <xref:System.Windows.Controls.TextBlock> には、値 "Slowest Value" が表示されます。  
  
 どのような値がバインディングからの正常な戻り値と見なされるかについては、<xref:System.Windows.Data.PriorityBinding> を参照してください。  
  
## 参照  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=fullName>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)