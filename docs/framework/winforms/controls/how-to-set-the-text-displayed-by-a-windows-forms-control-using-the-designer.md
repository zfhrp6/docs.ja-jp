---
title: "方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6d49466e5dd25bbe9e97262d68f2c3fb2f8ba1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する
Windows フォーム コントロールは、通常、コントロールの主な機能に関連するいくつかのテキストを表示します。 たとえば、<xref:System.Windows.Forms.Button>コントロールには、通常、ボタンがクリックされたときに実行するアクションを示すキャプションが表示されます。 すべてのコントロールに対して、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用してテキストを設定または返すことができます。 <xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して、フォントを変更することができます。  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a>テキストと、デザイナーでのフォントを設定するには  
  
1.  [プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.Control.Text%2A>適切な文字列をコントロールのプロパティです。  
  
     下線付きのショートカット キーを作成する、アンパサンドが含まれています (&) は、ショートカット キーとなる文字の前にします。  
  
2.  [プロパティ] ウィンドウで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、<xref:System.Windows.Forms.Control.Font%2A>プロパティです。  
  
     標準のフォント ダイアログ ボックスで、フォント、フォント スタイル、サイズ、(取り消し線、下線) などの効果とスクリプトを選択します。  
  
## <a name="see-also"></a>参照  
 [方法: Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
