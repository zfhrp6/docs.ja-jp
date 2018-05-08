---
title: BindingSource コンポーネント アーキテクチャ
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: b0334bd7a0bc5ff46c43fd7ee549422d98c35efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="bindingsource-component-architecture"></a>BindingSource コンポーネント アーキテクチャ
<xref:System.Windows.Forms.BindingSource>コンポーネントは、ユニバーサル データ ソースにすべての Windows フォーム コントロールをバインドすることができます。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントがデータ ソースにコントロールをバインドするプロセスを簡略化し、従来のデータ バインディングを使用した次の利点があります。  
  
-   ビジネス オブジェクトをデザイン時のバインドを有効にします。  
  
-   カプセル化<xref:System.Windows.Forms.CurrencyManager>機能を公開<xref:System.Windows.Forms.CurrencyManager>デザイン時のイベントです。  
  
-   サポートするリストの作成を簡略化、 <xref:System.ComponentModel.IBindingList>  ボックスの一覧をネイティブにサポートしないデータ ソースの変更通知の一覧変更通知を提供することでインターフェイスです。  
  
-   拡張ポイントを提供、<xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType>メソッドです。  
  
-   データ ソースと、コントロール間を間接化レベルを提供します。 この間接指定が実行時に、データ ソースを変更することがあるときに重要です。  
  
-   具体的には、その他のデータに関連する Windows フォーム コントロールと相互運用、<xref:System.Windows.Forms.BindingNavigator>と<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 これらの理由から、<xref:System.Windows.Forms.BindingSource>コンポーネントは、Windows フォーム コントロールをデータ ソースにバインドすることをお勧めします。  
  
## <a name="bindingsource-features"></a>BindingSource 機能  
 <xref:System.Windows.Forms.BindingSource>コンポーネントは、データへのコントロールのバインドのいくつかの機能を提供します。 これらの機能には、コーディングをほとんど行わず、ユーザー側でのほとんどのデータ バインディング シナリオを実装できます。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントでこれを行うさまざまな種類のデータ ソースにアクセスするための一貫したインターフェイスを提供することによりします。 これは、任意の型にバインドするため、同じ手順を使用することを意味します。 たとえば、アタッチすること、<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティを<xref:System.Data.DataSet>またはビジネス オブジェクトに、どちらの場合も同じプロパティ、メソッド、およびイベントのセットを使用して、データ ソースを操作します。  
  
 によって提供される一貫性のあるインターフェイス、<xref:System.Windows.Forms.BindingSource>コンポーネントは、コントロールにデータをバインドするプロセスを大幅に簡略化します。 変更の通知を提供するデータ ソースの種類に対して、<xref:System.Windows.Forms.BindingSource>コントロールとデータ ソース間で変更を自動的に通信するコンポーネントです。 変更通知を提供しないデータ ソースの種類のイベントが変更通知を生成するための提供されます。 次の一覧でサポートされる機能を示しています、<xref:System.Windows.Forms.BindingSource>コンポーネント。  
  
-   間接参照します。  
  
-   通貨管理します。  
  
-   一覧としてデータ ソースです。  
  
-   <xref:System.Windows.Forms.BindingSource> として、<xref:System.ComponentModel.IBindingList>です。  
  
-   カスタム アイテムを作成します。  
  
-   トランザクションのアイテムを作成します。  
  
-   <xref:System.Collections.IEnumerable> サポートしてください。  
  
-   デザイン時のサポート。  
  
-   静的<xref:System.Windows.Forms.ListBindingHelper>メソッドです。  
  
-   並べ替えとフィルター処理を<xref:System.ComponentModel.IBindingListView>インターフェイスです。  
  
-   統合<xref:System.Windows.Forms.BindingNavigator>です。  
  
