---
title: "方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする | Microsoft Docs"
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
  - "BindingSource コンポーネント [Windows フォーム], バインド (コントロールを)"
  - "コントロール [Windows フォーム], バインド"
  - "データ バインド, BindingSource コンポーネント"
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする
コントロールをフォームに追加し、アプリケーションのユーザー インターフェイスを決定したら、実行時にユーザーがアプリケーションに関するデータを変更および保存できるようにコントロールをデータ ソースにバインドできます。  
  
 Windows フォーム上の特定のコントロールまたは一連のコントロールをバインドする場合、フォーム上のコントロールとデータ ソース間の橋渡しとして <xref:System.Windows.Forms.BindingSource> コントロールを使用する方法が最も簡単です。  
  
 フォーム上の 1 つ以上のコントロールをデータにバインドできます。次の手順では、<xref:System.Windows.Forms.TextBox> コントロールをデータ ソースにバインドします。  
  
 この手順では、データベースから派生したデータ ソースにバインドするものと仮定します。  他のデータ ストアからデータ ソースを作成する方法の詳細については、「[データ ソースの概要](../Topic/Add%20new%20data%20sources.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にコントロールをバインドするには  
  
1.  <xref:System.Windows.Forms.TextBox> コントロールをフォーム上にドラッグします。  
  
2.  **\[プロパティ\]** ウィンドウで、次の操作を行います。  
  
    1.  **\[Databindings\]** ノードを展開します。  
  
    2.  <xref:System.Windows.Forms.TextBox.Text%2A> プロパティの横にある矢印をクリックします。  
  
         **DataSource** UI 型エディターが開きます。  
  
         データ ソースが既にこのプロジェクトまたはフォーム用に構成されている場合は、そのデータ ソースが表示されます。  
  
3.  **\[プロジェクト データ ソースの追加\]** をクリックしてデータに接続し、データ ソースを作成します。  
  
4.  **データ ソース構成ウィザード**の \[ようこそ\] ページで、**\[次へ\]** をクリックします。  
  
5.  **\[データ ソースの種類を選択\]** ページで、**\[データベース\]** を選択します。  
  
6.  **\[データ接続の選択\]** ページで、使用できる接続の一覧からデータ接続を選択します。  目的のデータ接続が表示されていないときは、**\[新しい接続\]** をクリックして新しいデータ接続を作成します。  
  
7.  **\[次の名前で接続を保存する\]** をクリックして、アプリケーション構成ファイルに接続文字列を保存します。  
  
8.  アプリケーションで使用するデータベース オブジェクトを選択します。  この場合は、<xref:System.Windows.Forms.TextBox> に表示するテーブルのフィールドを選択します。  
  
9. 必要に応じて、既定のデータセット名を変更します。  
  
10. **\[完了\]** をクリックします。  
  
11. **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.TextBox.Text%2A> プロパティの横にある矢印をもう一度クリックします。  **DataSource** UI 型エディターで、<xref:System.Windows.Forms.TextBox> をバインドするフィールドの名前を選択します。  
  
     **DataSource** UI 型エディターが閉じられ、データ接続に固有のデータセット、<xref:System.Windows.Forms.BindingSource>、およびテーブル アダプターがフォームに追加されます。  
  
## 参照  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.BindingNavigator>   
 [データ ソースの概要](../Topic/Add%20new%20data%20sources.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)