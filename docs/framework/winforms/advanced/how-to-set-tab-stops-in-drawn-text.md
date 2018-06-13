---
title: '方法 : 描画されたテキストにタブ ストップを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: e7f3fe9757db26bcc9dc9735f3d3d854edb7c099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523638"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>方法 : 描画されたテキストにタブ ストップを設定する
テキストのタブ ストップを設定するには呼び出すことによって、<xref:System.Drawing.StringFormat.SetTabStops%2A>のメソッド、<xref:System.Drawing.StringFormat>オブジェクトを渡す、<xref:System.Drawing.StringFormat>オブジェクトを<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>を使用して既存のタブを展開することができますが、描画するテキストへのタブ位置を追加するサポートされていませんが停止する機能は、<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>フラグ。  
  
## <a name="example"></a>例  
 次の例では、150、250、および 350 にタブ ストップを設定します。 次に、コードでは、名前と試験の点数のタブ付きの一覧が表示されます。  
  
 次の図は、タブ付きのテキストを示します。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 次のコードは 2 つの引数を渡す、<xref:System.Drawing.StringFormat.SetTabStops%2A>メソッドです。 2 番目の引数は、タブのオフセットを含む配列です。 渡される最初の引数<xref:System.Drawing.StringFormat.SetTabStops%2A>が 0 で、配列内の最初のオフセットが 0、外接する四角形の左端の位置から測定されることを示します。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [方法: GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
