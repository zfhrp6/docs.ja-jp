---
title: "方法 : Windows フォーム上のオブジェクトをレイヤー化する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], レイヤー化"
  - "コントロール [Windows フォーム], 配置"
  - "Windows フォーム コントロール, レイヤー化"
  - "z オーダー"
  - "z オーダー"
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム上のオブジェクトをレイヤー化する
複雑なユーザー インターフェイスを作成したり、マルチ ドキュメント インターフェイス \(MDI\) フォームを使用したりする場合は、コントロールと子フォームをレイヤー化する必要が生じることがよくあります。  グループのコンテキストで、コントロールとウィンドウを移動および制御するには、コントロールの z オーダーを操作します。  *Z オーダー*は、コントロールの視覚的な階層構造であり、フォームの z 軸 \(奥行\) に沿ってフォームに描かれます。  z オーダーのウィンドウは、ほかのすべてのウィンドウの上に重ねて、一番上に表示されます。  ほかのすべてのウィンドウは、z オーダーのウィンドウの下に重ねて表示されます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にコントロールをレイヤー化するには  
  
1.  レイヤー化するコントロールを選択します。  
  
2.  **\[書式\]** メニューの **\[順序\]** をポイントし、**\[最前面へ移動\]** または **\[最背面へ移動\]** をクリックします。  
  
### プログラムによってコントロールをレイヤー化するには  
  
-   <xref:System.Windows.Forms.Control.BringToFront%2A> メソッドおよび <xref:System.Windows.Forms.Control.SendToBack%2A> メソッドを使用して、コントロールの z オーダーを操作します。  
  
     たとえば、<xref:System.Windows.Forms.TextBox> コントロール `txtFirstName` が別のコントロールの下に表示されている場合は、次のコードを使用して、一番上に表示します。  
  
    ```vb  
    txtFirstName.BringToFront()  
  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows フォームでは、*コントロール コンテインメント*をサポートしています。  コントロール コンテインメントとは、コンテナーであるコントロールに、さまざまなコントロールが配置されている状態です。たとえば、<xref:System.Windows.Forms.GroupBox> コントロールには、さまざまな <xref:System.Windows.Forms.RadioButton> コントロールが含まれています。  このとき、コンテナーであるコントロールでコントロールをレイヤー化できます。  グループ ボックスを移動すると、中に含まれているコントロールも移動されます。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)