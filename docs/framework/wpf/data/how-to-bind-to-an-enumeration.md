---
title: "方法 : 列挙値にバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72439cdc1c1017378a5b6b3f6b4bf41a9eee2537
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-an-enumeration"></a>方法 : 列挙値にバインドする
この例では、列挙体の GetValues メソッドにバインドして列挙型にバインドする方法を示します。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Windows.Controls.ListBox>の一覧を表示<xref:System.Windows.HorizontalAlignment>データ バインディングを使用して列挙型値。 <xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.Button>を変更するようにバインドされて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>のプロパティの値、<xref:System.Windows.Controls.Button>で値を選択して、<xref:System.Windows.Controls.ListBox>です。  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>参照  
 [メソッドにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
