---
title: "イベントベースの非同期パターンの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント ベースの非同期パターン"
  - "ProgressChangedEventArgs クラス"
  - "BackgroundWorker コンポーネント"
  - "イベント [.NET Framework], 非同期"
  - "非同期パターン"
  - "AsyncOperationManager クラス"
  - "スレッド処理 [.NET Framework], 非同期機能"
  - "非同期コンポーネント [.NET Framework]"
  - "AsyncOperation クラス"
  - "AsyncCompletedEventArgs クラス"
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# イベントベースの非同期パターンの実装
いくつかの操作によって顕著な遅延が発生する可能性がありますクラスを作成している場合は、実装することによって、非同期機能を付けることを検討して[非同期パターンの概要をイベントに基づく](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)します。  
  
 イベント ベースの非同期パターンは、標準的な非同期機能を持つクラスをパッケージ化する方法を提供します。 ヘルパー クラスで実装される場合と同様に<xref:System.ComponentModel.AsyncOperationManager>、どのアプリケーション モデル、クラスが正しく動作を含む[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、コンソール アプリケーション、および Windows フォーム アプリケーションです。  
  
 イベント ベースの非同期パターンを実装する例を参照してください。[方法: イベント ベースの非同期パターンをサポートするコンポーネントの実装](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)します。  
  
 検索は、単純な非同期操作の<xref:System.ComponentModel.BackgroundWorker>適切なコンポーネントです。 詳細については<xref:System.ComponentModel.BackgroundWorker>を参照してください[方法: バック グラウンドで操作を実行](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)します。  
  
 次の一覧では、このトピックで説明するイベント ベースの非同期パターンの機能について説明します。  
  
-   イベント ベースの非同期パターンを実装するための機会  
  
-   非同期メソッドの名前を付ける  
  
-   オプションでキャンセルをサポートします。  
  
-   オプションでサポートする場合、IsBusy プロパティ  
  
-   進行状況レポートのサポートを必要に応じて指定します。  
  
-   必要に応じてインクリメンタル結果を返すためのサポートを提供します。  
  
-   処理し、メソッドの Ref パラメーター  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>イベント ベースの非同期パターンを実装するための機会  
 イベント ベースの非同期パターンの実装を検討する場合。  
  
-   クラスのクライアントは必要はありません<xref:System.Threading.WaitHandle>と<xref:System.IAsyncResult>非同期操作、つまり、そのポーリングに使用できるオブジェクトと<xref:System.Threading.WaitHandle.WaitAll%2A>または<xref:System.Threading.WaitHandle.WaitAny%2A>クライアントによってに基づいて作成する必要があります。  
  
-   使い慣れたイベントのデリゲートのモデルを使用するクライアントで管理するための非同期操作を必要とします。  
  
 すべての操作が非同期の実装の候補が、長い待機時間が予想されるものと見なします。 特に適切なは、操作をクライアントがメソッドを呼び出すし、それ以上の介入なしで通知を受けず、です。 適切なは、定期的に進捗状況、インクリメンタル結果や状態の変化をクライアントに通知を継続的に実行される操作です。  
  
 イベント ベースの非同期パターンをサポートする時期を決定する際の詳細については、次を参照してください。[を決定するときに、イベント ベースの非同期パターンを実装する](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)です。  
  
## <a name="naming-asynchronous-methods"></a>非同期メソッドの名前を付ける  
 各同期メソッド*MethodName*の対応する非同期を提供します。  
  
 定義、 *MethodName* `Async`メソッドです。  
  
-   `void` を返します。  
  
-   同じパラメーターを受け取り、 *MethodName*メソッドです。  
  
-   複数の呼び出しを受け入れます。  
  
 必要に応じて定義、 *MethodName* `Async`オーバー ロードのと同じ*MethodName*`Async`と呼ばれますが、追加のオブジェクトの値を持つパラメーターが`userState`です。 その場合、そのメソッドの複数の同時呼び出しを管理する準備を整えておけば場合は、`userState`メソッドの呼び出しを区別するためにすべてのイベント ハンドラーにもたらされる価値です。 できますこれを行う後で利用できるユーザーの状態を格納する場所として単純にします。  
  
 各個別*MethodName* `Async`メソッド シグネチャ。  
  
1.  メソッドと同じクラスでは、次のイベントを定義します。  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  次のデリゲートを定義し、 <xref:System.ComponentModel.AsyncCompletedEventArgs>します。 これらはの場合、同じ名前空間が、クラス自体の外部で定義されます。  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   いることを確認、 *MethodName* `CompletedEventArgs`フィールド、データ バインドできるため、クラスが読み取り専用プロパティとフィールドではなく、メンバーを公開します。  
  
    -   いずれかを定義しない<xref:System.ComponentModel.AsyncCompletedEventArgs>の結果が得られないメソッド用のクラスを派生します。 インスタンスを使用するだけ<xref:System.ComponentModel.AsyncCompletedEventArgs>自体です。  
  
        > [!NOTE]
        >  可能かつ適切なデリゲートを再利用するときにまったく問題ありませんが、 <xref:System.ComponentModel.AsyncCompletedEventArgs>型です。 ここでは、名前付けされませんメソッド名に一貫性のある特定のデリゲート以降と<xref:System.ComponentModel.AsyncCompletedEventArgs>&1; つのメソッドに関連付けられているされません。  
  
## <a name="optionally-support-cancellation"></a>オプションでキャンセルをサポートします。  
 クラスでは、非同期操作のキャンセルをサポートする場合、以下に示すようキャンセルは、クライアントに公開する必要があります。 キャンセルのサポートを定義する前に到達する必要がある&2; つの意思決定ポイントがあることに注意してください。  
  
-   を、今後の予想される追加機能を含め、クラスはキャンセルをサポートする非同期操作を&1; つだけありますか。  
  
-   キャンセルのサポートに複数の保留中の操作をサポートする非同期操作をできるでしょうか。 *MethodName* `Async`メソッドを`userState`パラメーター、おり、いずれかを完了するを待機する前に複数の呼び出しは許可してでしょうか。  
  
 次の表でこれら&2; つの質問に対する回答を使用して、キャンセル メソッドのシグネチャを決定します。  
  
### <a name="visual-basic"></a>Visual Basic  
  
||サポートされている複数の同時操作|一度に&1; つだけの操作|  
|------|------------------------------------------------|----------------------------------|  
|クラス全体で&1; つの非同期操作|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|クラスの複数の非同期操作|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||サポートされている複数の同時操作|一度に&1; つだけの操作|  
|------|------------------------------------------------|----------------------------------|  
|クラス全体で&1; つの非同期操作|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|クラスの複数の非同期操作|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 定義した場合、`CancelAsync(object userState)`メソッドでは、クライアントは、オブジェクトで呼び出されたすべての非同期メソッドを区別できるようにするには、その状態値を選択する場合は注意が必要またはすべての呼び出しで非同期メソッドを&1; つだけでなくにする必要があります。  
  
 1 つの非同期操作のバージョンの名前を決定*MethodName* `AsyncCancel`を Visual Studio の IntelliSense のようなデザイン環境でメソッドをより簡単に検出できないに基づきます。 これにより、関連するメンバーをグループ化し、それらを他のメンバーを持つ非同期機能とは無関係から区別します。 あることを追加する場合の非同期操作で追加今後のバージョンを定義することをお勧め`CancelAsync`します。  
  
 上の表の複数のメソッドを同じクラスに定義されていません。 しないことになる意味では、または、クラス インターフェイスのメソッドの増加に伴うがわかりにくくなります。  
  
 これらのメソッド通常がすぐに、れ、操作を実際にはキャンセルできませんか。 イベントのハンドラーで、 *MethodName* `Completed` 、イベント、 *MethodName* `CompletedEventArgs`オブジェクトが含まれています、`Cancelled`フィールドには、クライアントを使用して、キャンセルが発生したかどうかを確認します。  
  
 説明されているキャンセルのセマンティクスに従う[イベント ベースの非同期パターンを実装するためのベスト プラクティス](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)します。  
  
## <a name="optionally-support-the-isbusy-property"></a>オプションでサポートする場合、IsBusy プロパティ  
 クラスが複数の同時呼び出しをサポートしていない場合は、公開することを検討してください、`IsBusy`プロパティです。 これにより、開発者を判断するかどうか、 *MethodName* `Async`から例外をキャッチせずメソッドが実行されている、 *MethodName* `Async`メソッドです。  
  
 遵守、`IsBusy`セマンティクスの記載[イベント ベースの非同期パターンを実装するためのベスト プラクティス](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)します。  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>進行状況レポートのサポートを必要に応じて指定します。  
 その操作中に進行状況を報告する非同期操作のことをお勧めします。 イベント ベースの非同期パターンは、そのためのガイドラインを示します。  
  
-   必要に応じて、非同期操作で発生し、適切なスレッドで呼び出されるイベントを定義します。 <xref:System.ComponentModel.ProgressChangedEventArgs>オブジェクトは、0 ~ 100 の範囲であると予想される整数値の進行状況インジケーターを実行します。  
  
-   このイベントには、次のように名前を付けます。  
  
    -   `ProgressChanged`クラスが複数の非同期操作 (または将来のバージョンで複数の非同期操作を含めると予想されて) です。  
  
    -   *MethodName* `ProgressChanged`クラスは、非同期操作を&1; つを持つ場合です。  
  
     この名前の付け方は、必要に応じてキャンセルのサポート セクションで説明したキャンセル メソッドに対して行わ対応しています。  
  
 このイベントを使用する必要があります、 <xref:System.ComponentModel.ProgressChangedEventHandler>デリゲート シグネチャと<xref:System.ComponentModel.ProgressChangedEventArgs>クラスです。 代わりに、インスタンス、読み取られたバイトと、ダウンロード操作の合計バイト数) (よりドメイン固有の進行状況インジケーターを提供できる場合、必要があります定義の派生クラス<xref:System.ComponentModel.ProgressChangedEventArgs>します。  
  
 1 つだけ`ProgressChanged`または*MethodName* `ProgressChanged`としては、非同期のメソッドの数にかかわらず、クラスのイベントです。 クライアントが使用する必要があります、`userState`に渡されるオブジェクト、 *MethodName* `Async`メソッドを複数の同時操作の進行状況の更新を区別します。  
  
 複数の操作が進行状況をサポートし、進行状況のさまざまなインジケーターを返すそれぞれの状況である可能性があります。 この場合、1 つで`ProgressChanged`イベントが適切でないと、複数のサポートを検討することが`ProgressChanged`イベントです。 ここでの名前付けパターンを使用して*MethodName* `ProgressChanged`各*MethodName* `Async`メソッドです。  
  
 説明した進行状況レポートのセマンティクスに従う[イベント ベースの非同期パターンを実装するためのベスト プラクティス](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)します。  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>必要に応じてインクリメンタル結果を返すためのサポートを提供します。  
 場合もあります非同期操作が完了する前に、インクリメンタル結果を返すことができます。 このシナリオをサポートするために使用できるオプションが多数あります。 次の例をいくつか。  
  
### <a name="single-operation-class"></a>単一の操作  
 クラスは、1 つの非同期操作のみをサポートし、その操作が、インクリメンタル結果を返すことができません: 場合  
  
-   拡張、 <xref:System.ComponentModel.ProgressChangedEventArgs>インクリメンタル結果データを実行するために入力し、定義、 *MethodName* `ProgressChanged`イベントと、このデータを拡張します。  
  
-   これを発生させる*MethodName* `ProgressChanged`イベントのレポートへの増分の結果があるときです。  
  
 このソリューション適用具体的には、単一非同期操作として、「すべての操作」でインクリメンタル結果を返す発生している同じイベントに問題がないため、 *MethodName* `ProgressChanged`イベントがします。  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>同種のインクリメンタル結果を持つクラスを複数回の操作  
 この場合をこれらインクリメンタル結果をすべて同じ型のデータがあるクラスはそれぞれ、インクリメンタル結果を返すことのできる、複数の非同期メソッドをサポートします。  
  
 クラスについては単一の操作、同じとは、上記で説明したモデルに従う<xref:System.EventArgs>すべてインクリメンタル結果を使用しても構造体。 定義、`ProgressChanged`イベントの代わりに、 *MethodName* `ProgressChanged`イベント、複数の非同期メソッドに適用されるためです。  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>異種のインクリメンタル結果を持つクラスを複数回の操作  
 クラスは、複数の非同期メソッドをサポートする場合、データの別の型を返す各手順に従います。  
  
-   インクリメンタル結果の進行状況のレポートからレポートを区切ります。  
  
-   別の定義*MethodName* `ProgressChanged`イベントを適切な<xref:System.EventArgs>そのメソッドの増分の結果データを処理する各非同期メソッドのです。  
  
 」の説明に従って、適切なスレッドでは、そのイベント ハンドラーを呼び出す[イベント ベースの非同期パターンを実装するためのベスト プラクティス](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)します。  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>処理し、メソッドの Ref パラメーター  
 使用する`out`と`ref`一般に、.NET Framework で避けることを推奨、ここでは、ルールが含まれているときに実行します。  
  
 同期メソッドを指定した*MethodName*:  
  
-   `out`パラメーターを*MethodName*の一部をすることはできません*MethodName*`Async`します。 代わりの一部をすることがあります*MethodName* `CompletedEventArgs`と等価で、パラメーターと同じ名前の*MethodName* (がない限りより適切な名前)。  
  
-   `ref`パラメーターを*MethodName*の一部として出現する必要があります*MethodName*`Async`の一部として*MethodName* `CompletedEventArgs`と等価で、パラメーターと同じ名前の*MethodName* (がない限りより適切な名前)。  
  
 例を示します。  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 非同期メソッドとその<xref:System.ComponentModel.AsyncCompletedEventArgs>クラスは次のようになります。  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.ProgressChangedEventArgs>   
 <xref:System.ComponentModel.AsyncCompletedEventArgs>   
 [方法: イベント ベースの非同期パターンをサポートするコンポーネントの実装](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [方法: バック グラウンドで操作を実行](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [方法: フォーム バック グラウンド操作を実装します。](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [イベント ベースの非同期パターンを実装する状況の判断](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)   
 [イベント ベースの非同期パターンではマルチ スレッド プログラミング](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)   
 [イベント ベースの非同期パターンを実装するためのベスト プラクティス](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)