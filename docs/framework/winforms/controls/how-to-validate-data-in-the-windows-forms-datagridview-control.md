---
title: "方法 : Windows フォーム DataGridView コントロールのデータを検証する | Microsoft Docs"
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
  - "データ [Windows フォーム], 検証"
  - "データ グリッド, 検証 (データを)"
  - "データの妥当性検査, Windows フォーム"
  - "DataGridView コントロール [Windows フォーム], データの妥当性検査"
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 方法 : Windows フォーム DataGridView コントロールのデータを検証する
ユーザーによって <xref:System.Windows.Forms.DataGridView> コントロールに入力されたデータを検証する方法を次のコード例に示します。  この例では、<xref:System.Windows.Forms.DataGridView> には、Northwind サンプル データベースの `Customers` テーブルの行が読み込まれます。  ユーザーが `CompanyName` 列内のセルを編集すると、値の有効性をテストするために、空ではないことが確認されます。  <xref:System.Windows.Forms.DataGridView.CellValidating> イベントのイベント ハンドラーによって値が空の文字列であることが検出されると、<xref:System.Windows.Forms.DataGridView> では、ユーザーが空ではない文字列を入力するまでそのセルから移動できなくなります。  
  
 このコード例の詳細な説明については、「[チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Windows.Forms、および System.XML の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細は、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## .NET Framework セキュリティ  
 接続文字列内に機密情報 \(パスワードなど\) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)