---
title: "例外の処理とスロー | Microsoft Docs"
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
  - "共通言語ランタイム, 例外"
  - "エラー [.NET Framework], 例外"
  - "例外 [.NET Framework]"
  - "例外 [.NET Framework], 処理"
  - "例外 [.NET Framework], スロー"
  - "フィルター処理 (例外の)"
  - "ランタイム, 例外"
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 例外の処理とスロー
<a name="top"></a> アプリケーションは、実行中に発生するエラーを一貫した方法で処理できなければなりません。 共通言語ランタイムは、一貫した方法でアプリケーションにエラーを通知するためのモデルを提供します。 .NET Framework のすべての操作は、例外をスローすることによってエラーを示します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [.NET Framework における例外](#exceptions_in_the_net_framework)  
  
-   [例外:従来のエラー処理メソッド](#exceptions_vs_traditional_errorhandling_methods)  
  
-   [ランタイムが例外を管理する方法](#how_the_runtime_manages_exceptions)  
  
-   [ランタイム例外のフィルター処理](#filtering_runtime_exceptions)  
  
-   [関連トピック](#related_topics)  
  
-   [参照](#reference)  
  
<a name="exceptions_in_the_net_framework"></a>   
## .NET Framework における例外  
 例外とは、プログラムを実行することによって発生するエラー状態または予期しない動作のことです。 例外が発生する原因として、コードまたは呼び出したコード \(たとえば共有ライブラリ\) 内に障害がある、オペレーティング システム リソースを使用できない、予期しない状態 \(たとえば検証できないコード\) を共通言語ランタイムが検出したなどがあります。 アプリケーションは、他の状態からではなく、これらの状態のうちのいくつかから回復できます。 ほとんどのアプリケーション例外から回復できますが、ほとんどのランタイム例外からは回復できません。  
  
 .NET Framework では、例外は <xref:System.Exception?displayProperty=fullName> クラスから継承されるオブジェクトです。 例外は問題が発生したコード領域からスローされます。 例外は、アプリケーションが処理するかプログラムが終了するまで、スタックに渡されます。  
  
 [ページのトップへ](#top)  
  
<a name="exceptions_vs_traditional_errorhandling_methods"></a>   
## 例外:従来のエラー処理メソッド  
 言語のエラー処理モデルは従来、エラーを検出してそれに対応したハンドラーを見つける言語固有の方法か、オペレーティング システムが備えているエラー処理機構のいずれかを使用していました。 ランタイムは、次の機能を含んだ例外処理を実装します。  
  
-   例外を生成する言語または例外を処理する言語に関係なく、例外を処理します。  
  
-   例外を処理するための特定の言語構文を必要とせず、各言語が独自の構文を定義できます。  
  
-   プロセス間で、さらにはコンピューターの境界を越えて例外をスローできます。  
  
 例外には、リターン コードなどの他のエラー通知メソッドに優る利点がいくつかあります。 エラーが通知されずに進行することがありません。 無効な値がシステムに伝わり続けることがありません。 リターン コードを確認する必要がありません。 プログラムの信頼性を高めるための例外処理コードを簡単に追加できます。 最後に、ランタイムの例外処理は、Windows ベースの C\+\+ エラーの処理よりも高速です。  
  
 実行スレッドはコードのマネージ ブロックとアンマネージ ブロックを定期的にスキャンするので、ランタイムはマネージまたはアンマネージのどちらのコードでも例外をスローまたはキャッチできます。 アンマネージ コードには、C\+\+ スタイルの SEH 例外と COM ベースの HRESULT の両方を含めることができます。  
  
<a name="how_the_runtime_manages_exceptions"></a>   
## ランタイムが例外を管理する方法  
 ランタイムは、例外オブジェクトとコードの保護ブロックに基づいた例外処理モデルを使用します。 例外が発生すると、その例外を表す <xref:System.Exception> オブジェクトが作成されます。  
  
 ランタイムは、実行可能ファイルごとに例外情報テーブルを作成します。 実行可能ファイルの各メソッドには、例外情報テーブルで例外処理情報 \(空の場合がある\) の配列が関連付けられています。 配列内の各エントリは、コードの保護ブロック、そのコードに関連付けられた例外フィルター、例外ハンドラー \(`catch` ステートメント\) を示します。 この例外テーブルは非常に効率的なので、例外が発生していない場合にプロセッサ時間やメモリ使用のパフォーマンスが低下する原因にはなりません。 リソースを使用するのは、例外が発生したときだけです。  
  
 例外情報テーブルは、保護ブロックに対応する 4 つのタイプの例外ハンドラーを表します。  
  
-   `finally` ハンドラー。ブロックが終了するときに必ず実行され、通常の制御フローによって発生するか、未処理の例外によって発生します。  
  
-   フォールト ハンドラー。例外が発生すると必ず実行されますが、通常の制御フローの完了時には実行されません。  
  
-   タイプ フィルター ハンドラー。指定したクラスまたはその派生クラスのすべての例外を処理します。  
  
-   ユーザー フィルター ハンドラー。ユーザー指定のコードを実行して、関連付けられたハンドラーで例外を処理するか、次の保護ブロックに例外を渡すかを判断します。  
  
 どの言語でも、その仕様に従ってこれらの例外ハンドラーを実装しています。 たとえば Visual Basic では、`catch` ステートメント内の変数比較 \(`When` キーワードを使用\) を通してユーザー フィルター ハンドラーにアクセスできます。一方 C\# では、ユーザー フィルター ハンドラーを実装していません。  
  
 例外が発生すると、ランタイムは次の 2 段階プロセスを開始します。  
  
1.  ランタイムは、次のようにする最初の保護ブロックの配列を検索します。  
  
    -   現在実行中の命令が含まれている領域を保護する。  
  
    -   例外ハンドラーが含まれているか、例外を処理するフィルターが含まれている。  
  
2.  一致すると、ランタイムは例外を記述する <xref:System.Exception> オブジェクトを作成します。 ランタイムは次に、例外が発生したステートメントと例外を処理するステートメントの間のすべての `finally` またはフォールト ステートメントを実行します。 例外ハンドラーの順序は重要です。最も内側の例外ハンドラーが最初に評価されます。 例外ハンドラーは例外をキャッチするルーチンのローカル変数とローカル メモリにアクセスできるが、例外がスローされるときの中間値は失われるということにも注意してください。  
  
     現在のメソッドで一致しない場合、ランタイムは、現在のメソッドの各呼び出し元を検索し、スタックの最後までこのパスを続けます。 呼び出し元で一致しない場合、ランタイムはデバッガーに例外にアクセスさせます。 例外にデバッガーが付いていなければ、ランタイムは <xref:System.AppDomain.UnhandledException?displayProperty=fullName> イベントを発生させます。 このイベントのリスナーが存在しない場合、ランタイムはスタック トレースをダンプし、アプリケーションを終了します。  
  
 [ページのトップへ](#top)  
  
<a name="filtering_runtime_exceptions"></a>   
## ランタイム例外のフィルター処理  
 キャッチして処理する例外を、タイプでまたは何らかのユーザー定義条件でフィルター処理できます。  
  
 タイプ フィルター ハンドラーは、特定のタイプの例外 \(またはその派生クラス\) を管理します。 次の例は、特定の例外 \(この場合は <xref:System.IO.FileNotFoundException>\) をキャッチすることを意図して設計されたタイプ フィルター ハンドラーを示しています。  
  
 [!code-cpp[CatchException#5](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception3.cpp#5)]
 [!code-csharp[CatchException#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception3.cs#5)]
 [!code-vb[CatchException#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception3.vb#5)]  
  
 ユーザー フィルター例外ハンドラーは、ユーザーが例外に対して定義した要件に基づいて、例外をキャッチして処理します。 この方法による例外のフィルター処理の詳細については、「[キャッチ ブロックでの特定の例外の使用](../../../docs/standard/exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)」を参照してください。  
  
 [ページのトップへ](#top)  
  
<a name="related_topics"></a>   
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[Exception クラスとプロパティ](../../../docs/standard/exceptions/exception-class-and-properties.md)|例外オブジェクトの要素について説明します。|  
|[例外階層](../../../docs/standard/exceptions/exception-hierarchy.md)|ほとんどの例外が派生する例外について説明します。|  
|[例外処理の基本事項](../../../docs/standard/exceptions/exception-handling-fundamentals.md)|キャッチ、スロー、最後にステートメントを使用して例外を処理する方法について説明します。|  
|[例外の推奨事項](../../../docs/standard/exceptions/best-practices-for-exceptions.md)|例外を処理するための推奨方法について説明します。|  
|[COM 相互運用の例外の処理](../../../docs/standard/exceptions/handling-com-interop-exceptions.md)|アンマネージ コードでスローおよびキャッチされた例外を処理する方法について説明します。|  
|[方法: HRESULT に例外を割り当てる](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)|マネージ コードとアンマネージ コード間の例外のマッピングについて説明します。|  
  
<a name="reference"></a>   
## 参照  
 <xref:System.Exception?displayProperty=fullName>  
  
 <xref:System.ApplicationException?displayProperty=fullName>  
  
 <xref:System.SystemException?displayProperty=fullName>