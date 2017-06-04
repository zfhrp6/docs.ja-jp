---
title: "方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する | Microsoft Docs"
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
  - "ADO.NET [Windows フォーム]"
  - "BindingSource コンポーネント [Windows フォーム], 並べ替えとフィルター処理 (データを)"
  - "データ [Windows フォーム], フィルター処理"
  - "データ [Windows フォーム], 並べ替え"
  - "データの並べ替え, ADO.NET"
  - "フィルター処理 [Windows フォーム], ADO.NET"
  - "並べ替え (データの)"
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム BindingSource コンポーネントで ADO.NET データを並べ替える/フィルター処理する
<xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティと <xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティを使用して、<xref:System.Windows.Forms.BindingSource> コントロールの並べ替え機能とフィルター機能を公開できます。  基になるデータ ソースが <xref:System.ComponentModel.IBindingList> のときは単純な並べ替えを適用できます。また、データ ソースが <xref:System.ComponentModel.IBindingListView> のときはフィルター処理と高度な並べ替えを適用できます。  <xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティは、標準の [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 構文を必要とします。この構文では、データ ソース内のデータ列の名前を表す文字列に続けて、リストの並べ替えを昇順、降順のどちらで行うかを示す `ASC` または `DESC` を指定します。  高度な並べ替えや複数列の並べ替えを設定するには、コンマ \(区切り記号\) で各列を区切ります。  <xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティには文字列式を設定します。  
  
> [!NOTE]
>  接続文字列内にパスワードなどの機密情報を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
### BindingSource を使用してデータをフィルター処理するには  
  
-   <xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティを任意の式に設定します。  
  
     列名とその列に指定する値を次のコード例に示します。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### BindingSource を使用してデータを並べ替えるには  
  
1.  <xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティを設定します。任意の列名に続けて、昇順または降順を示す `ASC` または `DESC` を指定してください。  
  
2.  複数の列を指定するときは、コンマで区切ります。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## 使用例  
 Northwind サンプル データベースの顧客テーブルから <xref:System.Windows.Forms.DataGridView> コントロールにデータを読み込み、表示データのフィルター処理および並べ替えを行う方法を次のコード例に示します。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## コードのコンパイル  
 この例を実行するには、`BindingSource1` という名前の <xref:System.Windows.Forms.BindingSource> および `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> を含むフォームにコードを貼り付けます。  次に、フォームの <xref:System.Windows.Forms.Form.Load> イベントを処理し、Load イベント ハンドラー メソッド内で `InitializeSortedFilteredBindingSource` を呼び出します。  
  
## 参照  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>   
 <xref:System.Windows.Forms.BindingSource.Filter%2A>   
 [方法 : サンプル データベースをインストールする](../Topic/How%20to:%20Install%20Sample%20Databases.md)   
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)