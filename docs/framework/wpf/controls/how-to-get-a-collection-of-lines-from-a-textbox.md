---
title: "方法 : TextBox から行のコレクションを取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb771cdb4d12ebaa5160ec16ca57ba6acf011222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>方法 : TextBox から行のコレクションを取得する
この例からのテキスト行のコレクションを取得する方法を示しています、<xref:System.Windows.Controls.TextBox>です。  
  
## <a name="example"></a>例  
 次の例を受け取る単純なメソッドを示しています、<xref:System.Windows.Controls.TextBox>引数、および返しますとして、<xref:System.Collections.Specialized.StringCollection>内のテキストの行を含む、 **TextBox**です。  <xref:System.Windows.Controls.TextBox.LineCount%2A>現在では行の数を決定するプロパティを使用、 **TextBox**、および<xref:System.Windows.Controls.TextBox.GetLineText%2A>各行を抽出し、行のコレクションに追加するメソッドを使用しています。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>関連項目  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
