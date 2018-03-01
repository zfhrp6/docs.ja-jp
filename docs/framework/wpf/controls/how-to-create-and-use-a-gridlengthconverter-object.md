---
title: "方法 : GridLengthConverter オブジェクトを作成および使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 300916ec102682e1d886d43fbe70eeaf088d6454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>方法 : GridLengthConverter オブジェクトを作成および使用する
## <a name="example"></a>例  
 次の例は、作成しのインスタンスを使用する方法を示しています。<xref:System.Windows.GridLengthConverter>です。 例と呼ばれるカスタム メソッドを定義する`changeCol`、どのパス、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.GridLengthConverter>変換する、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Windows.GridLength>です。 変換後の値がの値として渡されたし、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>のプロパティ、<xref:System.Windows.Controls.ColumnDefinition>要素。  
  
 例と呼ばれる 2 番目のカスタム メソッドを定義も`changeColVal`します。 このカスタム メソッドは、変換、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>の<xref:System.Windows.Controls.Slider>を<xref:System.String>と値にバックアップし、パス、<xref:System.Windows.Controls.ColumnDefinition>として、<xref:System.Windows.Controls.ColumnDefinition.Width%2A>要素のです。  
  
 なお、個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルの内容を定義する、<xref:System.Windows.Controls.ListBoxItem>です。  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
