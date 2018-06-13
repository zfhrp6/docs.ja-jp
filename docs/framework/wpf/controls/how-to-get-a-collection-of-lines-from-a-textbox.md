---
title: '方法 : TextBox から行のコレクションを取得する'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 64187527da3cfb97343e2036338822d479dd997a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552741"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>方法 : TextBox から行のコレクションを取得する
この例からのテキスト行のコレクションを取得する方法を示しています、<xref:System.Windows.Controls.TextBox>です。  
  
## <a name="example"></a>例  
 次の例を受け取る単純なメソッドを示しています、<xref:System.Windows.Controls.TextBox>引数、および返しますとして、<xref:System.Collections.Specialized.StringCollection>内のテキストの行を含む、 **TextBox**です。  <xref:System.Windows.Controls.TextBox.LineCount%2A>現在では行の数を決定するプロパティを使用、 **TextBox**、および<xref:System.Windows.Controls.TextBox.GetLineText%2A>各行を抽出し、行のコレクションに追加するメソッドを使用しています。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>関連項目  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
