---
title: 弱いイベント パターン
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 4b1e8649e5d550ffa2c7ee614cb9102f86a83ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549348"
---
# <a name="weak-event-patterns"></a>弱いイベント パターン
アプリケーションでは、可能であれば、イベント ソースに接続されているハンドラーは破棄されません、ハンドラーをソースに接続されているリスナー オブジェクトと連携します。 このような状況は、メモリ リークが発生する可能性があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] この問題に対処、特定のイベントの専用マネージャー クラスを提供して、そのイベントのリスナーにインターフェイスを実装して使用できるデザイン パターンについて説明します。 この設計パターンと呼ばれる、*弱いイベント パターン*です。  
  
## <a name="why-implement-the-weak-event-pattern"></a>弱いイベント パターンを実装する理由  
 イベントのリッスンと、メモリ リークが発生する可能性があります。 イベントをリッスンするための一般的な手法では、ソースでのイベントにハンドラーをアタッチする言語固有の構文を使用します。 たとえば、C# の場合、その構文は:`source.SomeEvent += new SomeEventHandler(MyEventHandler)`です。  
  
 この手法は、強い参照をイベント ソースからのイベント リスナーを作成します。 オブジェクトの有効期間が影響を受けるソースのオブジェクトの有効期間 (しない限り、イベント ハンドラーが明示的に削除) にリスナーが通常は、リスナーのイベント ハンドラーをアタッチするとします。 特定の状況で、ソースの有効期間ではなく、アプリケーションのビジュアル ツリーに現在属しているかどうかなどするその他の要因によって制御されているリスナーのオブジェクトの有効期間をする可能性があります。 ソース オブジェクトの有効期間は、リスナーのオブジェクトの有効期間からはみ出した、ときに通常のイベント パターンは、メモリ リークが発生につながります。 リスナーが有効のまま保持ためのものよりも長い時間です。  
  
 弱いイベント パターンは、このメモリ リークの問題を解決するために設計されています。 リスナーは、イベントに登録する必要がありますが、リスナーは明示的に認識できない場合の登録を解除するたびに、弱いイベント パターンを使用できます。 弱いイベント パターンは、ソースのオブジェクトの有効期間は、リスナーの役に立つオブジェクトの有効期間を超えた場合にも使用できます。 (この場合、*便利*するによって決定されます)。弱いイベント パターンは、を登録し、任意の方法でリスナーのオブジェクトの有効期間の特性に影響を与えずに、イベントを受信するリスナーを使用できます。 実際には、ソースからの暗黙的な参照では、リスナーは、ガベージ コレクションの条件に適合するかどうかは不明です。 参照は、弱いイベント パターンとの関連する名前付けつまり、弱い参照[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]です。 リスナーはガベージ コレクトされ、それ以外の場合は破棄、ソースが破棄されたオブジェクトへの収集ハンドラーの参照を保持せずに続行できます。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>弱いイベント パターンを実装する必要がありますか。  
 弱いイベント パターンを実装するは、主にコントロールの作成者にとって重要です。 コントロールの作成者は、ユーザーは、動作や、コントロールと挿入されているアプリケーションへの影響の含有関係担当大きくします。 これが含まれています、コントロール オブジェクトの有効期間の動作では、具体的には記載されているメモリ リークの問題の処理には、します。  
  
 特定のシナリオでは、弱いイベント パターンをアプリケーション自体本質的に役立ちます。 このようなシナリオの 1 つは、データ バインディングです。 データ バインディングでは、ソース オブジェクトのバインディングのターゲットは、そのリスナー オブジェクトを完全に独立した一般的なです。 多くの側面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]弱いイベント パターン、イベントの実装方法で適用されるバインディングが既にデータがあります。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>弱いイベント パターンを実装する方法  
 弱いイベント パターンを実装する次の 3 つの方法はあります。 次の表は、3 つの方法を示し、それぞれを使用する際のガイダンスを紹介します。  
  
