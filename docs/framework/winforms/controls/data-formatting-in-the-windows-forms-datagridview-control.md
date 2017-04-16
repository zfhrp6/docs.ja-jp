---
title: "Windows フォーム DataGridView コントロールでのデータの書式設定 | Microsoft Docs"
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
  - "データ [Windows フォーム], 書式設定 (グリッド内の)"
  - "データ グリッド, 書式設定 (データを)"
  - "DataGridView コントロール [Windows フォーム], 書式設定 (データを)"
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows フォーム DataGridView コントロールでのデータの書式設定
<xref:System.Windows.Forms.DataGridView> コントロールでは、セル値と、親列に表示されるデータ型を自動的に変換できます。  たとえば、テキスト ボックス列には、日付値、時刻値、数値、および列挙値が文字列形式で表示され、ユーザーが入力した文字列値が、データ ストアで必要な型に変換されます。  
  
## DataGridViewCellStyle クラスを使用した書式設定  
 <xref:System.Windows.Forms.DataGridView> コントロールでは、<xref:System.Windows.Forms.DataGridViewCellStyle> クラスを介して、セル値の基本的なデータ書式設定を実行できます。  <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> プロパティを使用すると、「[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)」に記載されている書式指定子を使用し、現在の既定のカルチャに合わせて日付値、時刻値、数値、および列挙値の書式を設定できます。  また、<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> プロパティを使用すると、これらの値の書式を、特定のカルチャに合わせて設定できます。  指定した書式を使用して、データを表示したり、指定した書式でユーザーが入力したデータを解析したりできます。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> クラスは、ワード ラップ、テキストの配置、および null データベース値のカスタム表示に必要な追加の書式設定プロパティを提供します。  詳細については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## CellFormatting イベントを使用した書式設定  
 基本的な書式設定がニーズに適合しない場合は、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> イベントのハンドラーでカスタム データ書式設定を実行できます。  このハンドラーに渡される <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> には、初期値としてセル値を含む <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> プロパティがあります。  通常、この値は、表示型に自動的に変換されます。  この値を独自に変換するには、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A> プロパティに表示型の値を設定します。  
  
> [!NOTE]
>  書式指定文字列がセルに対して有効な場合は、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> プロパティを `true` に設定している場合を除き、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A> プロパティ値の変更内容が書式指定文字列によってオーバーライドされます。  
  
 また、<xref:System.Windows.Forms.DataGridView.CellFormatting> イベントは、個々のセルの <xref:System.Windows.Forms.DataGridViewCellStyle> プロパティを、それぞれの値に基づいて設定するときにも役立ちます。  詳細については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 ユーザー指定値の既定の解析がニーズに適合しない場合は、<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CellParsing> イベントを処理して、カスタム解析を実行できます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)