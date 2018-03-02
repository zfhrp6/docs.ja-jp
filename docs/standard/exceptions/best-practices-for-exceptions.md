---
title: "例外の推奨事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c5ea19077ff9ce8e36a33601b7e5e87c64afe60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-exceptions"></a>例外の推奨事項

適切にデザインされたアプリケーションは、アプリケーションのクラッシュを防ぐために、例外やエラーを処理します。 このセクションでは、例外の処理と作成のためのベスト プラクティスについて説明します。

## <a name="use-trycatchfinally-blocks"></a>try/catch/finally ブロックを使用する

`try`/`catch`/`finally` ブロックを使用して、例外を生成する可能性のあるコードを囲みます。 

`catch` ブロックでは、常に特定の例外から一般的な例外の順に例外を配置します。

回復できるかどうかに関わらず、`finally` ブロックを使用してリソースをクリーンアップします。

## <a name="handle-common-conditions-without-throwing-exceptions"></a>例外をスローせずに一般的な状態を処理する

発生する可能性があり、例外をトリガーする可能性がある状態に対し、例外を回避する方法で処理することを検討します。 たとえば、既に終了している接続を終了しようとすると、`InvalidOperationException` を受け取ります。 `if` ステートメントを使用して、終了しようとする前に接続状態を確認することで、これを回避することができます。

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

終了する前に接続状態を確認しない場合は、`InvalidOperationException` 例外をキャッチする可能性があります。

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

選択するメソッドは、予期されるイベント発生頻度によって決まります。

- イベントが頻繁には発生しない場合、つまり、イベントが本当に例外的であり、エラー (予期しないファイルの終端の検出など) を示す場合に、例外処理を使用します。 例外処理を使用すると、通常の状況では、実行されるコードが少なくなります。

- イベントが定期的に発生し、通常の実行の一部であると見なせる場合は、コード内でエラー条件をチェックします。 一般的なエラー条件をチェックするときに、例外を回避するためにより少ないコードが実行されます。

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>例外を回避するようにクラスを設計する

クラスは、例外をトリガーする呼び出しを行うことを回避できるようにするメソッドとプロパティを提供できます。 たとえば、<xref:System.IO.FileStream> クラスには、ファイルの終端に到達したかどうかを判別するために役立つメソッドが用意されています。 これらは、ファイルの終端を越えて読み取りを実行しようとした場合にも例外がスローされないようにするために使用できます。 次の例では、例外をトリガーすることなく、ファイルの末尾まで読み取る方法を示します。

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

例外が返されるのを回避するもう 1 つの方法は、非常に一般的なエラーの場合に、例外をスローする代わりに null を返すことです。 非常に一般的なエラーは、通常の制御の流れと見なすことができます。 このような場合は、null を返すことによって、アプリケーションのパフォーマンスへの影響を最小限に抑えることができます。

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>エラー コードを返す代わりに、例外をスローする

呼び出しのコードはリターン コードを確認しないので、例外によって、エラーを見過ごさないようにします。 

## <a name="use-the-predefined-net-exception-types"></a>事前定義済みの .NET の例外の種類を使用する

事前定義の例外クラスが適用されない場合に限り、新しい例外クラスを導入します。 例:

- オブジェクトの現在の状態に対して、プロパティの設定またはメソッドの呼び出しが適切でない場合は、<xref:System.InvalidOperationException> をスローします。

- <xref:System.ArgumentException> 例外または <xref:System.ArgumentException> から派生する定義済みのクラスの 1 つをスローします。

## <a name="end-exception-class-names-with-the-word-exception"></a>例外クラス名の末尾に `Exception` という単語を付加する

カスタム例外が必要な場合は、適切に名前を付け、<xref:System.Exception> クラスから派生させます。 例:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>カスタム例外クラスに 3 つのコンストラクターを含める

独自の例外クラスを作成するときに、少なくとも 3 つの共通コンストラクターを使用します。それらは、既定のコンストラクター、文字列メッセージを受け取るコンストラクター、および文字列メッセージと内部例外を受け取るコンストラクターです。

