---
title: "Windows フォームがサポートするデータ ソース | Microsoft Docs"
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
  - "配列 [Windows フォーム]"
  - "コレクション [Windows フォーム], バインド"
  - "データ [Windows フォーム], データ プロバイダー"
  - "データ プロバイダー [Windows フォーム]"
  - "データ ソース [Windows フォーム]"
  - "DataColumn クラス"
  - "DataSet クラス, バインディングと Windows フォーム"
  - "DataTable クラス, バインディングと Windows フォーム"
  - "DataView クラス, バインディングと Windows フォーム"
  - "DataViewManager クラス, バインディングと Windows フォーム"
  - "OLE DB プロバイダー, Windows フォーム"
  - "Windows フォーム, データ バインド"
  - "Windows フォーム, ソース データ"
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows フォームがサポートするデータ ソース
従来、データ バインディングは、データベースに格納されたデータをアプリケーション内で利用するために使用されてきました。  Windows フォームのデータ バインディングでは、データベースのデータだけでなく、配列やコレクションなど、一定の条件を満たす他の構造のデータにもアクセスできます。  
  
## バインドできる構造  
 Windows フォームでは、シンプル オブジェクトに対するバインド \(単純バインディング\) から、ADO.NET データ テーブルなどの複雑なリストに対するバインド \(複合バインディング\) まで、さまざまな構造にバインドできます。  単純バインディングでは、Windows フォームは、シンプル オブジェクトのパブリック プロパティに対するバインディングをサポートしています。  Windows フォームのリストベース バインディングでは、一般に、オブジェクトが <xref:System.Collections.IList> インターフェイスまたは <xref:System.ComponentModel.IListSource> インターフェイスをサポートしていることが必要です。  加えて、<xref:System.Windows.Forms.BindingSource> コンポーネントを通じてバインドする場合には、<xref:System.Collections.IEnumerable> インターフェイスをサポートするオブジェクトに対してバインドできます。  データ バインディングに関連するインターフェイスの詳細については、「[データ連結に関連するインターフェイス](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)」を参照してください。  
  
 次に示すのは、Windows フォームでバインドできる構造の一覧です。  
  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingSource> は、Windows フォームのデータ ソースとしては最も一般的で、データ ソースと Windows フォーム コントロールの間のプロキシの役割を果たします。  <xref:System.Windows.Forms.BindingSource> の使用パターンとしては、コントロールを <xref:System.Windows.Forms.BindingSource> にバインドし、<xref:System.Windows.Forms.BindingSource> をデータ ソース \(たとえば、ADO.NET データ テーブルやビジネス オブジェクト\) にバインドするという形が一般的です。  <xref:System.Windows.Forms.BindingSource> は、データ バインディングのサポートを実現し、そのレベルを向上させるサービスを備えています。  たとえば、Windows フォームのリストベースのコントロール \(<xref:System.Windows.Forms.DataGridView> や <xref:System.Windows.Forms.ComboBox> など\) は、<xref:System.Collections.IEnumerable> データ ソースへのバインディングを直接的にはサポートしていませんが、<xref:System.Windows.Forms.BindingSource> を通じてバインドすることにより、それが可能になります。  この場合、<xref:System.Windows.Forms.BindingSource> はデータ ソースを <xref:System.Collections.IList> に変換します。  
  
 シンプル オブジェクト  
 Windows フォームは、コントロールのプロパティをオブジェクト インスタンスのパブリック プロパティにバインドする、<xref:System.Windows.Forms.Binding> 型を使用したデータ バインディングをサポートします。  また、Windows フォームは、<xref:System.Windows.Forms.BindingSource> を使用したときには、リストベースのコントロール \(<xref:System.Windows.Forms.ListControl> など\) からオブジェクト インスタンスへのバインディングをサポートします。  
  
 配列またはコレクション  
 リストをデータ ソースとして使用するためには、<xref:System.Collections.IList> インターフェイスを実装する必要があります。その一例は、<xref:System.Array> クラスのインスタンスである配列です。  配列の詳細については、「[How to: Create an Array of Objects \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/6b64e069-0387-400c-9081-3bdc581020c3)」を参照してください。  
  
 一般に、データ バインディング用のオブジェクトのリストを作成するときは、<xref:System.ComponentModel.BindingList%601> を使用する必要があります。  <xref:System.ComponentModel.BindingList%601> は <xref:System.ComponentModel.IBindingList> インターフェイスのジェネリック バージョンです。  <xref:System.ComponentModel.IBindingList> インターフェイスは、<xref:System.Collections.IList> インターフェイスを拡張したもので、双方向のデータ バインディングに必要なプロパティ、メソッド、およびイベントが追加されています。  
  
 <xref:System.Collections.IEnumerable>  
 Windows フォーム コントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントを通じてバインドする場合には、<xref:System.Collections.IEnumerable> インターフェイスのみをサポートするデータ ソースにバインドできます。  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] データ オブジェクト  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] には、バインディングに適したデータ構造がいくつか用意されています。  各データ構造は、洗練の度合いと複雑さにおいてそれぞれ異なります。  
  
