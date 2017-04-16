---
title: "BindingSource コンポーネント アーキテクチャ | Microsoft Docs"
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
  - "BindingSource コンポーネント [Windows フォーム], BindingSource コンポーネントの概要"
  - "BindingSource コンポーネント, アーキテクチャ"
  - "データ バインド, BindingSource コンポーネント"
  - "Windows フォーム, データ バインド"
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# BindingSource コンポーネント アーキテクチャ
<xref:System.Windows.Forms.BindingSource> コンポーネントを使用すると、すべての Windows フォーム コントロールをデータ ソースへバインドできます。  
  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、コントロールをデータ ソースにバインドするプロセスを簡略化し、従来のデータ バインディングにはなかったいくつかの利点を提供します。  
  
-   ビジネス オブジェクトへのデザイン時のバインディングが可能です。  
  
-   <xref:System.Windows.Forms.CurrencyManager> 機能をカプセル化し、デザイン時に <xref:System.Windows.Forms.CurrencyManager> イベントを公開します。  
  
-   リストの変更通知機能をネイティブでサポートしないデータ ソースにリストの変更通知機能を提供することによって、<xref:System.ComponentModel.IBindingList> インターフェイスをサポートするリストの作成を簡略化します。  
  
-   <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=fullName> メソッドに機能拡張ポイントを提供します。  
  
-   データ ソースとコントロールの間に間接操作のレベルを提供します。  この間接操作は、実行時にデータ ソースが変化する可能性がある場合に重要です。  
  
-   他のデータ関連の Windows フォーム コントロール \(特に <xref:System.Windows.Forms.BindingNavigator> コントロールと <xref:System.Windows.Forms.DataGridView> コントロール\) と相互運用します。  
  
 これらの理由により、Windows フォーム コントロールをデータ ソースにバインドする方法として、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用することをお勧めします。  
  
## BindingSource の機能  
 <xref:System.Windows.Forms.BindingSource> コンポーネントには、コントロールをデータにバインドするための機能がいくつか用意されています。  これらの機能により、コーディングをほとんど行わずに、大部分のデータ バインディング シナリオを実装できます。  
  
 これを実現するため、<xref:System.Windows.Forms.BindingSource> コンポーネントはさまざまな種類のデータ ソースにアクセスするための一貫性のあるインターフェイスを提供します。  つまり、同じ手順を使用してすべての型にバインドできるということです。  たとえば、<xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティを <xref:System.Data.DataSet> にもビジネス オブジェクトにも追加できます。どちらの場合も、同じプロパティ、メソッド、およびイベントのセットを使用してデータ ソースを操作できます。  
  
 <xref:System.Windows.Forms.BindingSource> コンポーネントが提供する一貫性のあるインターフェイスにより、データをコントロールにバインドするプロセスが大幅に簡略化されます。  変更通知を行うデータ ソースの場合、<xref:System.Windows.Forms.BindingSource> コンポーネントによってコントロールとデータ ソース間で変更が自動的に伝達されます。  変更通知を行うデータ ソースの場合は、変更通知を発生させるためのイベントが提供されます。  <xref:System.Windows.Forms.BindingSource> コンポーネントがサポートする機能を次に示します。  
  
-   間接  
  
-   伝達性管理  
  
-   リストとしてのデータ ソース  
  
-   <xref:System.ComponentModel.IBindingList> としての <xref:System.Windows.Forms.BindingSource>  
  
-   カスタム項目の作成  
  
-   トランザクション項目の作成  
  
-   <xref:System.Collections.IEnumerable> のサポート  
  
-   デザイン時サポート  
  
-   静的な <xref:System.Windows.Forms.ListBindingHelper> メソッド  
  
-   <xref:System.ComponentModel.IBindingListView> インターフェイスを使用した並べ替えとフィルター処理  
  
-   <xref:System.Windows.Forms.BindingNavigator> との統合  
  
