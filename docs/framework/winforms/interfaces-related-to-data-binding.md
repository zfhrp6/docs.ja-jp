---
title: "データ連結に関連するインターフェイス | Microsoft Docs"
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
  - "データ [Windows フォーム], データ バインディング インターフェイス"
  - "データ バインド, インターフェイス"
  - "IBindingList インターフェイス, Windows フォームのデータ バインディング"
  - "IBindingListView インターフェイス"
  - "IDataErrorInfo インターフェイス, Windows フォームのデータ バインディング"
  - "IEditableObject インターフェイス, Windows フォームのデータ バインディング"
  - "IList インターフェイス, Windows フォームのデータ バインディング"
  - "INotifyPropertyChanged インターフェイス"
  - "インターフェイス, Windows フォームのデータ バインディング"
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# データ連結に関連するインターフェイス
[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] では、アプリケーションで必要なバインディングや、処理する対象のデータに合わせて、さまざまなデータ構造を作成できます。  Windows フォームでデータを提供または利用するための独自のクラスを作成すると役立つ場合があります。  これらのオブジェクトはさまざまなレベルの機能を提供でき、複雑さもそれぞれに異なります。基本的なデータ バインディングを提供するもの、デザイン時のサポート、エラー チェック機能、または変更通知機能を提供するもの、さらには、データ自体に加えられた変更の構造化されたロールバックをサポートするものまであります。  
  
## データ バインディング インターフェイスのコンシューマー  
 以下のセクションでは、インターフェイス オブジェクトを 2 つのグループに分けて説明します。  1 つ目のグループは、データ ソース作成者がデータ ソースに実装するインターフェイスの一覧です。  これらのインターフェイスは、データ ソース コンシューマーによって利用されるようにデザインされています。データ ソース コンシューマーは、通常は Windows フォーム コントロールまたはコンポーネントです。  2 つ目のグループは、コンポーネント作成者によって利用されるようデザインされているインターフェイスの一覧です。  Windows フォーム データ バインディング エンジンが利用する、データ バインディングをサポートするコンポーネントを作成するときに、コンポーネント作成者はこれらのインターフェイスを使用します。  フォームに関連付けられたクラス内にこれらのインターフェイスを実装することで、データ バインディングを有効にできます。つまり、データとの対話を実現するインターフェイスを実装したクラスを作成できます。  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の Rapid Application Development \(RAD\) データ デザイン体験ツールでは、この機能が既に活用されています。  
  
### データ ソース作成者が実装するインターフェイス  
 以下のインターフェイスは、Windows フォーム コントロールによって利用されるようにデザインされています。  
  
-   <xref:System.Collections.IList> インターフェイスの使い方  
  
     <xref:System.Collections.IList> インターフェイスを実装するクラスには、<xref:System.Array>、<xref:System.Collections.ArrayList>、および <xref:System.Collections.CollectionBase> があります。  これらは、<xref:System.Object> 型の項目のインデックス付きリストです。  これらのリストは、同じ型のみを格納できます。インデックスの先頭の項目によって型が決定されるためです。  <xref:System.Collections.IList> は、実行時にのみバインディングに利用できます。  
  
    > [!NOTE]
    >  Windows フォームとのバインディングのために、ビジネス オブジェクトのリストを作成する場合には、<xref:System.ComponentModel.BindingList%601> の使用を検討する必要があります。  <xref:System.ComponentModel.BindingList%601> は、双方向の Windows フォーム データ バインディングに必要となる主要なインターフェイスが実装された、拡張性のあるクラスです。  
  
