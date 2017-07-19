---
title: "方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする | Microsoft Docs"
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
  - "セル, 変更 (DataGridView コントロール内の色を) [Windows フォーム]"
  - "色, 変更 (DataGridView コントロール内の) [Windows フォーム]"
  - "データ [Windows フォーム], 書式設定 (DataGridView コントロール内の)"
  - "データ グリッド, 書式設定 (データを)"
  - "DataGridView コントロール [Windows フォーム], セルのカスタマイズ"
  - "DataGridView コントロール [Windows フォーム], セル スタイル"
  - "DataGridView コントロール [Windows フォーム], 変更 (セルの色を)"
  - "DataGridView コントロール [Windows フォーム], 書式設定 (データを)"
  - "DataGridView コントロール [Windows フォーム], 置換 (表示するセル値を)"
  - "Windows フォーム, 変更 (DataGridView セルの色を)"
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする
次のコード例は、列と値に応じてセルの表示方法を変更する<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> イベントのハンドラーを実装する方法について説明します。  
  
 負の数値が含まれている `Balance` 列のセルは、赤の背景が指定されます。  これらのセルを通貨として書式設定し、負の値をかっこで囲んで表示することもできます。  詳細については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 `Priority` 列のセルは、対応するテキスト セル値の代わりにイメージを表示します。  <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> の<xref:System.Windows.Forms.ConvertEventArgs.Value%2A> プロパティはテキストのセル値を取得して、対応するイメージの表示値に設定する場合に使用されます。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
-   `highPri.bmp`、`mediumPri.bmp`、および `lowPri.bmp` という名前の <xref:System.Drawing.Bitmap> イメージは、実行可能ファイルと同じディレクトリにあります。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからのこの例のビルドについては、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Drawing.Bitmap>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)