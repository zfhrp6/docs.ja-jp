---
title: "方法 : Windows フォームの 2 つの DataGridView コントロールを使用してマスター/詳細形式のフォームを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
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
  - "DataGridView コントロール [Windows フォーム], マスター/詳細形式のフォーム"
  - "マスター/詳細リスト, 作成"
  - "親/子テーブル, 表示 (Windows フォームに)"
ms.assetid: 99f6e876-3f7f-4139-9063-e36587c95b02
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 方法 : Windows フォームの 2 つの DataGridView コントロールを使用してマスター/詳細形式のフォームを作成する
次のコード例では、2 つの <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドされた 2 つの <xref:System.Windows.Forms.DataGridView> コントロールを使用してマスター\/詳細フォームを作成します。  データ ソースが、Northwind SQL Server のサンプル データベース、および `CustomerID` 列により 2 つに関連する <xref:System.Data.DataRelation> からの `Customers` テーブルと `Orders` テーブルを含む <xref:System.Data.DataSet> です。  
  
 1 つの <xref:System.Windows.Forms.BindingSource> はデータセットの親 `Customers` テーブルにバインドされます。  このデータは、マスタ <xref:System.Windows.Forms.DataGridView> コントロールに表示されます。  もう一方の <xref:System.Windows.Forms.BindingSource> は、最初のデータ コネクタにバインドされます。  2 つ目の <xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティは、<xref:System.Data.DataRelation> の名前に設定されます。  これにより、関連付けられている詳細の <xref:System.Windows.Forms.DataGridView> コントロールが、マスター <xref:System.Windows.Forms.DataGridView> コントロールの現在の行に対応する子の `Orders` テーブルの行を表示します。  
  
 このコード例の詳細な説明については、「[チュートリアル : Windows フォームの 2 つの DataGridView コントロールを使用したマスター\/詳細形式のフォームの作成](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagrids.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#00)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Windows.Forms、および System.XML の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからのこの例のビルドについては、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## .NET Framework セキュリティ  
 接続文字列内に機密情報 \(パスワードなど\) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [チュートリアル : Windows フォームの 2 つの DataGridView コントロールを使用したマスター\/詳細形式のフォームの作成](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagrids.md)   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)