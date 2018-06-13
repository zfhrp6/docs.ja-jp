---
title: データ連結に関連するインターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: 6c4470b33977408fa4429d187dafd76241d0d9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541847"
---
# <a name="interfaces-related-to-data-binding"></a>データ連結に関連するインターフェイス
[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] では、アプリケーションのバインドのニーズや使用するデータに合わせてさまざまなデータ構造を作成できます。 Windows フォームでデータを提供または使用するための独自のクラスを作成することもできます。 これらのオブジェクトは、基本的なデータ バインディングから、デザイン時サポートの提供、エラー チェック、変更通知、データ自体に加えられた変更の構造化されたロールバックのサポートに至るまで、さまざまなレベルの機能を提供することができ、複雑さに対応できます。  
  
## <a name="consumers-of-data-binding-interfaces"></a>データ バインディング インターフェイスのコンシューマー  
 以下のセクションでは、インターフェイス オブジェクトの 2 つのグループについて説明します。 1 つ目のグループでは、データ ソース作成者がデータ ソースに実装するインターフェイスを示します。 これらのインターフェイスは、データ ソース コンシューマーが使用するように設計されています。ほとんどの場合、データ ソース コンシューマーは、Windows フォーム コントロールまたはコンポーネントです。 2 つ目のグループでは、コンポーネント作成者向けに設計されたインターフェイスを示します。 コンポーネント作成者は、Windows フォーム データ バインディング エンジンが使用する、データ バインディングをサポートするコンポーネントを作成するときにこれらのインターフェイスを使用します。 フォームに関連付けられたクラス内でこれらのインターフェイスを実装することで、データ バインディングを実現できます。各ケースは、データの操作を可能にするインターフェイスを実装するクラスを示しています。 Visual Studio アプリケーションの迅速な development (RAD) データ デザイン エクスペリエンスのツールでは、この機能のこと既に利用します。  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>データ ソース作成者が実装するインターフェイス  
 以下のインターフェイスは、Windows フォーム コントロールで使用するように設計されています。  
  
-   <xref:System.Collections.IList> インターフェイス  
  
     実装するクラス、<xref:System.Collections.IList>インターフェイス可能性があります、 <xref:System.Array>、 <xref:System.Collections.ArrayList>、または<xref:System.Collections.CollectionBase>です。 これらの型の項目のインデックス付きのリストは、<xref:System.Object>です。 インデックスの最初の項目によって型が決定されるため、これらのリストには同種の型が含まれている必要があります。 <xref:System.Collections.IList> 実行時にのみバインドできるようになります。  
  
    > [!NOTE]
    >  Windows フォームでバインディング用のビジネス オブジェクトの一覧を作成する場合は、使用を検討する必要があります、<xref:System.ComponentModel.BindingList%601>です。 <xref:System.ComponentModel.BindingList%601>双方向の Windows フォーム データ バインディングに必要なプライマリ インターフェイスを実装する拡張可能なクラスです。  
  
-   <xref:System.ComponentModel.IBindingList> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.IBindingList>インターフェイスには、データ バインディング機能の非常に高いレベルが用意されています。 この実装では、基本的な並べ替え機能と変更通知を提供します。変更通知では、リスト項目が変更されたとき (たとえば、顧客リストの 3 番目の項目の Address フィールドが変更されたとき) と、リスト自体が変更されたとき (たとえば、リスト内の項目の数が増減したとき) のどちらの場合も変更が通知されます。 複数のコントロールを同じデータにバインドする予定であり、いずれかのコントロールで行われたデータ変更をバインドされた他のコントロールに反映させる必要がある場合に、変更通知が重要になります。  
  
    > [!NOTE]
    >  変更通知が有効になって、<xref:System.ComponentModel.IBindingList>によってインターフェイスを<xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>プロパティを`true`を発生させます、<xref:System.ComponentModel.IBindingList.ListChanged>変更されたリストまたはリスト内の項目を示すイベントを変更します。  
  
     変更の種類は、<xref:System.ComponentModel.ListChangedType>のプロパティ、<xref:System.ComponentModel.ListChangedEventArgs>パラメーター。 したがって、データ モデルが更新されるたびに、依存するビュー (同じデータ ソースにバインドされた他のコントロールなど) も更新されます。 ただし、一覧に含まれるオブジェクトがリストにリストを発生させることができるように変更したときに通知する必要が、<xref:System.ComponentModel.IBindingList.ListChanged>イベント。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601>の一般的な実装を提供、<xref:System.ComponentModel.IBindingList>インターフェイスです。  
  
-   <xref:System.ComponentModel.IBindingListView> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.IBindingListView>インターフェイスの実装のすべての機能を提供する<xref:System.ComponentModel.IBindingList>、同様に、フィルター処理と高度な並べ替え機能します。 この実装では、文字列ベースのフィルター処理と、プロパティ記述子と方向のペアによる複数列の並べ替え機能を提供します。  
  
