---
title: "方法 : デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "データ ソース, バインド (Windows フォーム コントロールに)"
  - "DataGridView コントロール [Windows フォーム], データ バインド"
  - "Windows フォーム コントロール, バインド (データ ソースに)"
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 方法 : デザイナーを使用してデータを Windows フォーム DataGridView コントロールにバインドする
デザイナーを使用して、データベース、ビジネス オブジェクト、Web サービスなど、さまざまなデータ ソースに <xref:System.Windows.Forms.DataGridView> コントロールを関連付けることができます。  デザイナーを使用してデータ ソースにコントロールをバインドすると、コントロールは、データ ソースを表す <xref:System.Windows.Forms.BindingSource> コンポーネントに自動的にバインドされます。  また、データ ソースが提供するスキーマ情報に合わせて、コントロール内に列が自動的に生成されます。  
  
 生成された列は、必要に応じて変更できます。  たとえば、表示する必要がない列を削除したり、非表示にしたりできます。また、列を再配置したり列の種類を変更することもできます。  列の変更の詳細については、「参照」の各トピックを参照してください。  
  
 また、複数の <xref:System.Windows.Forms.DataGridView> コントロールを関連するテーブルにバインドし、マスター\/詳細リレーションシップを構築することもできます。  この構成の場合、あるコントロールは親テーブルを表示し、別のコントロールは親テーブルの現在の行に関連する子テーブルの行のみを表示します。  詳細については、「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)」を参照してください。  
  
 次の手順では、マスター\/詳細リレーションシップに関する 1 つまたは 2 つの <xref:System.Windows.Forms.DataGridView> コントロールが含まれているフォームを持つ、**Windows アプリケーション** プロジェクトが必要です。  このようなプロジェクトの起動については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」と「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールをデータ ソースにバインドするには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅のスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックします。  
  
2.  **\[データ ソースの選択\]** オプションのドロップダウン矢印をクリックします。  
  
3.  プロジェクトのデータ ソースがまだない場合は、**\[プロジェクト データ ソースの追加\]** をクリックし、ウィザードに示された手順に従います。  
  
     詳細については、「[データ ソース構成ウィザード](../Topic/Data%20Source%20Configuration%20Wizard.md)」を参照してください。  新しいデータ ソースが **\[データ ソースの選択\]** ボックスに表示されます。  新しいデータ ソースに 1 つのメンバー \(たとえば、1 つのデータベース テーブル\) だけが含まれる場合、コントロールはそのメンバーに自動的にバインドされます。  それ以外の場合は、次の手順に進みます。  
  
4.  **\[他のデータ ソース\]** ノードと **\[プロジェクト データ ソース\]** ノードが展開されていない場合は、展開します。次に、コントロールをバインドするデータ ソースを選択します。  
  
5.  データ ソースに複数のメンバーが含まれる場合 \(たとえば、複数のテーブルを含む <xref:System.Data.DataSet?displayProperty=fullName> を作成した場合\) は、データ ソースを展開し、バインド先となる特定のメンバーを選択します。  
  
6.  マスター\/詳細リレーションシップを構築するには、2 つ目の <xref:System.Windows.Forms.DataGridView> コントロールの **\[データ ソースの選択\]** ドロップダウン ウィンドウで、親テーブル用に作成された <xref:System.Windows.Forms.BindingSource> を展開し、表示されるリストから関連する子テーブルを選択します。  
  
    > [!NOTE]
    >  プロジェクトにデータ ソースが既に含まれている場合、**\[データ ソース\]** ウィンドウを使用してデータ フォームを作成することもできます。  詳細については、「[ウィンドウ](../Topic/Data%20Sources%20Window.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName>   
 [方法 : データベース内のデータに接続する](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [ウィンドウ](../Topic/Data%20Sources%20Window.md)   
 [方法: 関連するデータを Windows フォーム アプリケーションに表示する](../Topic/How%20to:%20Display%20Related%20Data%20in%20a%20Windows%20Forms%20Application.md)