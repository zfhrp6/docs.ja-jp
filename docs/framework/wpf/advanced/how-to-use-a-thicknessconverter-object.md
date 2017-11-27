---
title: "方法 : ThicknessConverter オブジェクトを使用する"
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
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce70dcd749f31d77061b4669d83d2e0b83726c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thicknessconverter-object"></a>方法 : ThicknessConverter オブジェクトを使用する
## <a name="example"></a>例  
 この例は、のインスタンスを作成する方法を示しています。<xref:System.Windows.ThicknessConverter>境界線の太さを変更するとします。  
  
 例と呼ばれるカスタム メソッドを定義する`changeThickness`; このメソッドは最初のコンテンツを変換、<xref:System.Windows.Controls.ListBoxItem>個別で定義されている、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルのインスタンスを<xref:System.Windows.Thickness>、後に、コンテンツに変換します、<xref:System.String>です。 このメソッドは、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.ThicknessConverter>に変換するオブジェクト、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Windows.Thickness>です。 この値がの値として渡されたし、<xref:System.Windows.Controls.Border.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>です。  
  
 この例は実行できません。  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [方法: Margin プロパティの変更](http://msdn.microsoft.com/en-us/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [方法: ListBoxItem を新しいデータ型に変換します。](http://msdn.microsoft.com/en-us/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