-   <xref:System.ComponentModel.IBindingList> インターフェイスの使い方  
  
     <xref:System.ComponentModel.IBindingList> インターフェイスを実装するクラスは、はるかに高いレベルのデータ バインディング機能を提供します。  この実装は、基本的な並べ替え機能と変更通知機能を持ちます。変更通知機能では、リスト項目が変更されたとき \(たとえば、顧客リストの 3 番目の項目で Address フィールドが変更されたとき\) とリスト自体が変更されたとき \(たとえば、リスト内の項目の数が増減したとき\) の両方について変更が通知されます。  変更通知は、複数のコントロールを同じデータにバインドする予定のときに、1 つのコントロールで行ったデータ変更を他のバインド コントロールにも反映させる場合に重要です。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.IBindingList> インターフェイスの変更通知は <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> プロパティで有効にされます。このプロパティが `true` の場合には <xref:System.ComponentModel.IBindingList.ListChanged> イベントが発生し、リストまたはその中の項目が変更されたことが示されます。  
  
     変更の種類は、<xref:System.ComponentModel.ListChangedEventArgs> パラメーターの <xref:System.ComponentModel.ListChangedType> プロパティで示されます。  したがって、データ モデルが更新されたときには、それに依存するビュー \(たとえば、同じデータ ソースにバインドされた他のコントロール\) も更新されます。  ただし、リストが <xref:System.ComponentModel.IBindingList.ListChanged> イベントを発生させるためには、リスト内に含まれるオブジェクトが変更されたときに、それをリストに通知する必要があります。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> は、<xref:System.ComponentModel.IBindingList> インターフェイスの汎用実装です。  
  
-   <xref:System.ComponentModel.IBindingListView> インターフェイスの使い方  
  
     <xref:System.ComponentModel.IBindingListView> インターフェイスを実装するクラスは、<xref:System.ComponentModel.IBindingList> の実装が持つすべての機能に加えて、フィルター処理機能および高度な並べ替え機能を持ちます。  この実装は、文字列ベースのフィルター処理、およびプロパティ記述子と方向のペアによる複数列の並べ替え機能を提供します。  
  
-   <xref:System.ComponentModel.IEditableObject> インターフェイスの使い方  
  
     <xref:System.ComponentModel.IEditableObject> インターフェイスを実装するクラスを使用すると、オブジェクトへの変更を永続化するタイミングをオブジェクトが制御できるようになります。  この実装により、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> の各メソッドを使用できるようになり、それによってオブジェクトへの変更をロールバックできます。  次に示すのは、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> の各メソッドの機能と、データに対して加えられた変更のロールバックを実現するためのこれら各メソッドの連係についての簡単な説明です。  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> メソッドはオブジェクトの編集の開始を示します。  このインターフェイスを実装するオブジェクトは、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A> メソッドの呼び出し後に加えられたすべての更新を格納して、<xref:System.ComponentModel.IEditableObject.CancelEdit%2A> メソッドが呼び出されたときに破棄できるようにする必要があります。  Windows フォームのデータ バインディングでは、1 つの編集トランザクションのスコープ内で <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> を複数回呼び出すことができます \(たとえば、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A>\)。  <xref:System.ComponentModel.IEditableObject> の実装では、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A> が既に呼び出されたかどうかを追跡し、それ以降の <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> の呼び出しを無視する必要があります。  このメソッドは複数回呼び出すことができるため、同じメソッドの以降の呼び出しが破壊的でないことが重要です。つまり、以降の <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> の呼び出しでは、既に加えられている更新を破棄したり、最初の <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> 呼び出し時に保存されたデータを変更したりすることはできません。  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> メソッドは、基になるオブジェクトが現在編集モードである場合に、<xref:System.ComponentModel.IEditableObject.BeginEdit%2A> の呼び出し後に加えられた変更をオブジェクトに反映します。  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> メソッドは、オブジェクトに加えられた変更を破棄します。  
  
     <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>、<xref:System.ComponentModel.IEditableObject.EndEdit%2A>、および <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> の各メソッドの機能の詳細については、「[データセットのデータの保存](../Topic/Save%20data%20back%20to%20the%20database.md)」を参照してください。  
  
     データ機能のこのトランザクションの概念は、<xref:System.Windows.Forms.DataGridView> コントロールで使用されています。  
  
