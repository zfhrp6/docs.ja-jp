---
title: プロパティ変更イベント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: f4e6a6267df88cdd33a58093f276c6005209f38d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536242"
---
# <a name="property-changed-events"></a>プロパティ変更イベント
いう名前のプロパティの通知を送信する、制御したいかどうか*PropertyName*という名前のイベントを定義する、変更*PropertyName* `Changed`という名前のメソッドと`On` *PropertyName* `Changed`イベントを発生させます。 Windows フォームの名前付け規則では、単語を追加*Changed*プロパティの名前にします。 プロパティ変更イベントに関連付けられているイベントのデリゲート型は<xref:System.EventHandler>、イベントのデータ型は、<xref:System.EventArgs>です。 基本クラス<xref:System.Windows.Forms.Control>など多数のプロパティ変更イベントを定義<xref:System.Windows.Forms.Control.BackColorChanged>、 <xref:System.Windows.Forms.Control.BackgroundImageChanged>、 <xref:System.Windows.Forms.Control.FontChanged>、 <xref:System.Windows.Forms.Control.LocationChanged>、およびその他。 イベントに関する背景情報については、次を参照してください。[イベント](../../../../docs/standard/events/index.md)と[Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)です。  
  
 プロパティ変更イベントは、コントロールの変更に応答するイベント ハンドラーをアタッチするコンシューマーが追加できるため便利です。 コントロールを生成するプロパティ変更イベントに応答する場合は、上書き、対応する`On` *PropertyName* `Changed`メソッド、イベントにデリゲートをアタッチする代わりにします。 その他のプロパティを更新するかの描画サーフェイスの一部またはすべてを再描画して、コントロールは通常、プロパティ変更イベントに応答します。  
  
 例を次にどのように`FlashTrackBar`に対するいくつかのプロパティ変更イベントから継承するカスタム コントロールの応答<xref:System.Windows.Forms.Control>です。 サンプル全体については、次を参照してください。[する方法: Windows フォーム コントロールを示しています進行状況を作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)です。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../../docs/standard/events/index.md)  
 [Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
