---
title: '方法: FontSizeConverter クラスを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545127"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>方法: FontSizeConverter クラスを使用する
## <a name="example"></a>例  
 この例は、のインスタンスを作成する方法を示しています。<xref:System.Windows.FontSizeConverter>使用してフォント サイズを変更します。  
  
 例と呼ばれるカスタム メソッドを定義する`changeSize`の内容を変換する、<xref:System.Windows.Controls.ListBoxItem>個別で定義されている、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルのインスタンスを<xref:System.Double>、以降に、<xref:System.String>です。 このメソッドは、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.FontSizeConverter>に変換するオブジェクト、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Double>です。 この値がの値として渡されたし、<xref:System.Windows.Controls.TextBlock.FontSize%2A>のプロパティ、<xref:System.Windows.Controls.TextBlock>要素。  
  
 この例と呼ばれる 2 番目のカスタム メソッドを定義も`changeFamily`します。 このメソッドは、変換、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>を<xref:System.String>、し、その値を渡します、<xref:System.Windows.Controls.TextBlock.FontFamily%2A>のプロパティ、<xref:System.Windows.Controls.TextBlock>要素。  
  
 この例は実行できません。  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FontSizeConverter>
