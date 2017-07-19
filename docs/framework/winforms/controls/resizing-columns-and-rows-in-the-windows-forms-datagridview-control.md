---
title: "Windows フォーム DataGridView コントロール内の列と行のサイズ変更 | Microsoft Docs"
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
  - "列 [Windows フォーム], サイズ変更 (グリッドの)"
  - "データ グリッド, サイズ変更 (列と行を)"
  - "DataGridView コントロール [Windows フォーム], サイズ変更 (行と列を)"
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Windows フォーム DataGridView コントロール内の列と行のサイズ変更
`DataGridView` コントロールには、列と行のサイズ変更の動作をカスタマイズするさまざまな機能が用意されています。  通常、`DataGridView` のセルは、内容に基づくサイズ変更を行いません。  セルのサイズよりも大きい表示値は、一部だけが表示されます。  文字列として表示可能な内容は、ツールヒント内に表示されます。  
  
 既定では、行、列、およびヘッダーの区分線をユーザーがマウスでドラッグすることにより、より多くの情報を表示できるようになっています。  また、ユーザーが区分線をダブルクリックすると、関連する行、列、またはヘッダーのサイズは、内容に応じて自動的にサイズ変更されます。  
  
 `DataGridView` コントロールには、このようなすべてのユーザー操作をカスタマイズしたり無効にしたりするためのプロパティ、メソッド、およびイベントがあります。  また、プログラムによって、行、列、およびヘッダーのサイズを内容に基づいて変更したり、内容が変更されるたびに自動的にサイズ変更されるように設定したりすることもできます。  列の設定によって、使用できるコントロールの幅が指定した比率で自動的に分割されるようにもできます。  
  
## このセクションの内容  
 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 行、列、およびヘッダーのサイズ変更の機能について説明します。  また、サイズ変更関連のプロパティとメソッドの詳細を示し、一般的な使用シナリオを説明します。  
  
 [Windows フォーム DataGridView コントロールの列フィル モード](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 列フィル モードについて詳しく説明し、列フィル モードおよびその他のモードを試すために使用できるデモ用のコードを示します。  
  
 [方法 : Windows フォーム DataGridView コントロールのサイズ変更モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 一般的な用途でのサイズ変更モードの設定方法について説明します。  
  
 [方法 : Windows フォームの DataGridView コントロールの内容に合わせてセルのサイズをプログラムで変更する](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 プログラミングによるサイズ変更を試すために使用できるデモ用のコードを示します。  
  
 [方法 : Windows フォームの DataGridView コントロールの内容変更時にセルのサイズを自動的に変更する](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 自動サイズ変更モードを試すために使用できるデモ用のコードを示します。  
  
## 関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールの参照ドキュメントを提供します。  
  
## 参照  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)