-   <xref:System.ComponentModel.ICancelAddNew> インターフェイスの使い方  
  
     <xref:System.ComponentModel.ICancelAddNew> インターフェイスを実装するクラスには、<xref:System.ComponentModel.IBindingList> インターフェイスも実装するのが一般的で、<xref:System.ComponentModel.IBindingList.AddNew%2A> メソッドでデータ ソースに対して行われた追加をロールバックできるようにします。  データ ソースに <xref:System.ComponentModel.IBindingList> インターフェイスを実装する場合には、<xref:System.ComponentModel.ICancelAddNew> インターフェイスも実装する必要があります。  
  
-   <xref:System.ComponentModel.IDataErrorInfo> インターフェイスの使い方  
  
     <xref:System.ComponentModel.IDataErrorInfo> インターフェイスを実装するクラスでは、オブジェクトからバインド コントロールに対してカスタムのエラー情報を次のように提供できます。  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> プロパティは、一般的なエラー メッセージ テキスト \(たとえば、"An error has occurred"\) を返します。  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> プロパティは、列からの具体的なエラー メッセージを含む文字列 \(たとえば、"The value in the `State` column is invalid"\) を返します。  
  
-   <xref:System.Collections.IEnumerable> インターフェイスの使い方  
  
     <xref:System.Collections.IEnumerable> インターフェイスを実装するクラスは、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] によって利用されるのが一般的です。  このインターフェイスに対する Windows フォームのサポートは、<xref:System.Windows.Forms.BindingSource> コンポーネントを通じてのみ利用できます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> コンポーネントは、バインディングのために、すべての <xref:System.Collections.IEnumerable> 項目を別個のリストにコピーします。  
  
-   <xref:System.ComponentModel.ITypedList> インターフェイスの使い方  
  
     <xref:System.ComponentModel.ITypedList> インターフェイスを実装するコレクション クラスは、バインド コントロールに対して公開するプロパティの順序と組み合わせを制御する機能を持ちます。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> メソッドを実装するとき、<xref:System.ComponentModel.PropertyDescriptor> 配列が null でない場合には、配列の最後のエントリは、他の項目リストであるリスト プロパティを説明するプロパティ記述子です。  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> インターフェイスの使い方  
  
     <xref:System.ComponentModel.ICustomTypeDescriptor> インターフェイスを実装するクラスは、自らに関する動的な情報を提供します。  このインターフェイスは <xref:System.ComponentModel.ITypedList> に似ていますが、リストではなくオブジェクトに対して使用されます。  このインターフェイスは、<xref:System.Data.DataRowView> によって、基になる行のスキーマを反映するために使用されます。  <xref:System.ComponentModel.ICustomTypeDescriptor> の単純な実装は <xref:System.ComponentModel.CustomTypeDescriptor> クラスにより提供されています。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.ICustomTypeDescriptor> を実装する型に対するデザイン時バインディングをサポートするためには、その型に <xref:System.ComponentModel.IComponent> も実装し、フォーム上にインスタンスとして配置する必要があります。  
  
-   <xref:System.ComponentModel.IListSource> インターフェイスの使い方  
  
     <xref:System.ComponentModel.IListSource> インターフェイスを実装するクラスでは、非リスト オブジェクトへのリストベース バインディングが可能になります。  <xref:System.ComponentModel.IListSource> の <xref:System.ComponentModel.IListSource.GetList%2A> メソッドを使用すると、<xref:System.Collections.IList> を継承していないオブジェクトから、バインドできるリストを取得できます。  <xref:System.ComponentModel.IListSource> は <xref:System.Data.DataSet> クラスで使用されます。  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> インターフェイスの使い方  
  
     <xref:System.ComponentModel.IRaiseItemChangedEvents> インターフェイスを実装するクラスは、<xref:System.ComponentModel.IBindingList> インターフェイスも実装する、バインドできるリストです。  このインターフェイスは、<xref:System.ComponentModel.ListChangedType> 型の <xref:System.ComponentModel.IBindingList.ListChanged> イベントを発生させる型かどうかを <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> プロパティを通じて示すために使用されます。  
  
    > [!NOTE]
    >  データ ソースが、前述のリスト イベント変換を行うプロパティを持ち、<xref:System.Windows.Forms.BindingSource> コンポーネントとやり取りする場合には、<xref:System.ComponentModel.IRaiseItemChangedEvents> を実装する必要があります。  その他の場合は、<xref:System.Windows.Forms.BindingSource> がリスト イベント変換のためのプロパティを実行し、結果としてパフォーマンスが低下します。  
  
