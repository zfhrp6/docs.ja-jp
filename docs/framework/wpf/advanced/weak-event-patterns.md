---
title: "弱いイベント パターン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント ハンドラー, 弱いイベント パターン"
  - "IWeakEventListener インターフェイス"
  - "弱いイベント パターンの実装"
  - "WeakEventManager クラス"
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 弱いイベント パターン
アプリケーションでは、イベント ソースにアタッチされているハンドラーが、このハンドラーをソースにアタッチしたリスナー オブジェクトとの関連によって、破棄されないことがあります。  このような状況は、メモリ リークにつながる可能性があります。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、デザイン パターンが導入されており、このデザイン パターンを使用して、特定のイベントの専用マネージャー クラスを提供し、そのイベントのリスナーにインターフェイスを実装することによって、この問題に対処できます。  このデザイン パターンは、弱いイベント パターンと呼ばれます。  
  
## 弱いイベント パターンを実装する理由  
 イベントのリッスンによって、メモリ リークが発生する可能性があります。  イベントをリッスンする場合の一般的な手法は、言語固有の構文を使用して、ソース上でイベントにハンドラーをアタッチすることです。  たとえば、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] では、その構文は `source.SomeEvent += new SomeEventHandler(MyEventHandler)` です。  
  
 この手法では、イベント ソースからイベント リスナーへの強い参照を作成します。  通常、リスナーのイベント ハンドラーをアタッチすると、リスナーはオブジェクトの有効期間を持ちますが、この有効期間はソースのオブジェクトの有効期間の影響を受けます \(イベント ハンドラーが明示的に削除されない場合\)。  ただし、特定の状況では、リスナーのオブジェクトの有効期間を、ソースの有効期間によってではなく、アプリケーションのビジュアル ツリーに現在属しているかどうかなどの別の要素によって制御したい場合もあります。  ソース オブジェクトの有効期間がリスナーのオブジェクトの有効期間を超える場合、常に通常のイベント パターンによってメモリ リークが発生します。つまり、このリスナーは想定した以上に長く維持されます。  
  
 弱いイベント パターンは、このメモリ リークの問題を解決するように設計されています。  弱いイベント パターンは、リスナーをイベントに登録する必要がある際に、いつ登録を解除するかを明示的には認識できない場合に使用できます。  また、弱いイベント パターンは、ソースのオブジェクトの有効期間がリスナーの有用なオブジェクトの有効期間を超える場合にも使用できます  \(この場合、*"有用な"* ものは自分自身で判断します\)。弱いイベント パターンを使用すると、リスナーのオブジェクトの有効期間の特性にまったく影響を与えることなく、リスナーをイベントに登録し、イベントを受け取ることができます。  実際には、ソースからの暗黙的な参照では、リスナーがガベージ コレクションの対象であるかどうかは判断されません。  この参照は弱い参照であり、このことから弱いイベント パターンおよび関連する [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の名前が付けられています。  リスナーはガベージ コレクトされ、そうでなければ破棄されて、ソースは存続することができ、破棄されたオブジェクトへの収集不能なハンドラー参照を継続することもありません。  
  
## だれが弱いイベント パターンを実装するのか  
 弱いイベント パターンの実装は、主にコントロール作成者にとって意味があります。  コントロールの作成者には、作成したコントロールの動作と格納およびそれを組み込むアプリケーションに与える影響に対する主な責任があります。  これには、コントロール オブジェクトの有効期間の動作 \(特に、上に示したメモリ リークの問題への対応\) が含まれます。  
  
 弱いイベント パターンを適用すると本質的に役立つシナリオがいくつかあります。  このようなシナリオの 1 つが、データ バインディングです。  データ バインディングでは、ソース オブジェクトが、バインディングのターゲットであるリスナー オブジェクトにまったく依存しない場合が一般的です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディングの多くの側面は、イベントの実装方法に適用される弱いイベント パターンをあらかじめ含んでいます。  
  
## 弱いイベント パターンを実装する方法  
 弱いイベント パターンを実装する 3 とおりの方法があります。  次の表ではを使用すると3 とおりの方法についてガイダンスを提供します。  
  
|方法|実行します。|  
|--------|------------|  
|既存の弱いイベント マネージャー クラスを使用します。|サブスクライブするイベントに対応する <xref:System.Windows.WeakEventManager> を使用すると既存の弱いイベント マネージャーがある場合。  WPF に含まれる弱いイベント マネージャーの一覧については<xref:System.Windows.WeakEventManager> のクラスの継承階層 " を参照してください。  WPF に含まれているためは他の方法の 1 つがを選択する必要があります。ただし比較的少数の弱いイベント マネージャーがあることに注意してください。|  
|一般的に弱いイベント マネージャー クラスを使用します。|既存の <xref:System.Windows.WeakEventManager> が存在しない場合通常 <xref:System.Windows.WeakEventManager%602> を実行する必要があるため簡単にを使用して効率の影響を受けません。  一般的な <xref:System.Windows.WeakEventManager%602> は既存またはカスタムの弱いイベント マネージャーよりも効率的です。  たとえばジェネリック クラスはイベントの名前のイベントを検出するためにリフレクションを実行します。  またジェネリック <xref:System.Windows.WeakEventManager%602> を使用してイベントを登録するコードは既存またはカスタム <xref:System.Windows.WeakEventManager> を使用して冗長です。|  
|カスタム弱いイベント マネージャー クラスを作成します。|既存の <xref:System.Windows.WeakEventManager> 存在しない最適な効率が必要な場合はカスタム <xref:System.Windows.WeakEventManager> を作成します。  カスタム <xref:System.Windows.WeakEventManager> を使用してイベントをサブスクライブする方が効率的ですが先頭でのコードの記述のコストがかかります。|  
  
 以降のセクションでは弱いイベント パターンを実装する方法について説明します。  ここではサブスクライブするイベントには次の特徴があります。  
  
-   イベント名は `SomeEvent` です。  
  
-   イベントは `EventSource` のクラスによって発生します。  
  
-   イベント ハンドラーは型を含んでいます : `SomeEventEventHandler` \(または\) `EventHandler<SomeEventEventArgs>`。  
  
-   イベントがイベント ハンドラーに `SomeEventEventArgs` 型のパラメーターを渡します。  
  
### 既存の弱いイベント マネージャー クラスを使用します。  
  
1.  既存の弱いイベント マネージャーを検索します。  
  
     WPF に含まれる弱いイベント マネージャーの一覧については<xref:System.Windows.WeakEventManager> のクラスの継承階層 " を参照してください。  
  
2.  通常のイベントの接続ではなく弱いイベント マネージャーを使用します。  
  
     たとえばコードがイベントをサブスクライブするには次のパターンを使用する場合 :  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します :  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様にコードがイベントをサブスクライブを解除するには次のパターンを使用する場合 :  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します :  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### 一般的に弱いイベント マネージャー クラスを使用します。  
  
1.  通常のイベントの接続ではなく <xref:System.Windows.WeakEventManager%602> の一般的なクラスを使用します。  
  
     イベント リスナーの登録に <xref:System.Windows.WeakEventManager%602> を使用するとクラスに型パラメーターとして <xref:System.EventArgs> のイベント ソースを指定し次のコードに示すように <xref:System.Windows.WeakEventManager%602.AddHandler%2A> を呼び出します :  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### カスタム弱いイベント マネージャー クラスの作成  
  
1.  プロジェクトに次のクラス テンプレートをコピーします。  
  
     このクラスは <xref:System.Windows.WeakEventManager> クラスから継承します。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  独自の名前と `SomeEventWeakEventManager` の名前に置き換えます。  
  
3.  前に説明したイベントに対応する名前を持つ 3 個の名前に置き換えます。  \(`SomeEvent``EventSource` と `SomeEventEventArgs`\)  
  
4.  イベントは管理するのと同じ表示に弱いイベント マネージャー クラスの表示 \(public または internal キーと秘密キーのペア\) に設定します。  
  
5.  通常のイベントの接続ではなく弱いイベント マネージャーを使用します。  
  
     たとえばコードがイベントをサブスクライブするには次のパターンを使用する場合 :  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します :  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様にコードがイベントをサブスクライブを解除するには次のパターンを使用する場合 :  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します :  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## 参照  
 <xref:System.Windows.WeakEventManager>   
 <xref:System.Windows.IWeakEventListener>   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)