### <a name="indirection"></a>間接参照  
 <xref:System.Windows.Forms.BindingSource>コンポーネントは、コントロールとデータ ソース間を間接化レベルを提供します。 コントロールをバインドするデータ ソースに直接コントロールをバインディングではなく、 <xref:System.Windows.Forms.BindingSource>、接続して、データ ソース、<xref:System.Windows.Forms.BindingSource>コンポーネントの<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティです。  
  
 このレベルの間接参照するには、使用は、コントロールのバインディングをリセットせず、データ ソースを変更できます。 これにより、次の機能。  
  
-   アタッチすることができます、<xref:System.Windows.Forms.BindingSource>さまざまなデータ ソース コントロールの現在のバインドを維持したままにします。  
  
-   データ ソース内の項目を変更し、バインドされたコントロールに通知できます。 詳細については、次を参照してください。[する方法: データ ソースの更新の BindingSource で Windows フォーム コントロールに反映](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)です。  
  
-   バインドすることができます、<xref:System.Type>メモリ内のオブジェクトの代わりにします。 詳細については、次を参照してください。[する方法: Windows フォーム コントロールを型にバインド](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)です。 実行時に、オブジェクトにし、バインドできます。  
  
### <a name="currency-management"></a>通貨の管理  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.Windows.Forms.ICurrencyManagerProvider>を処理するため、通貨管理するインターフェイスです。 <xref:System.Windows.Forms.ICurrencyManagerProvider>インターフェイス、アクセスすることも currencymanager をする、 <xref:System.Windows.Forms.BindingSource>、別のカレンシー マネージャーだけでなく<xref:System.Windows.Forms.BindingSource>に同じバインド<xref:System.Windows.Forms.BindingSource.DataMember%2A>です。  
  
 <xref:System.Windows.Forms.BindingSource>コンポーネントをカプセル化<xref:System.Windows.Forms.CurrencyManager>機能と、最も一般的な公開<xref:System.Windows.Forms.CurrencyManager>プロパティとイベント。 次の表では、通貨管理に関連するメンバーの一部について説明します。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> プロパティ  
 関連付けられた currencymanager を取得、<xref:System.Windows.Forms.BindingSource>です。  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> メソッド  
 間を使用する必要がある場合<xref:System.Windows.Forms.BindingSource>指定されたデータ メンバーにバインドされている、その currencymanager を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> プロパティ  
 データソースの現在の項目を取得します。  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> プロパティ  
 基になるリストでの現在の位置を取得または設定します。  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> メソッド  
 基になるデータ ソースに保留中の変更を適用します。  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> メソッド  
 現在の編集操作をキャンセルします。  
  
### <a name="data-source-as-a-list"></a>一覧としてデータ ソース  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.ComponentModel.IBindingListView>と<xref:System.ComponentModel.ITypedList>インターフェイスです。 この実装で使用することができます、<xref:System.Windows.Forms.BindingSource>コンポーネント自体をデータ ソースとして、外部の記憶域がないです。  
  
 ときに、<xref:System.Windows.Forms.BindingSource>コンポーネントがデータ ソースに接続されている、一覧としてデータ ソースを公開します。  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティは、いくつかのデータ ソースに設定することができます。 型、オブジェクト、および種類のリストが含まれます。 結果のデータ ソースは、リストとして公開されます。 次の表は、一般的なデータ ソースと結果のリストの評価の一部を示します。  
  
|データ ソースのプロパティ|結果のリスト|  
|-------------------------|------------------|  
|null 参照 (Visual Basic の場合は `Nothing`)。|空<xref:System.ComponentModel.IBindingList>オブジェクト。 追加された項目の種類を一覧を設定する、項目の追加します。|  
|Null 参照 (`Nothing` Visual Basic で) と<xref:System.Windows.Forms.BindingSource.DataMember%2A>設定|サポートされていません。発生させます<xref:System.ArgumentException>です。|  
|リスト以外の型のオブジェクトまたはオブジェクト型"T"|空<xref:System.ComponentModel.IBindingList>型"T"です。|  
|配列のインスタンス|<xref:System.ComponentModel.IBindingList>の配列要素を格納します。|  
|<xref:System.Collections.IEnumerable> インスタンス|<xref:System.ComponentModel.IBindingList>を含む、<xref:System.Collections.IEnumerable>項目|  
|"T"の種類を含むインスタンスを一覧表示します。|<xref:System.ComponentModel.IBindingList>型"T"を含むインスタンス。|  
  
 さらに、<xref:System.Windows.Forms.BindingSource.DataSource%2A>などの他の種類を一覧表示、設定できる<xref:System.ComponentModel.IListSource>と<xref:System.ComponentModel.ITypedList>、および<xref:System.Windows.Forms.BindingSource>適切に処理されます。 この場合、一覧に含まれている型には、既定のコンス トラクターが必要です。  
  
