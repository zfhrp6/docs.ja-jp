---
title: "Windows フォームがサポートするデータ ソース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d2c1c021759c7032257e95eb2cad202a461dc05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows フォームがサポートするデータ ソース
従来は、データ バインディングは、データベースに格納されたデータを活用するためにアプリケーション内で使用されています。 Windows フォーム データ バインディングを特定の最小要件を満たしている限り、データベースに他の構造体、配列など、コレクション内のデータからデータにアクセスすることができます。  
  
## <a name="structures-to-bind-to"></a>連結するには構造体  
 単純なから Windows フォームでさまざまな構造体をバインドできます ADO.NET データ テーブル (複合バインディング) などの複雑なリストをオブジェクト (単純バインディング)。 単純なバインディングは、Windows フォームは、単純なオブジェクトでのパブリック プロパティへのバインドをサポートします。 通常、リストベース バインディングの Windows フォームでは、オブジェクトをサポートしている必要がある、<xref:System.Collections.IList>インターフェイスまたは<xref:System.ComponentModel.IListSource>インターフェイスです。 さらに、経由でバインドする場合、<xref:System.Windows.Forms.BindingSource>コンポーネントをサポートするオブジェクトにバインドすることができます、<xref:System.Collections.IEnumerable>インターフェイスです。 データ バインディングに関連するインターフェイスの詳細については、次を参照してください。[データ バインディングに関連するインターフェイス](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)です。  
  
 Windows フォームにバインドすることができます、構造体を次に示します。  
  
 <xref:System.Windows.Forms.BindingSource>  
 A<xref:System.Windows.Forms.BindingSource>最も一般的な Windows フォームのデータ ソースは、データ ソースと Windows フォーム コントロール間のプロキシは機能します。 一般的な<xref:System.Windows.Forms.BindingSource>使用パターンが、コントロールにバインドするには、<xref:System.Windows.Forms.BindingSource>し、バインド、<xref:System.Windows.Forms.BindingSource>データ ソース (たとえば、ADO.NET データ テーブルまたはビジネス オブジェクト) にします。 <xref:System.Windows.Forms.BindingSource>を有効にして、データ バインディングのサポートのレベルを改善するサービスを提供します。 たとえば、Windows フォーム リストベース コントロールなど、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.ComboBox>へのバインドを直接サポートしていない<xref:System.Collections.IEnumerable>データ ソースをバインドすることによって、このシナリオを有効にするただし、<xref:System.Windows.Forms.BindingSource>です。 ここで、<xref:System.Windows.Forms.BindingSource>をデータ ソースを変換、<xref:System.Collections.IList>です。  
  
 単純なオブジェクト  
 Windows フォームを使用して、オブジェクトのインスタンスでのパブリック プロパティをデータ バインド コントロールのプロパティをサポートしている、<xref:System.Windows.Forms.Binding>型です。 Windows フォームもサポートしています、バインディングのベース リスト コントロールなど、<xref:System.Windows.Forms.ListControl>オブジェクトをインスタンス化時に、<xref:System.Windows.Forms.BindingSource>を使用します。  
  
 配列またはコレクション  
 データ ソースとして機能し、一覧を実装する必要があります、<xref:System.Collections.IList>インターフェイス以外の 1 つの例は配列としてのインスタンスでは、<xref:System.Array>クラスです。 配列の詳細については、次を参照してください。[する方法: 配列のオブジェクト (Visual Basic) を作成する](http://msdn.microsoft.com/en-us/6b64e069-0387-400c-9081-3bdc581020c3)です。  
  
 一般に、使用するように<xref:System.ComponentModel.BindingList%601>データ バインディング用のオブジェクトのリストを作成する場合。 <xref:System.ComponentModel.BindingList%601>ジェネリック バージョンは、<xref:System.ComponentModel.IBindingList>インターフェイスです。 <xref:System.ComponentModel.IBindingList>インターフェイスを拡張、<xref:System.Collections.IList>プロパティ、メソッド、および双方向データ バインディングに必要なイベントを追加することでインターフェイスです。  
  
 <xref:System.Collections.IEnumerable>  
 Windows フォーム コントロールをのみをサポートするデータ ソースにバインドすることができます、<xref:System.Collections.IEnumerable>インターフェイスを通じてバインドされている場合、<xref:System.Windows.Forms.BindingSource>コンポーネントです。  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]データ オブジェクト  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)]バインドするために適切なデータ構造体の数を提供します。 各は、知識と複雑さによって異なります。  
  
-   <xref:System.Data.DataColumn>。 A<xref:System.Data.DataColumn>の不可欠なビルド ブロックには、<xref:System.Data.DataTable>列の数が、テーブルを構成することで、します。 各<xref:System.Data.DataColumn>が、<xref:System.Data.DataColumn.DataType%2A>データ列を保持します (たとえば、自動車車を記述する、テーブル内の作成) の種類を決定するプロパティです。 コントロールを単純なバインドこともできます (など、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.Control.Text%2A>プロパティ) データ テーブル内の列にします。  
  
-   <xref:System.Data.DataTable>。 A<xref:System.Data.DataTable>行と列を含む、テーブルの表現が、[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]です。 データ テーブルには、2 つのコレクションが含まれています: <xref:System.Data.DataColumn>、(最終的にそのテーブルに入力できるデータの種類が決まります) を特定のテーブル内のデータの列を表すと<xref:System.Data.DataRow>、特定のテーブル内のデータの行を表すです。 できる複合型をバインドするコントロールをデータ テーブルに含まれる情報 (バインディングなど、<xref:System.Windows.Forms.DataGridView>コントロールをデータ テーブルに)。 バインドすると、ただし、<xref:System.Data.DataTable>テーブルの既定のビューに本当にバインドします。  
  
-   <xref:System.Data.DataView>。 A<xref:System.Data.DataView>フィルター処理または並べ替えが 1 つのデータ テーブルのカスタマイズされたビューです。 データ ビューは、データの複雑なバインドされたコントロールによって使用される「スナップショット」です。 できます単純バインドまたはデータ ビュー内のデータへの複雑なバインドがクリーンで更新のデータ ソースではなく、データの固定された「画像」にバインドすることに注意してください。  
  
-   <xref:System.Data.DataSet>。 A<xref:System.Data.DataSet>テーブル、リレーションシップ、およびデータベース内のデータの制約のコレクションです。 できます単純バインドまたはデータセット内のデータへの複雑なバインドが、既定値にバインドすることに注意してください<xref:System.Data.DataViewManager>の<xref:System.Data.DataSet>(ポイント、次の項目を参照してください)。  
  
-   <xref:System.Data.DataViewManager>。 A<xref:System.Data.DataViewManager>全体のカスタマイズされたビューは、<xref:System.Data.DataSet>に似ています、<xref:System.Data.DataView>が含まれている関係を使用します。 <xref:System.Data.DataViewManager.DataViewSettings%2A>コレクション、および設定できます既定のフィルターされたビューの並べ替えオプションを<xref:System.Data.DataViewManager>が指定したテーブル。  
  
## <a name="see-also"></a>参照  
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)
