---
title: ダブル バッファリングされたグラフィックス
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: ea4b4b8616ed0b3eab2ddd6b2ec57a39909a0fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524067"
---
# <a name="double-buffered-graphics"></a>ダブル バッファリングされたグラフィックス
グラフィックスをプログラミングするときは、ちらつきが一般的な問題になります。 複数の複雑な描画操作を必要とするグラフィックス操作を実行すると、描画されたイメージがちらつきなどによって適切に表示されないことがあります。 このような問題に対処するために、.NET Framework では、ダブル バッファリングを利用できます。  
  
 ダブル バッファリングでは、メモリ バッファーを使用して、複数の描画操作に関連するちらつきの問題に対処します。 ダブル バッファリングを有効にすると、すべての描画操作が画面上の描画サーフェイスではなく、最初にメモリ バッファーに描画されます。 描画操作がすべて完了すると、メモリ バッファーが、関連付けられている描画サーフェイスに直接コピーされます。 画面上で実行されるグラフィックス操作は 1 つだけなので、複雑な描画操作に関連するイメージのちらつきが解消されます。  
  
## <a name="default-double-buffering"></a>既定のダブル バッファリング  
 アプリケーションでダブル バッファリングを使用するには、.NET Framework に用意されている、フォームやコントロールに対する既定のダブル バッファリングを使用するのが最も簡単です。 ダブル バッファリングを Windows フォームの既定値を有効にすることができ、設定が Windows コントロールを作成した、<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティを`true`またはを使用して、<xref:System.Windows.Forms.Control.SetStyle%2A>メソッドです。 詳細については、「[方法: フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)」を参照してください。  
  
## <a name="manually-managing-buffered-graphics"></a>バッファリングされたグラフィックスの手動管理  
 アニメーションや高度なメモリ管理など、より高度なダブル バッファリングのシナリオでは、.NET Framework クラスを使用して独自のダブル バッファリング ロジックを実装できます。 割り当てと個々 のグラフィックス バッファーを管理するクラスは、<xref:System.Drawing.BufferedGraphicsContext>クラスです。 すべてのアプリケーション ドメインが、独自の既定<xref:System.Drawing.BufferedGraphicsContext>ダブル バッファリングをそのアプリケーション用の既定のすべてを管理するインスタンス。 ほとんどの場合がある 1 つだけのアプリケーション ドメインごとのアプリケーションでは、1 つの既定値は、通常、<xref:System.Drawing.BufferedGraphicsContext>アプリケーションごとです。 既定の<xref:System.Drawing.BufferedGraphicsContext>によってインスタンスの管理、<xref:System.Drawing.BufferedGraphicsManager>クラスです。 既定値への参照を取得する<xref:System.Drawing.BufferedGraphicsContext>を呼び出してインスタンス、<xref:System.Drawing.BufferedGraphicsManager.Current%2A>です。 作成することも、専用<xref:System.Drawing.BufferedGraphicsContext>インスタンスで、画像を多用するアプリケーションのパフォーマンスを向上させることができます。 作成する方法については、<xref:System.Drawing.BufferedGraphicsContext>インスタンスは、「[する方法: バッファリングされたグラフィックス管理手動で](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)です。  
  
## <a name="manually-displaying-buffered-graphics"></a>バッファリングされたグラフィックスの手動表示  
 インスタンスを使用することができます、<xref:System.Drawing.BufferedGraphicsContext>を呼び出すことによってグラフィックス バッファーを作成するクラス、<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>のインスタンスが返されます、<xref:System.Drawing.BufferedGraphics>クラスです。 A<xref:System.Drawing.BufferedGraphics>オブジェクトは、フォームやコントロールなどの表示サーフェイスに関連付けられているメモリ バッファーを管理します。  
  
 インスタンス化された後、<xref:System.Drawing.BufferedGraphics>クラスは、メモリ内のグラフィックス バッファーへのレンダリングを管理します。 使用メモリ バッファーにグラフィックスをレンダリングすることができます、<xref:System.Drawing.BufferedGraphics.Graphics%2A>を公開、<xref:System.Drawing.Graphics>を直接メモリ バッファーを表すオブジェクト。 次のように描画できる<xref:System.Drawing.Graphics>オブジェクトと同じように、<xref:System.Drawing.Graphics>描画サーフェイスを表すオブジェクト。 バッファーへのすべてのグラフィックスを描画されて、したらを使用して、<xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType>を画面の描画サーフェイスへのバッファーの内容をコピーします。  
  
 使用する方法について、<xref:System.Drawing.BufferedGraphics>クラスを参照してください[バッファリングされたグラフィックス レンダリング手動で](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)です。 グラフィックスの描画の詳細については、「[Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [方法: バッファリングされたグラフィックスを手動で描画する](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [方法: フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [方法: バッファリングされたグラフィックスを手動で管理する](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Windows フォームにおけるグラフィックスと描画](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