### 間接  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、コントロールとデータ ソース間に間接操作のレベルを提供します。  コントロールをデータ ソースに直接バインドする代わりに、コントロールを <xref:System.Windows.Forms.BindingSource> にバインドし、<xref:System.Windows.Forms.BindingSource> コンポーネントの <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティにデータ ソースを追加します。  
  
 この間接操作のレベルを使用すると、コントロールのバインディングをリセットせずにデータ ソースを変更できます。  これによって、次の作業を行うことができます。  
  
-   現在のコントロール バインディングを維持したまま、異なるデータ ソースに <xref:System.Windows.Forms.BindingSource> を追加できます。  
  
-   データ ソース内の項目を変更し、バインド コントロールに通知できます。  詳細については、「[方法 : BindingSource を使用して Windows フォーム コントロール内にデータ ソースの更新を反映させる](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)」を参照してください。  
  
-   メモリ内のオブジェクトではなく、<xref:System.Type> にバインドできます。  詳細については、「[方法 : Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)」を参照してください。  その後、実行時にオブジェクトにバインドできます。  
  
### 伝達性管理  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、<xref:System.Windows.Forms.ICurrencyManagerProvider> インターフェイスを実装し、通過管理を処理します。  また、<xref:System.Windows.Forms.ICurrencyManagerProvider> インターフェイスにより、<xref:System.Windows.Forms.BindingSource> の CurrencyManager だけでなく、同じ <xref:System.Windows.Forms.BindingSource.DataMember%2A> にバインドされた他の <xref:System.Windows.Forms.BindingSource> の CurrencyManager にもアクセスできます。  
  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは <xref:System.Windows.Forms.CurrencyManager> 機能をカプセル化し、最も一般的な <xref:System.Windows.Forms.CurrencyManager> プロパティとイベントを公開します。  伝達性管理に関連するメンバーのいくつかを次の表に示します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> プロパティ  
 <xref:System.Windows.Forms.BindingSource> に関連付けられている CurrencyManager を取得します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> メソッド  
 別の <xref:System.Windows.Forms.BindingSource> が、指定したデータ メンバーにバインドされている場合、その CurrencyManager を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> プロパティ  
 データ ソースの現在の項目を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティ  
 基になるリストでの現在の位置を取得または設定します。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> メソッド  
 基になるデータ ソースに保留中の変更を適用します。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> メソッド  
 現在の編集操作をキャンセルします。  
  
### リストとしてのデータ ソース  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、<xref:System.ComponentModel.IBindingListView> インターフェイスと <xref:System.ComponentModel.ITypedList> インターフェイスを実装します。  この実装により、外部のストレージを使用せず、<xref:System.Windows.Forms.BindingSource> コンポーネント自体をデータ ソースとして使用できます。  
  
 <xref:System.Windows.Forms.BindingSource> コンポーネントをデータ ソースに追加すると、データ ソースはリストとして公開されます。  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティには、複数のデータ ソースを設定できます。  たとえば、型、オブジェクト、型のリストなどです。  その結果、データ ソースがリストとして公開されます。  一般的なデータ ソースおよび結果としてのリストの評価を次の表に示します。  
  
|DataSource プロパティ|結果のリスト|  
|----------------------|------------|  
|null 参照 \(Visual Basic では `Nothing`\)|オブジェクトの空の <xref:System.ComponentModel.IBindingList>。  項目を追加すると、リストは追加した項目の型に設定されます。|  
|<xref:System.Windows.Forms.BindingSource.DataMember%2A> を設定した null 参照 \(Visual Basic では `Nothing`\)|サポートされていません。<xref:System.ArgumentException> が発生します。|  
|非リスト型、または "T" 型のオブジェクト|"T" 型の空の <xref:System.ComponentModel.IBindingList>。|  
|配列インスタンス|配列要素を含む <xref:System.ComponentModel.IBindingList>。|  
|<xref:System.Collections.IEnumerable> インスタンス|<xref:System.Collections.IEnumerable> 項目を含む <xref:System.ComponentModel.IBindingList>。|  
|"T" 型を含むリスト インスタンス|"T" 型を含む <xref:System.ComponentModel.IBindingList> インスタンス。|  
  
 また、<xref:System.Windows.Forms.BindingSource.DataSource%2A> は <xref:System.ComponentModel.IListSource> や <xref:System.ComponentModel.ITypedList> などの他のリスト型に設定でき、それらは <xref:System.Windows.Forms.BindingSource> によって適切に処理されます。  この場合、リストに含まれる型は既定のコンストラクターを持ちます。  
  
