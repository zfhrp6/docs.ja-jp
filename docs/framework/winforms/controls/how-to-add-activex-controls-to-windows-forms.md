---
title: '方法 : Windows フォームに ActiveX コントロールを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: c851a215638e60642bf93564f4884b5a79d430d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>方法 : Windows フォームに ActiveX コントロールを追加する
Windows フォーム コントロールをホストするには、Windows フォーム デザイナーが最適化され、ときにも Windows フォームで ActiveX コントロールを配置することができます。  
  
> [!CAUTION]
>  ActiveX コントロールに追加されるときに、Windows フォームのパフォーマンスの制限があります。  
  
 ActiveX コントロールをフォームに追加する前に、ツールボックスに追加する必要があります。 詳細については、次を参照してください。 [COM コンポーネント、ツールボックスのカスタマイズ ダイアログ ボックス](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Windows フォームに ActiveX コントロールを追加するには  
  
-   ツールボックスでコントロールをダブルクリックします。  
  
     Visual Studio は、プロジェクト内のコントロールへのすべての参照を追加します。 Windows フォームで ActiveX コントロールを使用する場合に留意すべきことに関する詳細については、次を参照してください。 [Windows フォームで ActiveX コントロールをホストしている場合の考慮事項](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)です。  
  
    > [!NOTE]
    >  Windows フォーム ActiveX コントロール インポーター (AxImp.exe) は、ActiveX のダイナミック リンク ライブラリのインポート時に予想よりも、別の種類のイベント引数を作成します。 AxImp.exe によって作成された引数は、次のような: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`、`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`が必要です。 この不規則性は防止しませんコードが正常に注意してください。 詳細については、「 [Windows フォーム ActiveX コントロール インポーター (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)  
 [各言語およびライブラリにおける、コントロールとプログラミング可能オブジェクトの比較](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
