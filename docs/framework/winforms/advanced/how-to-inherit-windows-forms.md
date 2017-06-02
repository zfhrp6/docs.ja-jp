---
title: "方法 : Windows フォームを継承する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "継承, フォーム"
  - "継承フォーム, 作成 (実行時に)"
  - "Windows フォーム, 継承"
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームを継承する
新規の Windows フォームは、基本フォームから継承して簡単に複製できます。フォームが必要になるたびに、最初から作成し直す必要はありません。  
  
 デザイン時に **\[継承ピッカー\]** ダイアログ ボックスを使用してフォームを継承する方法、および継承されるコントロールのセキュリティ レベルを視覚的に区別する方法の詳細については、「[方法: &#91;継承ピッカー&#93; ダイアログ ボックスを使用してフォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)」を参照してください。  
  
 **メモ** フォームを継承するには、実行可能ファイルまたはダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) の形式で、継承元のフォームを含むファイルや名前空間を作成しておく必要があります。  プロジェクトを作成するには、**\[ビルド\]** メニューの **\[ビルド\]** を選択します。  また、フォームの継承先となるクラスに、名前空間への参照を追加する必要があります。  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### プログラムによってフォームを継承するには  
  
1.  クラスに、継承元のフォームを含む名前空間への参照を追加します。  
  
2.  クラス定義に、継承元のフォームへの参照を追加します。  参照では、フォームを含んでいる名前空間を指定し、その後にピリオド、続いて基本フォーム自体の名前を指定します。  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
  
    ```  
  
 フォームを継承する場合は、イベント ハンドラーが 2 回呼び出されることで問題が発生する可能性があることに注意してください。これは、各イベントが基底クラスと継承クラスの両方によって処理されるためです。  この問題を回避する方法の詳細については、「[Visual Basic で継承されたイベント ハンドラーのトラブルシューティング](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)」を参照してください。  
  
## 参照  
 [Inherits Statement](../../../../ocs/visual-basic/language-reference/statements/inherits-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../ocs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [使用](../Topic/using%20\(C%23%20Reference\).md)   
 [基本フォームの外観を変更した場合の影響](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)   
 [Windows フォームのビジュアルの継承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)