### IBindingList としての BindingSource  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、基になるデータにアクセスし、操作するためのメンバーを <xref:System.ComponentModel.IBindingList> として提供します。  これらのメンバーのいくつかを次の表に示します。  
  
|メンバー|Description|  
|----------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> プロパティ|<xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティまたは <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティの評価から生成されるリストを取得します。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> メソッド|基になるリストに新しい項目を追加します。  <xref:System.ComponentModel.IBindingList> インターフェイスを実装し、項目の追加を有効にする \(つまり、<xref:System.Windows.Forms.BindingSource.AllowNew%2A> プロパティが `true` に設定されている\) データ ソースに適用されます。|  
  
### カスタム項目の作成  
 <xref:System.Windows.Forms.BindingSource.AddingNew> イベントを処理して独自の項目作成ロジックを提供できます。  <xref:System.Windows.Forms.BindingSource.AddingNew> イベントは、新しいオブジェクトが <xref:System.Windows.Forms.BindingSource> に追加される前に発生します。  このイベントは、<xref:System.Windows.Forms.BindingSource.AddNew%2A> メソッドが呼び出された後、基になるリストに新しい項目が追加される前に発生します。  このイベントを処理することにより、<xref:System.Windows.Forms.BindingSource> クラスからクラスを派生せずにカスタム項目の作成動作を提供できます。  詳細については、「[方法 : Windows フォーム BindingSource を使用した項目の追加をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)」を参照してください。  
  
### トランザクション項目の作成  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、トランザクション項目が作成できるようにする <xref:System.ComponentModel.ICancelAddNew> インターフェイスを実装します。  <xref:System.Windows.Forms.BindingSource.AddNew%2A> を呼び出して新しい項目を仮に作成した後、次の方法で追加をコミットまたはロールバックできます。  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> メソッドを使用して、保留中の追加を明示的にコミットします。  
  
-   挿入、削除、移動など、他のコレクション操作を実行すると、保留中の追加を暗黙的にコミットします。  
  
-   まだメソッドをコミットしていない場合に、<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> メソッドを使用して保留中の追加をロールバックします。  
  
### IEnumerable のサポート  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは、<xref:System.Collections.IEnumerable> データ ソースへのコントロールのバインドを有効にします。  このコンポーネントを使用すると、<xref:System.Data.SqlClient.SqlDataReader?displayProperty=fullName> のようなデータ ソースにバインドできます。  
  
 <xref:System.Collections.IEnumerable> データ ソースが <xref:System.Windows.Forms.BindingSource> コンポーネントに割り当てられている場合、<xref:System.Windows.Forms.BindingSource> は <xref:System.ComponentModel.IBindingList> を作成し、そのリストに <xref:System.Collections.IEnumerable> データ ソースの内容を追加します。  
  
