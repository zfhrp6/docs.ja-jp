---
title: "方法 : Windows フォーム上のタブ オーダーを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7acca633a5a2b98d7c4b6dd64355996e763d6df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>方法 : Windows フォーム上のタブ オーダーを設定する
タブ オーダーでは、ユーザーが TAB キーを押して 1 つのコントロールからでフォーカスを移動する順序です。 各フォームには、独自のタブ オーダーがあります。 既定では、タブ オーダーは、コントロールを作成した順序と同じです。 タブ オーダーの番号は 0 から始まります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-set-the-tab-order-of-a-control"></a>コントロールのタブ オーダーを設定するには  
  
1.  **ビュー**  メニューのをクリックして**タブ オーダー**です。  
  
     これには、フォーム上のタブ オーダー選択モードがアクティブにします。 数値 (を表す、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティ) の各コントロールの左上隅に表示されます。  
  
2.  タブの順序を確立するために順番にコントロールをクリックします。  
  
    > [!NOTE]
    >  タブ オーダーのコントロールの位置は、0 以上、任意の値に設定できます。 重複が発生すると、2 つのコントロールの z オーダーが評価され、上位のコントロールが最初にタブ付き。 (Z オーダーは、フォームの z 軸 [奥行] に沿ってフォーム上のコントロールのビジュアルの重ね順です。 Z オーダーを決定するコントロールは、その他のコントロールの前にします。)Z オーダーの詳細については、次を参照してください。 [Windows フォームでのオブジェクトの階層構造](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md)です。  
  
3.  完了したら、をクリックして**タブ オーダー**上、**ビュー**タブ オーダー モードを終了するには、もう一度メニュー。  
  
    > [!NOTE]
    >  フォーカスを取得できません。 コントロールだけでなく、無効になっており、非表示のコントロールがない、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティであり、タブ オーダーに含まれません。 ユーザーは、TAB キーを押すと、これらのコントロールはスキップされます。  
  
 プロパティ ウィンドウを使用して、タブ オーダーを設定する代わりに、<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティです。 <xref:System.Windows.Forms.Control.TabIndex%2A>  タブの順序で配置されているコントロールのプロパティを決定します。 既定では、最初のコントロールの描画が、<xref:System.Windows.Forms.Control.TabIndex%2A>値 0、2 番目は、 <xref:System.Windows.Forms.Control.TabIndex%2A> 1 というようです。  
  
 さらに、既定では、<xref:System.Windows.Forms.GroupBox>コントロールが持つ独自<xref:System.Windows.Forms.Control.TabIndex%2A>られている整数値。 A<xref:System.Windows.Forms.GroupBox>コントロール自体は、実行時にフォーカスを持つことはできません。 したがって、各コントロール、<xref:System.Windows.Forms.GroupBox>独自の 10 進数を持つ<xref:System.Windows.Forms.Control.TabIndex%2A>.0 で始まる値。 当然ながら、として、<xref:System.Windows.Forms.Control.TabIndex%2A>の<xref:System.Windows.Forms.GroupBox>コントロールがインクリメントされます、内のコントロールが増加します。 変更した場合、 <xref:System.Windows.Forms.Control.TabIndex%2A> 5、6 ~ 値、 <xref:System.Windows.Forms.Control.TabIndex%2A> 6.0 というように、グループの最初のコントロールの値が自動的に変更します。  
  
 最後に、フォームのさまざまの任意のコントロールは、タブ オーダーでスキップできます。 通常は、TAB キーを押して連続して実行時の選択、タブ オーダー内の各コントロールです。 無効にして、<xref:System.Windows.Forms.Control.TabStop%2A>プロパティ、行うことができます、フォームのタブ オーダーで経由で渡されるコントロール。  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>タブ オーダーのコントロールを削除するには  
  
1.  コントロールの設定<xref:System.Windows.Forms.Control.TabStop%2A>プロパティを`false`プロパティ ウィンドウでします。  
  
     いる A コントロール<xref:System.Windows.Forms.Control.TabStop%2A>プロパティに設定された`false`TAB キーでコントロールを循環するときに、コントロールがスキップされた場合でも、タブ オーダー内での位置を維持できます。  
  
    > [!NOTE]
    >  ラジオ ボタン グループでは、実行時に停止する 1 つのタブがします。 選択したボタン (ボタンは、その<xref:System.Windows.Forms.RadioButton.Checked%2A>プロパティに設定`true`) がその<xref:System.Windows.Forms.Control.TabStop%2A>プロパティが自動的に設定`true`れ、他のボタン、<xref:System.Windows.Forms.Control.TabStop%2A>プロパティに設定`false`です。 グループ化の詳細については<xref:System.Windows.Forms.RadioButton>コントロールを参照してください[セットとして機能する Windows フォーム RadioButton コントロールをグループ化](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
