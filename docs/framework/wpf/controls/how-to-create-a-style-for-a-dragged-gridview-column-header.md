---
title: "方法 : ドラッグされた GridView 列ヘッダーのスタイルを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 001d0ec45ad990ef366e7fc1216a7370aade9cb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>方法 : ドラッグされた GridView 列ヘッダーのスタイルを作成する
この例は、ドラッグしたの外観を変更する方法を示します<xref:System.Windows.Controls.GridViewColumnHeader>ユーザーが列の位置を変更するときにします。  
  
## <a name="example"></a>例  
 内の別の場所に列ヘッダーをドラッグすると、<xref:System.Windows.Controls.ListView>を使用して<xref:System.Windows.Controls.GridView>その表示モードの場合、列が新しい位置へ移動します。 列ヘッダーをドラッグすると、元のヘッダーだけでなく、ヘッダーの浮動小数点のコピーが表示されます。 列ヘッダーを<xref:System.Windows.Controls.GridView>で表される、<xref:System.Windows.Controls.GridViewColumnHeader>オブジェクト。  
  
 浮動小数点と元の両方のヘッダーの外観をカスタマイズするには設定<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>を変更する、 <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>です。 これら<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>場合に適用されます、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>プロパティの値が`true`と<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティの値が<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>です。  
  
 ユーザーがマウス ボタンを押すし、を押したことで、マウスが一時停止中に、 <xref:System.Windows.Controls.GridViewColumnHeader>、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>プロパティの値に変更`true`です。 同様に、ユーザーがドラッグ操作を開始するとき、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティに対する変更を<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>です。  
  
 次の例は、設定する方法を示します<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>を変更する、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.Background%2A>元および浮動小数点のヘッダー、ユーザーが列の新しい位置にドラッグしたときの色。  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)
