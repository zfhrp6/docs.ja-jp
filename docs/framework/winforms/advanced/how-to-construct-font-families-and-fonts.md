---
title: '方法 : フォント ファミリとフォントを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: ceace5950ec135ea4d52081da7d1de7a820583ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520891"
---
# <a name="how-to-construct-font-families-and-fonts"></a>方法 : フォント ファミリとフォントを作成する
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] スタイルは異なっても同じ書体を使用するフォントのフォント ファミリにグループ化します。 たとえば、Arial フォント ファミリには、次のフォントが含まれています。  
  
-   Arial 標準  
  
-   Arial 太字  
  
-   Arial 斜体  
  
-   Arial 太字斜体  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] フォームのファミリに 4 つのスタイルを使用します。 標準、太字、斜体、および太字斜体です。 などの形容詞*を絞り込む*と*丸め*スタイル; とは見なされません、ファミリ名の一部であるではなくです。 たとえば、次のメンバーのフォント ファミリはゴシックのように。  
  
-   Arial ナロー標準  
  
-   太字 arial ナロー  
  
-   Arial ナロー斜体  
  
-   Arial ナロー太字斜体  
  
 テキストを描画する前に[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]、構築する必要があります、<xref:System.Drawing.FontFamily>オブジェクトおよび<xref:System.Drawing.Font>オブジェクト。 <xref:System.Drawing.FontFamily>オブジェクト (たとえば、Arial) 書体を指定して、<xref:System.Drawing.Font>オブジェクトは、サイズ、スタイル、および単位を指定します。  
  
## <a name="example"></a>例  
 次の例では、標準のスタイル、サイズが 16 ピクセルの Arial フォントを構築します。 次のコードでは、最初の引数が渡される、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクターは、<xref:System.Drawing.FontFamily>オブジェクト。 2 番目の引数は、4 番目の引数によって識別される単位でフォントのサイズを指定します。 3 番目の引数は、スタイルを識別します。  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> メンバーである、<xref:System.Drawing.GraphicsUnit>列挙型、および<xref:System.Drawing.FontStyle.Regular>のメンバーである、<xref:System.Drawing.FontStyle>列挙します。  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> のパラメーターである `e`<xref:System.Windows.Forms.PaintEventHandler> を必要とします。  
  
## <a name="see-also"></a>関連項目  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
