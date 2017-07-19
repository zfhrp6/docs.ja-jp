---
title: "方法 : Windows フォームに ActiveX コントロールを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ActiveX コントロール [Windows フォーム], 追加"
  - "フォーム, 追加 (ActiveX コントロールを)"
  - "Windows フォーム コントロール, ActiveX コントロール"
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォームに ActiveX コントロールを追加する
Windows フォーム デザイナーは、Windows フォーム コントロールをホストするために最適化されていますが、代わりに Windows フォームに ActiveX コントロールを配置することもできます。  
  
> [!CAUTION]
>  ActiveX コントロールを Windows フォームに追加した場合は、Windows フォームのパフォーマンスが制限されます。  
  
 フォームに ActiveX コントロールを追加する前に、ツールボックスに ActiveX コントロールを追加する必要があります。  詳細については、「[&#91;COM コンポーネント&#93; \(&#91;ツールボックスのカスタマイズ&#93; ダイアログ ボックス\)](http://msdn.microsoft.com/ja-jp/171333f3-f207-4e02-bbdc-17862556212c)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### Windows フォームに ActiveX コントロールを追加するには  
  
-   ツールボックスでコントロールをダブルクリックします。  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] によって、プロジェクトのコントロールにすべての参照が追加されます。  Windows フォーム上で ActiveX コントロールを使用する場合の注意事項の詳細については、「[Windows フォームで ActiveX コントロールをホストする場合の考慮事項](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)」を参照してください。  
  
    > [!NOTE]
    >  Windows フォーム ActiveX コントロール インポーター \(AxImp.exe\) は、ActiveX ダイナミック リンク ライブラリのインポート時に、変則的な型のイベント引数を作成します。  AxImp.exe によって作成される引数は、`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` ではなく、実際には `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)` のようになります。  この変則性によって、コードの正常な機能が妨げられないように注意してください。  詳細については、「[Windows フォーム ActiveX コントロール インポーター \(Aximp.exe\)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)」を参照してください。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Controls and Programmable Objects Compared in Various Languages and Libraries](http://msdn.microsoft.com/ja-jp/021f2a1b-8247-4348-a5ad-e1d9ab23004b)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)