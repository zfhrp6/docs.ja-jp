---
title: "例外の推奨事項 | Microsoft Docs"
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
  - "例外, 推奨される手順"
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# 例外の推奨事項
適切にデザインされたアプリケーションは、アプリケーションのクラッシュを防ぐために、例外やエラーを処理します。  ここでは、例外の処理と作成のためのベスト プラクティスについて説明します。  
  
## 例外処理  
 次の一覧に、アプリケーションで例外を処理するための一般的なガイドラインを示します。  
  
-   例外処理コード \(`try`\/`catch` ブロック\) を適切に使用します。  例外処理を実行せずに、発生する可能性のあるエラーの条件をプログラムによってチェックすることもできます。  
  
     **プログラムによるチェック**。  接続が閉じているかどうかをチェックする `if` ステートメントを次のコード例に示します。  閉じていない場合、コード例は例外をスローせずに接続を閉じます。  
  
     [!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
     [!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
     [!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  
  
     **例外処理**。  次の例は、`try`\/`catch` ブロックを使用して接続を確認し、接続が閉じられていない場合は例外をスローします。  
  
     [!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
     [!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
     [!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  
  
     例外処理を使用するかどうかは、予期されるイベント発生頻度によって決まります。  
  
    -   イベントが頻繁には発生しない場合、つまり、イベントが本当に例外的であり、エラー \(予期しないファイルの終端の検出など\) を示す場合に、例外処理を使用します。  例外処理を使用すると、通常の状況では、実行されるコードが少なくなります。  
  
    -   イベントが頻繁に発生し、通常の実行の一部であると見なせる場合は、プログラムによってエラーをチェックする方法を使用します。  プログラムによってエラーをチェックすると、例外が発生した場合に、より多くのコードが実行されます。  
  
-   例外が発生する可能性のあるコードの前後に `try`\/`catch` ブロックを配置し、必要に応じて `finally` ブロックを使用してリソースをクリーンアップします。  このように配置することで、`try` ステートメントで例外が発生すると、`catch` ステートメントが例外を処理し、`finally` ステートメントは例外の発生の有無にかかわらずリソースを閉じるかまたは解放します。  
  
-   `catch` ブロックでは、常に特定の例外から一般的な例外の順に例外を配置します。  この手法により、まず特定の例外が処理され、次にこの例外がより一般的な `catch` ブロックに渡されます。  
  
## 例外の作成と発生  
 次の一覧では、独自の例外の作成と、それをいつ発生させるかについてのガイドラインを示します。  詳細については、「[例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)」を参照してください。  
  
-   通常の使用状態では例外が返されないようにクラスをデザインします。  たとえば、<xref:System.IO.FileStream> クラスには、ファイルの終端に到達したかどうかを判別するために役立つメソッドが用意されています。  これにより、ファイルの終端を越えて読み取りを実行しようとした場合にも例外がスローされません。  ファイルの終端の読み取り方法を示すコード例を次に示します。  
  
     [!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
     [!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
     [!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  
  
-   エラー コードや HRESULT を返す代わりに、例外をスローします。  
  
-   非常に一般的なエラーの場合は、例外をスローする代わりに null を返します。  非常に一般的なエラーは、通常の制御の流れと見なすことができます。  このような場合は、null を返すことによって、アプリケーションのパフォーマンスへの影響を最小限に抑えることができます。  
  
-   ほとんどの場合、事前に定義されている .NET Framework 例外タイプを使用します。  事前定義の例外クラスが適用されない場合に限り、新しい例外クラスを導入します。  
  
-   オブジェクトの現在の状態に対して、プロパティの設定またはメソッドの呼び出しが適切でない場合は、<xref:System.InvalidOperationException> をスローします。  
  
-   無効なパラメーターが渡された場合は、<xref:System.ArgumentException> 例外または <xref:System.ArgumentException> の派生クラスをスローします。  
  
-   ほとんどのアプリでは、<xref:System.Exception> クラスからカスタム例外を派生します。  <xref:System.ApplicationException> クラスからの派生によって大きな価値が付加されることはありません。  
  
-   例外クラス名の終わりに "Exception" という単語を付けてください。  次に例を示します。  
  
     [!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
     [!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
     [!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  
  
-   C\# および C\+\+ では、独自の例外クラスを作成するときに、少なくとも 3 つの共通コンストラクターを使用します。それらは、既定のコンストラクター、文字列メッセージを受け取るコンストラクター、および文字列メッセージと内部例外を受け取るコンストラクターです。  例については、「[方法 : ユーザー定義の例外を作成する](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md)」を参照してください。  
  
    1.  既定の値を使用する <xref:System.Exception.%23ctor>。  
  
    2.  文字列メッセージを受け取る <xref:System.Exception.%23ctor%28System.String%29>。  
  
    3.  文字列メッセージと内部例外を受け取る <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>。  
  
-   ユーザー定義例外を作成するときには例外のメタデータを使用できるようにしてください。アプリ ドメイン間で例外が発生した場合や、リモート処理で必要となります。  たとえば、アプリ ドメイン A によってアプリ ドメイン B が作成され、このドメイン B で例外をスローするコードが実行されるとします。  アプリ ドメイン A で例外を適切にキャッチして処理するには、ドメイン A が、アプリ ドメイン B によりスローされた例外が格納されているアセンブリを検出できる必要があります。  アプリ ドメイン B がスローした例外が、ドメイン A のアプリケーション ベースではなくドメイン B のアプリケーション ベースにあるアセンブリに格納されている場合、ドメイン A は例外を検出できないため、共通言語ランタイムが <xref:System.IO.FileNotFoundException> 例外をスローします。  このような状況を回避するには、例外情報が格納されているアセンブリを次のいずれかの方法で配置します。  
  
    -   2 つのアプリ ドメインが共有する共通アプリケーション ベースにアセンブリを配置する。  
  
         または  
  
    -   ドメインが共通アプリケーション ベースを共有していない場合には、例外情報が格納されているアセンブリに厳密な名前で署名し、グローバル アセンブリ キャッシュにこのアセンブリを配置する。  
  
-   すべての例外に、ローカライズした説明文字列を含めます。  ユーザーに対して表示されるエラー メッセージは、例外クラスではなく、スローされた例外の説明文字列から派生されます。  
  
-   文法的に正しいエラー メッセージを使用します。句点も含めてください。  例外の説明文字列の文の末尾には、必ず句点を使用します。  たとえば、"ログ テーブルがオーバーフローしました。" は、適切な説明文字列です。  
  
-   プログラムからアクセスできるように、<xref:System.Exception> のプロパティを設定します。  プログラミングの点で追加情報が役立つ場合にだけ、\(説明文字列以外の\) 例外の追加プロパティを含めてください。  たとえば、<xref:System.IO.FileNotFoundException> には <xref:System.IO.FileNotFoundException.FileName%2A> プロパティがあります。  
  
-   例外がスローされたステートメントからスタック トレースが開始され、例外をキャッチした `catch` ステートメントでトレースが終了します。  `throw` ステートメントを配置する位置を決定するときには、このことに注意してください。  
  
-   例外ビルダー メソッドを使用します。  一般に、クラスはクラス実装内の複数の位置で同一の例外をスローします。  コードが長くなることを防ぐため、例外を作成して返すヘルパー メソッドを使用します。  次に例を示します。  
  
     [!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
     [!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
     [!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
     例外のコンストラクターを使用して例外を作成することもできます。  この方法は、<xref:System.ArgumentException> などのグローバル例外クラスに適しています。  
  
-   例外をスローするときに、中間結果を削除します。  呼び出し元が、メソッドから例外がスローされるときに副作用が発生しないと仮定できる必要があります。  
  
## 参照  
 [例外](../../../docs/standard/exceptions/index.md)