### デザイン時サポート  
 一部のオブジェクト型 \(たとえば、ファクトリ クラスで作成されたオブジェクトや Web サービスから返されたオブジェクトなど\) はデザイン時に作成できません。  コントロールをバインドできるオブジェクトがメモリに存在しない場合でも、デザイン時に、コントロールをこれらの型にバインドする必要が生じることがあります。  たとえば、<xref:System.Windows.Forms.DataGridView> コントロールの列ヘッダーにカスタム型のパブリック プロパティの名前のラベルを付けることが必要な場合もあります。  
  
 このようなシナリオをサポートするため、<xref:System.Windows.Forms.BindingSource> コンポーネントは <xref:System.Type> へのバインドをサポートしています。  <xref:System.Type> を <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティに割り当てる場合、<xref:System.Windows.Forms.BindingSource> コンポーネントは <xref:System.Type> 項目の空の <xref:System.ComponentModel.BindingList%601> を作成します。  それ以降、<xref:System.Windows.Forms.BindingSource> コンポーネントにコントロールをバインドしようとすると、使用する型のプロパティまたはスキーマが既に存在することがデザイン時または実行時に警告されます。  詳細については、「[方法 : Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)」を参照してください。  
  
### 静的な ListBindingHelper メソッド  
 <xref:System.Windows.Forms.BindingContext?displayProperty=fullName> 型、<xref:System.Windows.Forms.CurrencyManager?displayProperty=fullName> 型、および <xref:System.Windows.Forms.BindingSource> 型は、すべて共通のロジックを使用して `DataSource`\/`DataMember` のペアからリストを生成します。  また、この共通のロジックは、コントロールの作成者およびその他のサードパーティが使用できるように、次の `static` メソッド内で一般に公開されます。  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### IBindingListView インターフェイスを使用した並べ替えとフィルター処理  
 <xref:System.Windows.Forms.BindingSource> コンポーネントは <xref:System.ComponentModel.IBindingListView> インターフェイスを実装します。このインターフェイスは、<xref:System.ComponentModel.IBindingList> インターフェイスを拡張します。  <xref:System.ComponentModel.IBindingList> には単一の列を並べ替える機能があり、<xref:System.ComponentModel.IBindingListView> には高度なソート機能とフィルタリング機能があります。  データ ソースでこれらのインターフェイスのいずれかを実装している場合、<xref:System.ComponentModel.IBindingListView> を使用すると、データ ソースの項目を並べ替えたり、フィルター処理を行うことができます。  <xref:System.Windows.Forms.BindingSource> コンポーネントは、これらのメンバーの参照実装を提供しません。  代わりに、基になるリストに呼び出しが転送されます。  
  
 並べ替えとフィルター処理に使用するプロパティを次の表に示します。  
  
|メンバー|Description|  
|----------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingListView> である場合は、表示する行のフィルター処理に使用する式を取得または設定します。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingList> である場合は、並べ替えに使用する列名と並べ替え順序情報を取得または設定します。<br /><br /> または<br /><br /> データ ソースが <xref:System.ComponentModel.IBindingListView> であり、高度な並べ替えをサポートしている場合は、並べ替えに使用する複数の列名と並べ替え順序情報を取得します。|  
  
### BindingNavigator との統合  
 <xref:System.Windows.Forms.BindingSource> コンポーネントを使用して任意の Windows フォーム コントロールをデータ ソースにバインドすることもできます。ただし、<xref:System.Windows.Forms.BindingNavigator> コントロールは具体的には <xref:System.Windows.Forms.BindingSource> コンポーネントと共に使用するように設計されています。  <xref:System.Windows.Forms.BindingNavigator> コントロールは、<xref:System.Windows.Forms.BindingSource> コンポーネントの現在の項目を制御するためのユーザー インターフェイスを提供します。  既定では、<xref:System.Windows.Forms.BindingNavigator> コントロールには、<xref:System.Windows.Forms.BindingSource> コンポーネントのナビゲーション メソッドに対応するボタンが用意されています。  詳細については、「[方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.BindingNavigator>   
 [BindingSource コンポーネントの概要](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)   
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [Windows フォームでのデータ バインド](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [方法 : Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)   
 [方法 : BindingSource を使用して Windows フォーム コントロール内にデータ ソースの更新を反映させる](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)