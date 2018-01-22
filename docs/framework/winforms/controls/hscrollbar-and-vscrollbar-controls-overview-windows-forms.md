---
title: "HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fbdb3778959d1691200cde49e485d8a63c6e645
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ScrollBar>または垂直方向に水平方向にスクロールすることにより、アプリケーションまたはコントロール内で簡単にナビゲート長い一覧の項目または大量の情報を提供するコントロールを使用します。 スクロール バーは、Windows のインターフェイスの一般的な要素をそのため、<xref:System.Windows.Forms.ScrollBar>コントロールから派生していないを持つコントロールが使用される多くの場合、<xref:System.Windows.Forms.ScrollableControl>クラスです。 組み込むに多くの開発者が同様に、選択、<xref:System.Windows.Forms.ScrollBar>独自のユーザー コントロールを作成するときに制御します。  
  
 <xref:System.Windows.Forms.HScrollBar> (水平) と<xref:System.Windows.Forms.VScrollBar>(縦方向) の制御は、他のコントロールから独立して動作して、独自のイベント、プロパティ、およびメソッドのセット。 <xref:System.Windows.Forms.ScrollBar>コントロールは、テキスト ボックス、リスト ボックス、コンボ ボックス、または MDI フォームにアタッチされている組み込みのスクロール バーと同じではありません (、<xref:System.Windows.Forms.TextBox>コントロールが、<xref:System.Windows.Forms.TextBox.ScrollBars%2A>プロパティ、コントロールに関連付けられているスクロール バーを非表示)。  
  
 <xref:System.Windows.Forms.ScrollBar>使用を制御、<xref:System.Windows.Forms.ScrollBar.Scroll>スクロール バーに沿ったスクロール ボックス (つまみとも呼ばれます) の動きを監視するイベントです。 使用して、<xref:System.Windows.Forms.ScrollBar.Scroll>がドラッグされていると、イベントがスクロール バーの値へのアクセスを提供します。  
  
## <a name="value-property"></a>Value プロパティ  
 <xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティ (つまり、既定では、0) は、`integer`スクロール バーのスクロール ボックスの位置に対応する値。 スクロール ボックスの位置は、最小値では、ときに、左端の位置 (水平スクロール バーまたは (垂直スクロール バーの上端の位置に移動します。 スクロール ボックスがの場合、最大値、一番右にスクロール ボックスの移動、または最下部の位置です。 同様に、範囲の上部と下部の中間値は、スクロール バーの途中でスクロール ボックスの先端を配置します。  
  
 に加えて、マウスのクリックを使用して、スクロール バーの値を変更する、ユーザーが任意の時点、バーのスクロール ボックスをドラッグすることもできます。 結果の値は、スクロール ボックスの位置によって異なりますが、範囲内では常に、<xref:System.Windows.Forms.ScrollBar.Minimum%2A>に<xref:System.Windows.Forms.ScrollBar.Maximum%2A>ユーザーによって設定されるプロパティです。  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange と SmallChange プロパティ  
 ユーザーが PAGEUP または PAGEDOWN キーを押すかスクロール ボックスのどちら側にスクロール バーのトラックをクリックしたときに、<xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティの変更に設定された値に従って、<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>プロパティです。  
  
 押されたときの矢印のいずれかのキーか、スクロール バーのボタンのいずれかをクリックすると、<xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティの変更に設定された値に従って、<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>プロパティです。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [.NET Framework 2.0 の Windows フォームへの追加](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