|方法|実装する場合|  
|--------------|-----------------------|  
|既存の弱いイベント マネージャー クラスを使用します。|サブスクライブするイベントが、対応する<xref:System.Windows.WeakEventManager>、既存の弱いイベント マネージャーを使用します。 WPF に含まれている弱いイベント マネージャーの一覧は、継承階層を参照してください、<xref:System.Windows.WeakEventManager>クラスです。 ただし、他のアプローチのいずれかを選択する必要がありますので、WPF に含まれる比較的少数の弱いイベント マネージャーがあることに注意してください。|  
|ジェネリックの弱いイベント マネージャー クラスを使用します。|ジェネリック型を使用して<xref:System.Windows.WeakEventManager%602>既存<xref:System.Windows.WeakEventManager>が利用できないを実装する簡単な方法を目的し、していない関係する効率。 ジェネリック<xref:System.Windows.WeakEventManager%602>既存またはカスタムの弱いイベント マネージャーより効率が下がります。 たとえば、discover イベントのイベントの名前を指定するために複数のリフレクションでは、ジェネリック クラス。 ジェネリックを使用して、イベントを登録するコードも、<xref:System.Windows.WeakEventManager%602>がより既存を使用するよりも詳細なまたは custom<xref:System.Windows.WeakEventManager>です。|  
|カスタムの弱いイベント マネージャー クラスを作成します。|カスタム作成<xref:System.Windows.WeakEventManager>既存<xref:System.Windows.WeakEventManager>ことはできませんし、最適な効率。 使用するカスタム<xref:System.Windows.WeakEventManager>をサブスクライブするイベントをより効率的になりますが、先頭にさらにコードを記述するコストが発生する操作を行います。|  
  
 次のセクションでは、弱いイベント パターンを実装する方法について説明します。  この説明の目的は、サブスクライブするイベントは、次の特性を持ちます。  
  
-   イベント名が`SomeEvent`です。  
  
-   このイベントは、`EventSource`クラスです。  
  
-   イベント ハンドラーが型: `SomeEventEventHandler` (または`EventHandler<SomeEventEventArgs>`)。  
  
-   このイベントは、型のパラメーターを渡します`SomeEventEventArgs`イベント ハンドラーにします。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>既存の弱いイベント マネージャー クラスを使用します。  
  
1.  既存の弱いイベント マネージャーが見つかりません。  
  
     WPF に含まれている弱いイベント マネージャーの一覧は、継承階層を参照してください、<xref:System.Windows.WeakEventManager>クラスです。  
  
2.  通常のイベント フックアップの代わりに新しいの弱いイベント マネージャーを使用します。  
  
     たとえば、コードでは、次のパターンを使用してイベントにサブスクライブします。  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様に、コードがイベントをアンサブスク ライブするのに次のパターンを使用する場合。  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>ジェネリックの弱いイベント マネージャー クラスを使用します。  
  
1.  ジェネリックを使用して<xref:System.Windows.WeakEventManager%602>通常のイベント フックアップではなくクラスです。  
  
     使用すると<xref:System.Windows.WeakEventManager%602>イベント リスナーを登録するには、イベント ソースを指定し、<xref:System.EventArgs>への呼び出し、クラス型のパラメーターとして型<xref:System.Windows.WeakEventManager%602.AddHandler%2A>次のコードに示すように。  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>カスタムの弱いイベント マネージャー クラスを作成します。  
  
1.  次のクラス テンプレートをプロジェクトにコピーします。  
  
     このクラスから継承、<xref:System.Windows.WeakEventManager>クラスです。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  置換、`SomeEventWeakEventManager`名に置き換えて名前。  
  
3.  イベントの対応する名前の前に説明した 3 つの名前に置き換えます。 (`SomeEvent`、 `EventSource`、および`SomeEventEventArgs`)  
  
4.  管理イベントと同様に表示するには、弱いイベント マネージャー クラスの可視性 (パブリック/内部/プライベート) を設定します。  
  
5.  通常のイベント フックアップの代わりに新しいの弱いイベント マネージャーを使用します。  
  
     たとえば、コードでは、次のパターンを使用してイベントにサブスクライブします。  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同様に、コードがイベントをアンサブスク ライブするのに次のパターンを使用する場合。  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     次のパターンに変更します。  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)