-   <xref:System.ComponentModel.IEditableObject> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.IEditableObject>インターフェイスにより、そのオブジェクトへの変更を永続的なものとを制御するオブジェクト。 この実装により、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドで、使用すると、オブジェクトに加えられた変更をロールバックします。 機能の簡単な説明を次に示します、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドと考えられるデータに加えられた変更のロールバックを有効にするのには互いに連携して動作方法。  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>メソッドがオブジェクトの編集の開始を通知します。 このインターフェイスを実装するオブジェクトが、更新プログラムを後に保存する必要があります、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>メソッドの呼び出し、更新プログラムを破棄できるように場合、<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドが呼び出されます。 データ バインディング Windows フォームでを呼び出すことができます<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>複数回、1 つのスコープ内でトランザクションの編集 (たとえば、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>)。 実装<xref:System.ComponentModel.IEditableObject>かどうかを追跡する必要があります<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>は既に呼び出されておよび後続の呼び出しを無視する<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>です。 このメソッドは、複数回呼び出すことができます、ためにが後続の呼び出しが破壊的でないことが重要つまり、後続<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>呼び出しが行われたまたは保存されたデータを変更する更新プログラムを破棄できません。 最初の<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>を呼び出します。  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A>メソッドは、以降のすべての変更をプッシュ<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>が、オブジェクトが現在編集モードである場合、基になるオブジェクトに呼び出されました。  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>メソッドがオブジェクトに加えられた変更を破棄します。  
  
     方法の詳細については<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、 <xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および<xref:System.ComponentModel.IEditableObject.CancelEdit%2A>作業、メソッドを参照してください[データをデータベースに保存](/visualstudio/data-tools/save-data-back-to-the-database)です。  
  
     によってこのトランザクション データ機能の概念が使用される、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
-   <xref:System.ComponentModel.ICancelAddNew> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.ICancelAddNew>インターフェイスは通常、実装、<xref:System.ComponentModel.IBindingList>インターフェイスし、使用して、データ ソースに加え、追加をロールバックすることができます、<xref:System.ComponentModel.IBindingList.AddNew%2A>メソッドです。 データ ソースを実装する場合、<xref:System.ComponentModel.IBindingList>インターフェイスも必要を実施する、<xref:System.ComponentModel.ICancelAddNew>インターフェイスです。  
  
-   <xref:System.ComponentModel.IDataErrorInfo> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.IDataErrorInfo>インターフェイスにより、バインド コントロールをカスタム エラー情報を提供するオブジェクト。  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A>プロパティには、一般的なエラー メッセージ テキストが返されます (たとえば、「エラーが発生しました」) です。  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A>プロパティは、列から特定のエラー メッセージで文字列を返します (たとえば、"の値、`State`列は有効ではありません") です。  
  
-   <xref:System.Collections.IEnumerable> インターフェイス  
  
     実装するクラス、<xref:System.Collections.IEnumerable>インターフェイスがによって使用される通常[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]です。 Windows フォームのこのインターフェイスはのみサポートを介して使用できる、<xref:System.Windows.Forms.BindingSource>コンポーネントです。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource>コンポーネントがすべてコピー<xref:System.Collections.IEnumerable>バインド用に別の一覧にアイテムをします。  
  
-   <xref:System.ComponentModel.ITypedList> インターフェイス  
  
     実装するコレクション クラス、<xref:System.ComponentModel.ITypedList>インターフェイスには、順序と、バインドされたコントロールに公開されるプロパティのセットを制御する機能が用意されています。  
  
    > [!NOTE]
    >  実装する場合、<xref:System.ComponentModel.ITypedList.GetItemProperties%2A>メソッド、および<xref:System.ComponentModel.PropertyDescriptor>配列が null でない、配列の最後のエントリは項目の別の一覧は、一覧のプロパティを説明するプロパティ記述子。  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスがそれ自体の動的な情報を提供します。 このインターフェイスはのような<xref:System.ComponentModel.ITypedList>がリストではなく、オブジェクトの使用されます。 このインターフェイスを使用して<xref:System.Data.DataRowView>基になる行のスキーマをプロジェクトにします。 簡単な実装<xref:System.ComponentModel.ICustomTypeDescriptor>によって提供される、<xref:System.ComponentModel.CustomTypeDescriptor>クラスです。  
  
    > [!NOTE]
    >  デザイン時のバインドをサポートする型を実装する<xref:System.ComponentModel.ICustomTypeDescriptor>、型を実装する必要がありますも<xref:System.ComponentModel.IComponent>フォーム上のインスタンスとして存在します。  
  
