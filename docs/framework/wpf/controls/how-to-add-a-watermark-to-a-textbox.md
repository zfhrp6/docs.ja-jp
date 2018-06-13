---
title: '方法: TextBox にウォーターマークを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 962d6958de0811863393f930d8672769a50e8265
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550066"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>方法: TextBox にウォーターマークを追加する
次の例の使いやすさを支援する方法を示しています、<xref:System.Windows.Controls.TextBox>内の説明の背景イメージを表示することによって、<xref:System.Windows.Controls.TextBox>この時点で、イメージを削除するまで、ユーザーがテキストを入力します。 さらに、背景画像は、ユーザー入力を削除する場合、再度復元します。 次の図を参照してください。  
  
 ![背景画像を含む TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  背景画像は、この例ではなく、単に操作で使用する理由、<xref:System.Windows.Controls.TextBox.Text%2A>のプロパティ<xref:System.Windows.Controls.TextBox>がある、背景画像は、データ バインディングには影響しません。  
  
## <a name="example"></a>例  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>関連項目  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
