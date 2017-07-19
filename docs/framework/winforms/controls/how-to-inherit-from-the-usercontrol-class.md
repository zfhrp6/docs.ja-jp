---
title: "方法 : UserControl クラスを継承する | Microsoft Docs"
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
  - "複合コントロール, 作成"
  - "継承, Windows フォーム カスタム コントロール"
  - "ユーザー コントロール [Windows フォーム], 作成"
  - "UserControl クラス, 継承"
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : UserControl クラスを継承する
1 つ以上の Windows フォーム コントロールの機能をカスタム コードと組み合わせるには、*ユーザー コントロール*を作成します。  ユーザー コントロールは、迅速なコントロール開発、標準の Windows フォーム コントロールの機能、およびカスタム プロパティやカスタム メソッドの柔軟性を兼ね備えています。  ユーザー コントロールの作成を開始すると、デザイナーが表示され、標準の Windows フォーム コントロールを配置できます。  これらのコントロールは、標準コントロールの外観と動作に加えて、継承した機能のすべてを保持します。  ただし、これらのコントロールをユーザー コントロールに組み込んだ場合、コードを介して使用することはできなくなります。  ユーザー コントロールは独自の描画を行い、標準コントロールに関連付けられた基本的な機能もすべて処理します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### ユーザー コントロールを作成するには  
  
1.  新しい **Windows コントロール ライブラリ** プロジェクトを作成します。  
  
     空白のユーザー コントロールを持つ新しいプロジェクトが作成されます。  
  
2.  **ツールボックス**の **\[Windows フォーム\]** タブから、コントロールをデザイナーにドラッグします。  
  
3.  これらのコントロールは、最終的なユーザー コントロールに表示するときと同じように、配置およびデザインする必要があります。  開発者が内在コントロールにアクセスできるようにする場合は、内在コントロールをパブリックとして宣言するか、内在コントロールの選択したプロパティを公開します。  詳細については、「[方法 : 内在コントロールのプロパティを公開する](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)」を参照してください。  
  
4.  コントロールに含めるカスタム メソッドやカスタム プロパティを実装します。  
  
5.  F5 キーを押してプロジェクトをビルドし、**ユーザー コントロール テスト コンテナー**でコントロールを実行します。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
## 参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [方法 : コントロール クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [方法 : 既存の Windows フォーム コントロールから継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [方法 : Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)