-   <xref:System.ComponentModel.ISupportInitialize> インターフェイスの使い方  
  
     <xref:System.ComponentModel.ISupportInitialize> インターフェイスを実装するコンポーネントは、プロパティの設定、および互いに依存するプロパティの初期化のために、バッチ最適化を活用します。  <xref:System.ComponentModel.ISupportInitialize> は次の 2 つのメソッドを持ちます。  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> は、オブジェクトの初期化の開始を通知します。  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> は、オブジェクトの初期化の終了を通知します。  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> インターフェイスの使い方  
  
     <xref:System.ComponentModel.ISupportInitializeNotification> インターフェイスを実装するコンポーネントは <xref:System.ComponentModel.ISupportInitialize> インターフェイスも実装します。  このインターフェイスを使用すると、他の <xref:System.ComponentModel.ISupportInitialize> コンポーネントに対して初期化の完了を通知できます。  <xref:System.ComponentModel.ISupportInitializeNotification> インターフェイスは次の 2 つのメンバーを持ちます。  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> は、コンポーネントが初期化されているかどうかを示す `boolean` 値を返します。  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> は、<xref:System.ComponentModel.ISupportInitialize.EndInit%2A> が呼び出されたときに発生します。  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスの使い方  
  
     このインターフェイスを実装するクラスは、いずれかのプロパティ値が変更されたときにイベントを発生させる型です。  このインターフェイスは、コントロールの各プロパティに対して変更イベントを用意するパターンを置き換えるようにデザインされています。  <xref:System.ComponentModel.BindingList%601> で使用する場合、ビジネス オブジェクトは <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装する必要があり、BindingList\`1 は <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> イベントを <xref:System.ComponentModel.ListChangedType> 型の <xref:System.ComponentModel.BindingList%601.ListChanged> イベントに変換します。  
  
    > [!NOTE]
    >  バインド クライアントとデータ ソースとの間のバインディングで変更通知が行われるためには、バインドされるデータ ソース型に <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装するか、またはバインドされる型に *propertyName*`Changed` イベントを用意するかのいずれか一方を行う必要があります。両方を行うことはできません \(前者を行うことをお勧めします\)。  
  
### コンポーネント作成者が実装するインターフェイス  
 以下のインターフェイスは、Windows フォームのデータ バインディング エンジンによって利用されるようデザインされています。  
  
-   <xref:System.Windows.Forms.IBindableComponent> インターフェイスの使い方  
  
     このインターフェイスを実装するクラスは、データ バインディングをサポートする非コントロール コンポーネントです。  このクラスは、このインターフェイスの <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> プロパティおよび <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> プロパティを通じて、コンポーネントのデータ バインディングおよびバインディング コンテキストを返します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control> を継承するコンポーネントの場合は、<xref:System.Windows.Forms.IBindableComponent> インターフェイスを実装する必要はありません。  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> インターフェイスの使い方  
  
     <xref:System.Windows.Forms.ICurrencyManagerProvider> インターフェイスを実装するクラスは、この特定のコンポーネントに関連付けられたバインディングを管理するための独自の <xref:System.Windows.Forms.CurrencyManager> を持つコンポーネントです。  カスタムの <xref:System.Windows.Forms.CurrencyManager> へは <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> プロパティからアクセスできます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Control> を継承するクラスでは、バインディングは <xref:System.Windows.Forms.Control.BindingContext%2A> プロパティを通じて自動的に管理されます。そのため、<xref:System.Windows.Forms.ICurrencyManagerProvider> の実装が必要なケースはきわめてまれです。  
  
## 参照  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [方法 : Windows フォームに単純バインド コントロールを作成する](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)