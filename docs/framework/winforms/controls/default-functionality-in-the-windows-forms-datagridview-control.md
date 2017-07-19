---
title: "Windows フォーム DataGridView コントロールの既定の機能 | Microsoft Docs"
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
  - "データ グリッド, 既定の機能 (DataGridView コントロール内の)"
  - "DataGridView コントロール [Windows フォーム], 既定の機能"
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows フォーム DataGridView コントロールの既定の機能
Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールには、既定の機能が多数用意されています。  
  
## 既定の機能  
 <xref:System.Windows.Forms.DataGridView> コントロールの既定の機能は次のとおりです。  
  
-   テーブルを垂直方向にスクロールしたときに表示されたままになる列ヘッダーおよび行ヘッダーを自動的に表示します。  
  
-   行ヘッダーには、現在の行を示す選択インジケーターが表示されます。  
  
-   最初のセルに、選択領域を示す四角形が表示されます。  
  
-   列の区分線をダブルクリックして、列のサイズを自動的に変更できます。  
  
-   アプリケーションの `Main` メソッドから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> メソッドを呼び出した場合には、Windows XP および Windows Server 2003 ファミリの visual スタイルが自動的にサポートされます。  
  
 また、既定では <xref:System.Windows.Forms.DataGridView> コントロールのコンテンツを編集できるようになっています。  
  
-   セルをダブルクリックするか F2 キーを押すと、セルは自動的に編集モードへ切り替わり、入力するとセルの内容が更新されます。  
  
-   グリッドを最後までスクロールすると、新規レコードを追加するための行が表示されます。  この行をクリックすると、既定値の設定された新しい行が <xref:System.Windows.Forms.DataGridView> コントロールに追加されます。  Esc キーを押すと、新しい行は消去されます。  
  
-   行ヘッダーをクリックすると、行全体が選択されます。  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを設定して、<xref:System.Windows.Forms.DataGridView> コントロールをデータ ソースにバインドすると、コントロールでは次のような処理を実行します。  
  
-   列ヘッダーのテキストとして、データ ソースの列の名を自動的に使用します。  
  
-   データ ソースの内容を読み込みます。  <xref:System.Windows.Forms.DataGridView> 列は、データ ソースの各列に対応させて自動的に作成されます。  
  
-   表示する各行に対応させてテーブル内に行を作成します。  
  
-   列ヘッダーをクリックすると、基になるデータに従って行を自動的に並べ替えます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)