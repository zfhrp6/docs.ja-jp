---
title: "方法 : 複数行の TextBox コントロールを作成する"
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
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a6885a594e5fcd747f85dedf1afbd39ec644717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a>方法 : 複数行の TextBox コントロールを作成する
この例を使用する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を定義する、<xref:System.Windows.Controls.TextBox>複数行のテキストに合わせて自動的に拡張するコントロール。  
  
## <a name="example"></a>例  
 設定、<xref:System.Windows.Controls.TextBox.TextWrapping%2A>属性を**ラップ**入力したテキストを新しいをラップすると、行の端、<xref:System.Windows.Controls.TextBox>コントロールに達すると、自動的に拡大、<xref:System.Windows.Controls.TextBox>の場合、新しい行の領域を確保するコントロールいる。  
  
 設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>属性を**true** RETURN キーを押すと、自動的にもう一度拡張に挿入される新しい行をにより、<xref:System.Windows.Controls.TextBox>に必要な場合、新しい行のスペースを含めます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>属性によって、スクロール バーを表示、追加、<xref:System.Windows.Controls.TextBox>いるための内容、<xref:System.Windows.Controls.TextBox>できますスクロールできる場合は、<xref:System.Windows.Controls.TextBox>フレームまたはそれを囲むウィンドウのサイズよりも大ききます。  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.TextWrapping>  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
