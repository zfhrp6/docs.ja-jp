---
title: '方法 : タブ ページにコントロールを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 1bb2233cf9e288ae89ebb8cab3df4f6451dc8eed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526697"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a>方法 : タブ ページにコントロールを追加する
Windows フォームを使用することができます<xref:System.Windows.Forms.TabControl>を組織的に他のコントロールを表示します。 次の手順では、最初のタブにボタンを追加する方法を示します。タブ ページのラベルの一部にアイコンを追加する方法の詳細については、次を参照してください。[する方法: Windows フォーム TabControl の外観を変更](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)です。  
  
### <a name="to-add-a-control-programmatically"></a>コントロールをプログラムで追加するには  
  
1.  使用して、<xref:System.Windows.Forms.Control.ControlCollection.Add%2A>メソッドによって返されるコレクションの<xref:System.Windows.Forms.Control.Controls%2A>プロパティ<xref:System.Windows.Forms.TabPage>:  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [方法: Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [方法: タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [方法: Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
