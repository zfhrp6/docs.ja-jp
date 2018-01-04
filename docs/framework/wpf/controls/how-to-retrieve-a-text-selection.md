---
title: "方法 : テキスト選択を取得する"
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
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32be79811de4b8056449c2c6d6c53eca8cc063f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-text-selection"></a>方法 : テキスト選択を取得する
この例を使用する方法を示しています、<xref:System.Windows.Controls.TextBox.SelectedText%2A>で、ユーザーが選択したテキストを取得するプロパティを<xref:System.Windows.Controls.TextBox>コントロール。  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の定義の例、<xref:System.Windows.Controls.TextBox>を選択するにはいくつかのテキストを含むコントロールと<xref:System.Windows.Controls.Button>と指定したコントロール<xref:System.Windows.Controls.Button.OnClick%2A>メソッドです。  
  
 この例では、ボタンに関連付けられている<xref:System.Windows.Controls.Primitives.ButtonBase.Click>テキスト選択範囲を取得するイベント ハンドラーを使用します。 ユーザーは、ボタンをクリックしたときに、<xref:System.Windows.Controls.Button.OnClick%2A>メソッドは、文字列に、テキスト ボックスで、選択したテキストをコピーします。 特定の状況で選択されているテキストを取得 (ボタンをクリックすると、) も (テキストの選択を文字列にコピー)、選択範囲で実行されるアクションは、さまざまなシナリオに合わせて簡単に変更できます。  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>例  
 次[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]の例に示す、<xref:System.Windows.Controls.Button.OnClick%2A>で定義されているボタンのイベント ハンドラー、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]この例です。  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
