---
title: "方法 : XAML を使用してテーブルを定義する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドキュメント, 定義 (XAML でテーブルを)"
  - "テーブル, 定義 (XAML で)"
  - "XAML, 定義 (テーブルを)"
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : XAML を使用してテーブルを定義する
この例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して <xref:System.Windows.Documents.Table> を定義する方法を示します。  例で定義するテーブルには、4 つの列 \(<xref:System.Windows.Documents.TableColumn> 要素によって表される\) といくつかの行 \(<xref:System.Windows.Documents.TableRow> 要素によって表される\) があり、データの他にタイトル、ヘッダー、およびフッターの情報を格納します。  行は、<xref:System.Windows.Documents.TableRowGroup> 要素に格納する必要があります。  テーブルの各行は、1 つ以上のセル \(<xref:System.Windows.Documents.TableCell> 要素によって表される\) で構成されます。  テーブルのセル内のコンテンツは、<xref:System.Windows.Documents.Block> 要素に格納する必要があります。この例では、<xref:System.Windows.Documents.Paragraph> 要素を使用しています。  このテーブルには、ハイパーリンク \(<xref:System.Windows.Documents.Hyperlink> 要素で表される\) もフッター行内にあります。  
  
## 使用例  
 [!code-xml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 この例で定義されたテーブルのレンダリング結果を次の図に示します。  
  
 ![描画されたテーブル。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")