### <a name="bindingsource-as-an-ibindinglist"></a>IBindingList としての BindingSource  
 <xref:System.Windows.Forms.BindingSource>コンポーネントへのアクセスととしての基になるデータを操作するメンバーを提供する、<xref:System.ComponentModel.IBindingList>です。 次の表では、これらのメンバーの一部について説明します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> プロパティ|評価の結果の一覧を取得、<xref:System.Windows.Forms.BindingSource.DataSource%2A>または<xref:System.Windows.Forms.BindingSource.DataMember%2A>プロパティです。|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> メソッド|基になるリストに新しい項目を追加します。 実装するデータ ソースに適用されます、<xref:System.ComponentModel.IBindingList>インターフェイスし、項目の追加を許可する (つまり、<xref:System.Windows.Forms.BindingSource.AllowNew%2A>プロパティに設定されている`true`)。|  
  
### <a name="custom-item-creation"></a>カスタム アイテムの作成  
 処理することができます、<xref:System.Windows.Forms.BindingSource.AddingNew>独自項目作成ロジックを提供するイベントです。 <xref:System.Windows.Forms.BindingSource.AddingNew>に新しいオブジェクトを追加する前に、イベントが発生した、<xref:System.Windows.Forms.BindingSource>です。 後にこのイベントは、<xref:System.Windows.Forms.BindingSource.AddNew%2A>メソッドが呼び出されると、新しい項目が基になるリストに追加する前にします。 このイベントを処理してから派生することがなくカスタムの項目の作成の動作を指定できます、<xref:System.Windows.Forms.BindingSource>クラスです。 詳細については、次を参照してください。[する方法: Windows フォーム BindingSource で項目の追加をカスタマイズ](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)です。  
  
### <a name="transactional-item-creation"></a>トランザクションのアイテムの作成  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.ComponentModel.ICancelAddNew>インターフェイスで、トランザクションの項目を作成できるようにします。 呼び出しを使用して、新しい項目が作成された仮後<xref:System.Windows.Forms.BindingSource.AddNew%2A>追加のコミットまたは次の方法でロールバック可能性があります。  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A>メソッドは保留中の追加を明示的にコミットします。  
  
-   挿入、削除、または、移動など、別のコレクションの操作を実行すると、保留中の追加は暗黙的にコミットします。  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>メソッドは元に戻す保留中の追加メソッドが既にコミットされていない場合。  
  
### <a name="ienumerable-support"></a>IEnumerable のサポート  
 <xref:System.Windows.Forms.BindingSource>コンポーネントにより、コントロールへのバインド<xref:System.Collections.IEnumerable>データ ソース。 このコンポーネントにすることができます、データ ソースにバインドなど、<xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>です。  
  
 ときに、<xref:System.Collections.IEnumerable>に割り当てられているデータ ソース、 <xref:System.Windows.Forms.BindingSource> 、コンポーネント、<xref:System.Windows.Forms.BindingSource>を作成、<xref:System.ComponentModel.IBindingList>の内容を追加し、<xref:System.Collections.IEnumerable>データ ソースの一覧にします。  
  