-   <xref:System.Data.DataColumn>.  1 つのテーブルは複数の列で構成されるという点で、<xref:System.Data.DataColumn> は <xref:System.Data.DataTable> の基本的なビルド ブロックです。  各 <xref:System.Data.DataColumn> オブジェクトには <xref:System.Data.DataColumn.DataType%2A> プロパティがあります。このプロパティは、列に保持されるデータの種類 \(自動車を表すテーブルの場合は自動車の型など\) を決定します。  データ テーブル内の列に、コントロール \(<xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティなど\) を単純バインドできます。  
  
-   <xref:System.Data.DataTable>.  <xref:System.Data.DataTable> は、行と列で構成される、[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] のテーブルの表現です。  データ テーブルは、<xref:System.Data.DataColumn> と <xref:System.Data.DataRow> という 2 つのコレクションを持ちます。前者は、当該のテーブルのデータの列を表し、そのテーブルに入力できるデータの種類は最終的にはこれにより決まります。後者は、当該のテーブルの行を表します。  データ テーブルに含まれる情報に対して、コントロールを複合バインドできます \(たとえば、<xref:System.Windows.Forms.DataGridView> コントロールからデータ テーブルに対するバインドなど\)。  ただし、<xref:System.Data.DataTable> にバインドすると、実際にはテーブルの既定のビューにバインドされます。  
  
-   <xref:System.Data.DataView>.  <xref:System.Data.DataView> は、1 つのデータ テーブルのカスタマイズされたビューであり、フィルター処理や並べ替えを行うことができます。  データ ビューは、複合連結コントロールで使用するデータの "スナップショット" です。  データ ビュー内のデータには単純バインドまたは複合バインドできますが、バインドしているのはクリーンな最新の状態のデータ ソースではなく、データの固定された "画像" であることに注意してください。  
  
-   <xref:System.Data.DataSet>.  <xref:System.Data.DataSet> は、データベース内のデータのテーブル、リレーションシップ、および制約のコレクションです。  データセット内のデータには単純バインドまたは複合バインドできますが、バインドしているのは <xref:System.Data.DataSet> の既定の <xref:System.Data.DataViewManager> \(次の項目を参照\) に対してであることに注意してください。  
  
-   <xref:System.Data.DataViewManager>.  <xref:System.Data.DataViewManager> は、<xref:System.Data.DataSet> 全体のカスタマイズされたビューです。<xref:System.Data.DataView> に似ていますが、リレーションシップが含まれています。  <xref:System.Data.DataViewManager.DataViewSettings%2A> コレクションを使用すると、指定したテーブルに対して <xref:System.Data.DataViewManager> に設定されているビューに、既定のフィルターや並べ替えオプションを設定できます。  
  
## 参照  
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)   
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)