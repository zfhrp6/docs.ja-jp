---
title: '方法 : Windows フォームにコントロールをロックする'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: f05da53f134f13bf5edbbe7ab8c5973f79bbca4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-lock-controls-to-windows-forms"></a>方法 : Windows フォームにコントロールをロックする
Windows アプリケーションのユーザー インターフェイス (UI) を設計するときは、正しく配置を誤って移動や、その他のプロパティを設定するときのサイズを変更しないように後に、コントロールをロックできます。  
  
 さらに、ロックして、フォームを一度に多くのコントロールをフォームは、上のすべてのコントロールをロック解除することができますか、個々 のコントロールのロックを解除することができます。 配置した後のすべてのコントロール、好きな場所、フォームに、ロックがすべて適用誤って移動しないようにします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-lock-a-control"></a>コントロールをロックするには  
  
1.  **プロパティ**ウィンドウで、をクリックして、**ロック**プロパティを選択`true`です。 (名前をダブルクリックするとは、プロパティの設定を切り替えます。)  
  
     また、コントロールを右クリックして選択**ロック コントロール**です。  
  
    > [!NOTE]
    >  コントロールのロックが原因でデザイン画面で、新しいサイズまたは場所にドラッグされているからです。 ただし、することができます、サイズや位置を変更ことで、コントロールの**プロパティ**ウィンドウまたはコード。  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>フォーム上のすべてのコントロールをロックするには  
  
1.  **形式**] メニューの [選択**ロック コントロール**です。  
  
    > [!NOTE]
    >  このコマンドでは、フォームがコントロールであるため、フォームのサイズがロックされます。  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>フォーム上のコントロールがロックされているすべてのロックを解除するには  
  
1.  **形式**] メニューの [選択**ロック コントロール**です。  
  
     フォーム上のすべてのロックされているコントロールを今すぐはロックを解除します。  
  
### <a name="to-unlock-locked-controls-individually"></a>ロックを解除するには、コントロールを個別にロック  
  
1.  **プロパティ**ウィンドウで、をクリックして、**ロック**プロパティを選択`false`です。 (名前をダブルクリックするとは、プロパティの設定を切り替えます。)  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
