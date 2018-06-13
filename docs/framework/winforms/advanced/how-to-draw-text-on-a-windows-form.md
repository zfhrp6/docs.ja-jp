---
title: '方法 : Windows フォームにテキストを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: 9369a4ed26107bdc395d455ba6fb8420fd895d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524785"
---
# <a name="how-to-draw-text-on-a-windows-form"></a>方法 : Windows フォームにテキストを描画する
次のコード例を使用する方法を示しています、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>フォームにテキストを描画します。 また、使用することができます<xref:System.Windows.Forms.TextRenderer>フォームでテキストを描画するためです。 詳細については、次を参照してください。[する方法: GDI でテキストを描画](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)です。  
  
## <a name="example"></a>例  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 呼び出すことはできません、<xref:System.Drawing.Graphics.DrawString%2A>メソッドで、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。 フォームがサイズ変更されるか、別の形式によって隠されている場合、描画済みのコンテンツを再描画されませんされます。 コンテンツを自動的に再描画するために、オーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   Arial フォントがインストールされていません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [方法: GDI を使用してテキストを描画する](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