-   <xref:System.ComponentModel.IListSource> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.IListSource>インターフェイス非リスト オブジェクトのリストに基づくバインドを有効にします。 <xref:System.ComponentModel.IListSource.GetList%2A>メソッドの<xref:System.ComponentModel.IListSource>から継承しないオブジェクトからバインド可能な一覧を返すために使用<xref:System.Collections.IList>です。 <xref:System.ComponentModel.IListSource> によって使用される、<xref:System.Data.DataSet>クラスです。  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> インターフェイス  
  
     実装するクラス、<xref:System.ComponentModel.IRaiseItemChangedEvents>インターフェイスも実装するバインド可能なリストは、<xref:System.ComponentModel.IBindingList>インターフェイスです。 このインターフェイスは、種類を発生させるかどうかを示すために使用<xref:System.ComponentModel.IBindingList.ListChanged>の種類のイベント<xref:System.ComponentModel.ListChangedType.ItemChanged>を通じてその<xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>プロパティです。  
  
    > [!NOTE]
    >  実装する必要があります、 <xref:System.ComponentModel.IRaiseItemChangedEvents> 、データ ソースから一覧イベントへの変換前に説明したプロパティを提供しとの対話は、<xref:System.Windows.Forms.BindingSource>コンポーネントです。 それ以外の場合、<xref:System.Windows.Forms.BindingSource>一覧イベント変換のパフォーマンスが低下するプロパティも実行されます。  
  
-   <xref:System.ComponentModel.ISupportInitialize> インターフェイス  
  
     実装するコンポーネント、<xref:System.ComponentModel.ISupportInitialize>インターフェイスは、プロパティを設定し、相互に依存するプロパティの初期化中のバッチの最適化の利点があります。 <xref:System.ComponentModel.ISupportInitialize> 2 つのメソッドが含まれています。  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> オブジェクト初期化の開始を通知します。  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> そのオブジェクトの初期化が完了を通知します。  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> インターフェイス  
  
     実装するコンポーネント、<xref:System.ComponentModel.ISupportInitializeNotification>インターフェイスも実装して、<xref:System.ComponentModel.ISupportInitialize>インターフェイスです。 このインターフェイスを使用すると、その他の通知<xref:System.ComponentModel.ISupportInitialize>コンポーネント初期化が完了しました。 <xref:System.ComponentModel.ISupportInitializeNotification>インターフェイスには、2 つのメンバーが含まれています。  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> 返します、`boolean`コンポーネントが初期化されているかどうかを示す値。  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> 発生したときに<xref:System.ComponentModel.ISupportInitialize.EndInit%2A>と呼びます。  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイス  
  
     このインターフェイスを実装するクラスは、プロパティ値のいずれかが変更されたときにイベントを発生させる型です。 このインターフェイスは、コントロールのプロパティごとに変更イベントを持つパターンを置き換えるように設計されています。 使用する場合、 <xref:System.ComponentModel.BindingList%601>、ビジネス オブジェクトを実装する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスと、BindingList\`1 に変換されます<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベント<xref:System.ComponentModel.BindingList%601.ListChanged>の種類のイベント<xref:System.ComponentModel.ListChangedType.ItemChanged>です。  
  
    > [!NOTE]
    >  変更の通知をバインドされているクライアントとデータ間のバインドで発生ソース、バインドされたデータ ソースの種類、実装する必要があります、 <xref:System.ComponentModel.INotifyPropertyChanged> (推奨) インターフェイスを提供できる*propertyName* `Changed`バインドの型がのイベントは、両方を行うことはできません。  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>コンポーネント作成者が実装するインターフェイス  
 以下のインターフェイスは、Windows フォーム データ バインディング エンジンが使用するように設計されています。  
  
-   <xref:System.Windows.Forms.IBindableComponent> インターフェイス  
  
     このインターフェイスを実装するクラスは、データ バインディングをサポートするコントロール以外のコンポーネントです。 このクラスは、データ バインディングおよびバインディング コンテキストを使用して、コンポーネントを返します、<xref:System.Windows.Forms.IBindableComponent.DataBindings%2A>と<xref:System.Windows.Forms.IBindableComponent.BindingContext%2A>このインターフェイスのプロパティです。  
  
    > [!NOTE]
    >  コンポーネントから継承している場合<xref:System.Windows.Forms.Control>、実装する必要はありません、<xref:System.Windows.Forms.IBindableComponent>インターフェイスです。  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> インターフェイス  
  
     実装するクラス、<xref:System.Windows.Forms.ICurrencyManagerProvider>インターフェイスは、独自に提供するコンポーネント<xref:System.Windows.Forms.CurrencyManager>この特定のコンポーネントに関連付けられているバインドを管理します。 カスタムへのアクセス<xref:System.Windows.Forms.CurrencyManager>によって提供される、<xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>プロパティです。  
  
    > [!NOTE]
    >  継承するクラスを<xref:System.Windows.Forms.Control>管理バインドを使用して自動的にその<xref:System.Windows.Forms.Control.BindingContext%2A>プロパティを実装する必要があります。 その場合、<xref:System.Windows.Forms.ICurrencyManagerProvider>非常にまれです。  
  
## <a name="see-also"></a>関連項目  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [方法: Windows フォームに単純バインド コントロールを作成する](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)
