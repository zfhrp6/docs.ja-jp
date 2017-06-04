---
title: "方法 : コントロール クラスを継承する | Microsoft Docs"
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
  - "Control クラス, 継承"
  - "カスタム コントロール [Windows フォーム], 作成"
  - "カスタム コントロール [Windows フォーム], 継承"
  - "継承, Windows フォーム カスタム コントロール"
  - "OnPaint メソッド [Windows フォーム]"
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : コントロール クラスを継承する
Windows フォームで使用する、完全なカスタム コントロールを作成する場合は、<xref:System.Windows.Forms.Control> クラスから継承する必要があります。  <xref:System.Windows.Forms.Control> クラスから継承する場合、多くの計画と実装が必要となりますが、非常に多様なオプションも用意されています。  <xref:System.Windows.Forms.Control> から継承すると、コントロールを動作させるためのごく基本的な機能だけが継承されます。  <xref:System.Windows.Forms.Control> クラス本来の機能は、キーボードやマウスによるユーザー入力の処理、コントロールの境界線およびサイズの定義、ウィンドウ ハンドルの提供、およびメッセージ処理とセキュリティの提供です。  描画機能、つまりこの場合はコントロールのグラフィカル インターフェイスを実際に表示する機能や、ユーザーとやり取りするための具体的な機能は含まれていません。  このような機能は、カスタム コードを記述して提供する必要があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### カスタム コントロールを作成するには  
  
1.  新しい **Windows アプリケーション** プロジェクトまたは **Windows コントロール ライブラリ** プロジェクトを作成します。  
  
2.  **\[プロジェクト\]** メニューの **\[クラスの追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスにある **\[カスタム コントロール\]** をクリックします。  
  
     新しいカスタム コントロールがプロジェクトに追加されます。  
  
4.  F7 キーを押してカスタム コントロールの**コード エディター**を開きます。  
  
5.  <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドを見つけます。このメソッドは、基本クラスの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドの呼び出しを除いて、空白になっています。  
  
6.  コントロールで使用するカスタム描画を含むように、コードを修正します。  
  
     コントロールのグラフィックスを描画するコードの作成については、「[コントロールのカスタム描画およびレンダリング](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)」を参照してください。  
  
7.  コントロールに含めるカスタム メソッド、カスタム プロパティ、カスタム イベントを実装します。  
  
8.  保存してコントロールの動作確認を行います。  
  
## 参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [方法 : UserControl クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [方法 : 既存の Windows フォーム コントロールから継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [方法 : Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)