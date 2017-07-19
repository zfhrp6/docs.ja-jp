---
title: "チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け | Microsoft Docs"
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
  - "ElementHost コントロール, コピーと貼り付け (デザイン時に)"
  - "相互運用性 [WPF]"
  - "Windows フォーム, コンテンツのコピーと貼り付け"
  - "WPF ユーザー コントロール, ホスト (Windows フォームで)"
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け
このチュートリアルでは、Windows フォーム間で Windows Presentation Foundation \(WPF\) コントロールをコピーする方法について説明します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   プロジェクトを作成する。  
  
-   WPF コントロールをコピーする。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## プロジェクトの作成  
 まず、Windows フォーム プロジェクトを作成します。  
  
> [!NOTE]
>  WPF コンテンツをホストする場合は、C\# プロジェクトと Visual Basic プロジェクトのみがサポートされます。  
  
#### プロジェクトを作成するには  
  
-   `CopyElementHost` という名前の新しい Windows フォーム アプリケーション プロジェクトを Visual Basic または Visual C\# で作成します。  
  
## WPF コントロールのコピー  
 プロジェクトに WPF コントロールを追加した後、プロジェクト内の他のフォームにコピーすることができます。  
  
#### WPF コントロールをコピーするには  
  
1.  新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。  コントロール型の既定の名前である `UserControl1.xaml` を使用します。  詳細については、「[チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)」を参照してください。  
  
2.  プロジェクトをビルドします。  
  
3.  Windows フォーム デザイナーで `Form1` を開きます。  
  
4.  **ツールボックス**から、`UserControl1` のインスタンスをフォームにドラッグします。  
  
     `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。  
  
5.  `elementHost1` を選択して、CTRL \+ C キーを押してクリップボードにコピーします。  
  
6.  新しい Windows フォームをプロジェクトに追加します。  フォームの種類の既定の名前である `Form2` を使用します。  
  
7.  Windows フォーム デザイナーで `Form2` を開いたまま、CTRL キーを押しながら V キーを押して、`elementHost1` のコピーをフォームに貼り付けます。  
  
     `Form2` クラスのプライベート フィールドであるため、コピーしたコントロールの名前も `elementHost1` です。  `Form1` クラスの `elementHost1` には名前の競合がありません。  
  
## 参照  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [WPF コントロールの使用](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)