* 既定の値を使用する <xref:System.Exception.%23ctor>。
  
* 文字列メッセージを受け取る <xref:System.Exception.%23ctor%28System.String%29>。  
  
* 文字列メッセージと内部例外を受け取る <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>。  
  
例については、「[方法: ユーザー定義の例外を作成する](how-to-create-user-defined-exceptions.md)」を参照してください。

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>コードがリモートで実行されるときに、例外データが利用できるようにする

ユーザー定義例外を作成するときには、リモートで実行されるコードで例外のメタデータを使用できるようにします。 

たとえば、アプリ ドメインをサポートする .NET 実装では、アプリ ドメイン間で例外が発生する可能性があります。 アプリ ドメイン A が、例外をスローするコードを実行するアプリ ドメイン B を作成するとします。 アプリ ドメイン A が例外を適切にキャッチして処理するには、アプリ ドメイン B によりスローされた例外が含まれているアセンブリを検出できる必要があります。アプリ ドメイン B が、アプリ ドメイン A のアプリケーション ベースではなく、自身のアプリケーション ベースの下のアセンブリに含まれている例外をスローする場合、アプリ ドメイン A は、例外を検出できなくなり、共通言語ランタイムが <xref:System.IO.FileNotFoundException> 例外をスローします。 このような状況を回避するには、例外情報が格納されているアセンブリを次のいずれかの方法で配置します。

- 2 つのアプリ ドメインが共有する共通アプリケーション ベースにアセンブリを配置する。

    \- または

- ドメインが共通アプリケーション ベースを共有していない場合には、例外情報が格納されているアセンブリに厳密な名前で署名し、グローバル アセンブリ キャッシュにこのアセンブリを配置する。

## <a name="include-a-localized-description-string-in-every-exception"></a>すべての例外に、ローカライズした説明文字列を含める

ユーザーに対して表示されるエラー メッセージは、例外クラスの名前ではなく、スローされた例外の説明文字列から派生されます。

## <a name="use-grammatically-correct-error-messages"></a>文法的に正しいエラー メッセージを使用する

明確な文を記述し、末尾に句点を含めます。 例外の説明文字列の文の末尾には、必ず句点を使用します。 たとえば、"ログ テーブルがオーバーフローしました。" は、 適切な説明文字列です。

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>カスタム例外で、必要に応じて追加のプロパティを提供する

プログラミングの点で追加情報が役立つ場合にだけ、(説明文字列以外の) 例外の追加プロパティを含めてください。 たとえば、<xref:System.IO.FileNotFoundException> には <xref:System.IO.FileNotFoundException.FileName> プロパティがあります。

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>スタック トレースが役に立つように throw ステートメントを配置する

例外がスローされたステートメントからスタック トレースが開始され、例外をキャッチした `catch` ステートメントでトレースが終了します。

## <a name="use-exception-builder-methods"></a>例外ビルダー メソッドを使用する

一般に、クラスはクラス実装内の複数の位置で同一の例外をスローします。 コードが長くなることを防ぐため、例外を作成して返すヘルパー メソッドを使用します。 例:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
場合によっては、例外のコンストラクターを使用して例外を作成する方が適切な場合もあります。 <xref:System.ArgumentException> などのグローバル例外クラスはその一例です。

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>例外をスローするときに、中間結果を削除する

呼び出し元が、メソッドから例外がスローされるときに副作用が発生しないと仮定できる必要があります。 たとえば、ある口座から現金を引き出して別の口座に預金することで送金を行うコードがあって、預金の実行中に例外がスローされた場合、引き出しが有効のままにしておきたくはないはずです。

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

この状況に対処する方法の 1 つは、預金トランザクションによってスローされた例外をキャッチし、引き出しをロールバックすることです。

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

この例では、`throw` を使用して、元の例外を再スローすることを示しています。これにより、呼び出し元が <xref:System.Exception.InnerException> プロパティを確認することなく、問題の本当の原因を容易に確認できるようになります。 別の方法は、新しい例外をスローして元の例外を内部例外として含めることです。

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>参照  
[例外](index.md)
