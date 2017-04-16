---
title: "方法 : Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする | Microsoft Docs"
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
  - "データ グリッド, カスタマイズ (並べ替えを)"
  - "DataGridView コントロール [Windows フォーム], 並べ替え"
  - "並べ替え, DataGridView コントロール"
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする
<xref:System.Windows.Forms.DataGridView> コントロールは、自動並べ替え機能を提供しますが、ニーズに応じて、並べ替え操作をカスタマイズすることが必要な場合があります。  たとえば、プログラムによる並べ替え機能を使用して、代替のユーザー インターフェイス \(UI\) を作成することができます。  また、複数の列の並べ替えなど、並べ替え柔軟性を高めるために、<xref:System.Windows.Forms.DataGridView.SortCompare> イベントを処理したり、<xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(IComparer)` のオーバーロードを呼び出したりすることができます。  
  
 次のコード例は、カスタムの並べ替えの 3 つの方法を示します。  詳細については、「[Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## プログラムによる並べ替え  
 次のコード例は、<xref:System.Windows.Forms.DataGridView.SortOrder%2A> プロパティと <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> プロパティを使用して並べ替えの方向を判断し、<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> プロパティを使用してナラベカエグリフを手動で設定する、プログラムによる並べ替えを示しています。  <xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(DataGridViewColumn,ListSortDirection)` のオーバーロードは 1 つの列のみでのデータの並べ替えに使用します。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## SortCompare イベントを使用したカスタムの並べ替え  
 次のコード例は、<xref:System.Windows.Forms.DataGridView.SortCompare> イベント ハンドラーを使用したカスタムの並べ替えを示しています。  選択した <xref:System.Windows.Forms.DataGridViewColumn> が並べ替えられて、列に重複する値がある場合は、最終的な順序を決定する、ID 列が使用されます。  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## IComparer インターフェイスを使用したカスタムの並べ替え  
 次のコード例は、複数列の並べ替えを実行する <xref:System.Collections.IComparer> インターフェイスの実装を取得する <xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(IComparer)` のオーバーロードを使用したカスタムの並べ替えを示しています。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## コードのコンパイル  
 これらの例には次の項目が必要です。  
  
-   System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこれらの例をビルドする方法の詳細については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows フォームの DataGridView コントロールでのデータの並べ替え](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)