---
title: "方法 : Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する | Microsoft Docs"
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
  - "データ グリッド, 行のスタイル"
  - "DataGridView コントロール [Windows フォーム], 行のスタイル"
  - "行, データ グリッド"
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する
表形式のデータは、多くの場合、行の背景色が交互に別の色になった、帳簿のような形式でユーザーに表示されます。  この形式を使用すると、多数の列がある幅の広いテーブルで、ユーザーが各行にあるセルを簡単に識別できるようになります。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールを使用すると、1 行おきの完全なスタイル情報を指定できます。  これにより、背景色だけでなく、前景色とフォントなどのスタイルの特性を使用して、交互の行を区別することができます。  
  
 Visual Studio では、このタスクに対するサポートが用意されています。  「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\))」も参照してください。  
  
### 交互の行のスタイルをプログラムで設定する  
  
-   <xref:System.Windows.Forms.DataGridView> の <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> プロパティと <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> プロパティにより返される <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトのプロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> プロパティと <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> プロパティを使用して指定したスタイルは、列と <xref:System.Windows.Forms.DataGridView> のレベルで指定されたスタイルをオーバーライドしますが、個別の行とセルのレベルで設定されたスタイルによってオーバーライドされます。  詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName>、および <xref:System.Windows.Forms?displayProperty=fullName> の各アセンブリへの参照。  
  
## 信頼性の高いプログラミング  
 最大限のスケーラビリティを実現するには、各要素のスタイルのプロパティを個別に設定するのではなく、同じスタイルを使用する複数の行、列、またはセルで <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを共有してください。  詳細については、「[Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのフォントと色のスタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)