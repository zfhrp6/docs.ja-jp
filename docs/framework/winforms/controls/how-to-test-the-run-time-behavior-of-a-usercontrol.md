---
title: "方法 : UserControl の実行時の動作をテストする | Microsoft Docs"
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
  - "複合コントロール, テスト"
  - "ユーザー コントロール [Windows フォーム], テスト"
  - "UserControl クラス, 実行時の動作"
  - "UserControl クラス, テスト"
  - "UserControl テスト コンテナー"
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : UserControl の実行時の動作をテストする
<xref:System.Windows.Forms.UserControl> を開発したときは、実行時の動作をテストする必要があります。  別個の Windows ベース アプリケーション プロジェクトを作成し、コントロールをテスト フォームに配置できますが、この手順は手間がかかります。  それよりも Visual Studio の **UserControl テスト コンテナー**を使用する方がすばやく簡単にテストできます。  このテスト コンテナーは、Windows コントロール ライブラリ プロジェクトから直接起動します。  
  
> [!IMPORTANT]
>  テスト コンテナーに <xref:System.Windows.Forms.UserControl> を読み込むには、コントロールには少なくとも 1 つのパブリック コンストラクターが必要です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
> [!NOTE]
>  Visual C\+\+ コントロールは**ユーザー コントロール テスト コンテナー**でテストできません。  
  
### UserControl の実行時の動作をテストするには  
  
1.  TestContainerExample という名前の Windows コントロール ライブラリ プロジェクトを作成します。  詳細については、「[Windows Control Library Template](http://msdn.microsoft.com/ja-jp/722f4e2d-1310-4ed5-8f33-593337ab66b4)」を参照してください。  
  
2.  **Windows フォーム デザイナー**で、**ツールボックス**の <xref:System.Windows.Forms.Label> コントロールをコントロールのデザイン サーフェイスにドラッグします。  
  
3.  F5 キーを押してプロジェクトをビルドし、**UserControl テスト コンテナー**を実行します。  テスト コンテナーと <xref:System.Windows.Forms.UserControl> が**プレビュー** ペインに表示されます。  
  
4.  **プレビュー** ペインの右側の <xref:System.Windows.Forms.PropertyGrid> コントロールに表示されている <xref:System.Windows.Forms.Control.BackColor%2A> プロパティを選択します。  プロパティの値を `ControlDark` に変更します。  コントロールが暗い色に変化することを確認します。  他のプロパティ値も変更してみて、コントロールへの影響を観察します。  
  
5.  **プレビュー** ペインの下の **\[ユーザー コントロールの四辺にドッキング\]** チェック ボックスをクリックします。  コントロールのサイズがペイン全体に拡大することを確認します。  テスト コンテナーのサイズを変更し、ペインと共にコントロールのサイズが変更されることを確認します。  
  
6.  テスト コンテナーを閉じます。  
  
7.  TestContainerExample プロジェクトに別のユーザー コントロールを追加します。  詳細については、「[NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/ja-jp/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)」を参照してください。  
  
8.  **Windows フォーム デザイナー**で、**ツールボックス**の <xref:System.Windows.Forms.Button> コントロールをコントロールのデザイン サーフェイスにドラッグします。  
  
9. F5 キーを押してプロジェクトをビルドし、テスト コンテナーを実行します。  
  
10. **\[ユーザー コントロールの選択\]** <xref:System.Windows.Forms.ComboBox> をクリックし、2 つのユーザー コントロールを切り替えます。  
  
## 別のプロジェクトのユーザー コントロールのテスト  
 現在のプロジェクトのテスト コンテナーで、別のプロジェクトのユーザー コントロールをテストできます。  
  
#### 別のプロジェクトのユーザー コントロールをテストするには  
  
1.  TestContainerExample2 という名前の Windows コントロール ライブラリ プロジェクトを作成します。  詳細については、「[Windows Control Library Template](http://msdn.microsoft.com/ja-jp/722f4e2d-1310-4ed5-8f33-593337ab66b4)」を参照してください。  
  
2.  **Windows フォーム デザイナー**で、**ツールボックス**の <xref:System.Windows.Forms.RadioButton> コントロールをコントロールのデザイン サーフェイスにドラッグします。  
  
3.  F5 キーを押してプロジェクトをビルドし、テスト コンテナーを実行します。  テスト コンテナーと <xref:System.Windows.Forms.UserControl> が**プレビュー** ペインに表示されます。  
  
4.  **\[読み込み\]** をクリックします。  
  
5.  **\[ファイルを開く\]** ダイアログ ボックスで、前の手順でビルドした TestContainerExample.dll に移動します。  TestContainerExample.dll を選択し、**\[開く\]** をクリックしてユーザー コントロールを読み込みます。  
  
6.  **\[ユーザー コントロールの選択\]** <xref:System.Windows.Forms.ComboBox> を使用して、TestContainerExample プロジェクトの 2 つのユーザー コントロールを切り替えます。  
  
## 参照  
 <xref:System.Windows.Forms.UserControl>   
 [方法 : 複合コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)   
 [チュートリアル : Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [チュートリアル : Visual C\# による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)   
 [User Control Designer](http://msdn.microsoft.com/ja-jp/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)