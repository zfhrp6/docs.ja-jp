---
title: "方法 : バインディングの方向を指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdcda02a61f0114bfbbe5d5c411cb397cddcf683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>方法 : バインディングの方向を指定する
この例では、バインドの更新先 (バインディング ターゲット (ターゲット) のプロパティのみ、バインディング ソース (ソース) のプロパティのみ、またはターゲットのプロパティとソースのプロパティの両方) を指定する方法を示します。  
  
## <a name="example"></a>例  
 使用する、<xref:System.Windows.Data.Binding.Mode%2A>プロパティのバインドの方向を指定します。 次の列挙リストは、バインドの更新で使用できるオプションを示しています。  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay>対象となるプロパティまたは基になるプロパティのいずれかが変更されるたびに、対象となるプロパティまたはプロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode.OneWay>基になるプロパティが変更されたときにのみ、ターゲット プロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode.OneTime>アプリケーションの起動時にのみ、またはターゲット プロパティが更新、<xref:System.Windows.FrameworkElement.DataContext%2A>で変更が行われます。  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource>ターゲット プロパティが変更されたときに、基になるプロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode.Default>により、既定<xref:System.Windows.Data.Binding.Mode%2A>使用するターゲット プロパティの値。  
  
 詳細については、<xref:System.Windows.Data.BindingMode> 列挙型のページをご覧ください。  
  
 <xref:System.Windows.Data.Binding.Mode%2A> プロパティを設定する方法を次の例に示します。  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 ソースの変更を検出するために (に適用できる<xref:System.Windows.Data.BindingMode.OneWay>と<xref:System.Windows.Data.BindingMode.TwoWay>バインド)、ソースがなど、適切なプロパティの変更通知のメカニズムを実装する必要があります<xref:System.ComponentModel.INotifyPropertyChanged>です。 参照してください[実装プロパティの変更通知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)の例については、<xref:System.ComponentModel.INotifyPropertyChanged>実装します。  
  
 <xref:System.Windows.Data.BindingMode.TwoWay>または<xref:System.Windows.Data.BindingMode.OneWayToSource>バインドを設定して、ソースの更新のタイミングを制御することができます、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>プロパティです。 詳細については、「<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.Binding>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