### <a name="design-time-support"></a>デザイン時サポート  
 オブジェクトの種類によっては、ファクトリ クラスから作成されたオブジェクトや Web サービスによって返されるオブジェクトなど、デザイン時に作成できません。 コントロールをバインドできるメモリ内にオブジェクトが存在しない場合でも、デザイン時にこれらの型に、コントロールにバインドする必要がある場合があります。 列ヘッダーのラベル付けする必要があります、たとえば、<xref:System.Windows.Forms.DataGridView>カスタム型のパブリック プロパティの名前を制御します。  
  
 このシナリオをサポートするために、<xref:System.Windows.Forms.BindingSource>コンポーネントへのバインドをサポートしている、<xref:System.Type>です。 割り当てると、<xref:System.Type>を<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティ、<xref:System.Windows.Forms.BindingSource>コンポーネントは、空、作成<xref:System.ComponentModel.BindingList%601>の<xref:System.Type>項目。 任意のコントロールにバインドする、その後、<xref:System.Windows.Forms.BindingSource>コンポーネントは警告を表示するプロパティまたは型のスキーマが存在する、デザイン時または実行時にします。 詳細については、次を参照してください。[する方法: Windows フォーム コントロールを型にバインド](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)です。  
  
### <a name="static-listbindinghelper-methods"></a>静的 ListBindingHelper メソッド  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>、 <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>、および<xref:System.Windows.Forms.BindingSource>から一覧を生成する、すべての共有の共通のロジックの種類、 `DataSource` / `DataMember`ペア。 さらに、この一般的なロジックがパブリックに公開用にコントロールを作成し、次にその他のサード パーティによって`static`メソッド。  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>。  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>並べ替えと IBindingListView インターフェイスとフィルター処理  
 <xref:System.Windows.Forms.BindingSource>コンポーネントを実装して、<xref:System.ComponentModel.IBindingListView>を拡張するインターフェイス、<xref:System.ComponentModel.IBindingList>インターフェイスです。 <xref:System.ComponentModel.IBindingList>単一列の並べ替えを提供し、<xref:System.ComponentModel.IBindingListView>先進的な並べ替えとフィルター処理を提供します。 <xref:System.ComponentModel.IBindingListView>並べ替えることができます、および場合は、データ ソースも、データ ソース内のアイテムのフィルターには、これらのインターフェイスのいずれかを実装します。 <xref:System.Windows.Forms.BindingSource>コンポーネントがこれらのメンバーの参照の実装を提供していません。 代わりに、呼び出しは、基になるリストに転送されます。  
  
 次の表では、並べ替えとフィルター処理に使用するプロパティについて説明します。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingListView> である場合は、表示する行のフィルター処理に使用する式を取得または設定します。|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> プロパティ|データ ソースが <xref:System.ComponentModel.IBindingList> である場合は、並べ替えに使用する列名と並べ替え順序情報を取得または設定します。<br /><br /> - または -<br /><br /> データ ソースがある場合、<xref:System.ComponentModel.IBindingListView>を並べ替え、高度なサポートの並べ替えと並べ替え順序に使用する複数の列名を取得します|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator との統合  
 使用することができます、<xref:System.Windows.Forms.BindingSource>データ ソースへの Windows フォーム コントロールをバインドするコンポーネントですが、<xref:System.Windows.Forms.BindingNavigator>コントロールは操作専用に設計されています、<xref:System.Windows.Forms.BindingSource>コンポーネントです。 <xref:System.Windows.Forms.BindingNavigator>コントロールを制御するためのユーザー インターフェイスを提供する、<xref:System.Windows.Forms.BindingSource>コンポーネントの現在の項目。 既定では、<xref:System.Windows.Forms.BindingNavigator>コントロールには、ナビゲーション メソッドに対応するボタンが用意されています、<xref:System.Windows.Forms.BindingSource>コンポーネントです。 詳細については、次を参照してください。[する方法: Windows フォーム BindingNavigator コントロールにデータを移動](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingSource コンポーネントの概要](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [BindingNavigator コントロール](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Windows フォームでのデータ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [方法: Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [方法: BindingSource を使用して Windows フォーム コントロール内にデータ ソースの更新を反映させる](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
