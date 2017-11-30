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
ms.openlocfilehash: 31fb9adbda47514e5405d465c0b5e2493b966d8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-enumeration"></a>方法 : 列挙値にバインドする
この例では、列挙体の GetValues メソッドにバインドして列挙型にバインドする方法を示します。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Windows.Controls.ListBox>の一覧を表示<xref:System.Windows.HorizontalAlignment>データ バインディングを使用して列挙型値。 <xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.Button>を変更するようにバインドされて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>のプロパティの値、<xref:System.Windows.Controls.Button>で値を選択して、<xref:System.Windows.Controls.ListBox>です。  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>関連項目  
 [メソッドにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
