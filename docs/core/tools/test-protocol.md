---
title: ".NET Core CLI テスト通信プロトコル | Microsoft Docs"
description: ".NET Core CLI テスト通信プロトコル"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88cba792-3640-41de-b55d-00f575e9d5e2
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 83555650a5a3ce9ed28d329aa82f5ead75e2d9cb

---

#<a name="net-core-cli-test-communication-protocol"></a>.NET Core CLI テスト通信プロトコル

> [!WARNING]
> このトピックは .NET Core Tools Preview 2 を対象としています。 .NET Core Tools RC4 ドキュメントについては、「[.NET Core コマンドライン インターフェイス ツール (.NET Core Tools RC4)](../preview3/tools/index.md)」セクションを参照してください。

## <a name="introduction"></a>はじめに
dotnet テストにポートを渡すときはいつでも、デザイン時、このコマンドが実行されます。 つまり、`dotnet test` は TCP を利用してそのポートに接続し、そのポートに接続されている要素と確立済みの一連のメッセージを交換します。 これが行われるとき、ランナーも、`dotnet test` がそれとの通信に使用する新しいポートを受け取ります。 ランナーも TCP を利用して `dotnet test` と通信する理由は、デザイン モードでは、コンソールに結果を出力するだけでは十分ではないためです。 このコマンドは、テスト実行の結果を含むアダプター構造メッセージを送信する必要があります。

### <a name="communication-protocol-at-design-time"></a>デザイン時の通信プロトコル。

1. デザイン時に、`dotnet test` は起動するとポートに接続するため、アダプターはそのポートでリッスンする必要があります。そうでない場合、`dotnet test` は失敗します。 アダプターが必要なすべてのポートを予約できるように、そのような措置を行いました。`dotnet test` が実行され、ランナーのポートを取得しようとする前に、アダプターは必要なすべてのポートをバインドし、リッスンします。
2. `dotnet test` が開始されると、TestSession.Connected メッセージをアダプターに送信し、メッセージの受信準備ができていることを示します。
3. プロトコルのアダプター バージョンを含む任意の[バージョン チェック](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/ProtocolVersionMessage.cs) メッセージを送信できます。 `dotnet test` は、それがサポートするプロトコルのバージョンを返します。

すべてのメッセージにここで説明する形式が与えられます: [Message.cs](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/Message.cs)。 各メッセージのペイロード形式は、プロトコルの説明の情報をシリアル化/逆シリアル化するためのクラスのリンクで説明されます。

#### <a name="test-execution"></a>テストの実行
![テストの実行](./media/test-protocol/dotnet-test-execute.png)

1. 任意のバージョン チェック後、アダプターは TestExecution.GetTestRunnerProcessStartInfo を送信します。その中で実行する[テスト](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs)が含まれます。 `dotnet test` は [TestStartInfo](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/dotnet/commands/dotnet-test/TestStartInfo.cs) ペイロード内で FileName と Arguments を返します。アダプターはこれを利用し、ランナーを開始できます。 以前は、この引数の一部として実行するテストの一覧を送信していました。しかしながら、実際は、一部のテスト プロジェクトでは、コマンド ラインのサイズ上限を超えていました。
  1. 引数の一部として、ランナーが接続するべきポートを送信し、テストを実行するために、--wait-command フラグを送信します。このフラグは、ランナーはポートに接続したら先に進んでテストを実行する代わりにコマンドを待つことを指示します。
2. この時点で、アダプターはランナーを起動できます (選択した場合、ランナーに接続し、デバッグします)。
3. ランナーが起動すると、`dotnet test`に TestRunner.WaitCommand メッセージを送信し、コマンドの受信準備ができていることを示します。その時点で、`dotnet test`は TestRunner.Execute と実行する[テスト](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Messages/RunTestsMessage.cs)の一覧を送信します。 これは前述のコマンド ラインのサイズ上限を無視します。
4. 次にランナーは `dotnet test` に各テストの TestExecution.TestStarted を送信します (その後、アダプターに転送されます)。各テストはその中の[テスト](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Test.cs)情報で開始します。
5. ランナーはまた、`dotnet test` に各テストの TestExecution.TestResult を送信します (その後、アダプターに転送されます)。これにはテストの[個別結果](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/TestResult.cs)が含まれます。
6. すべてのテストが完了すると、ランナーは TestRunner.Completed メッセージを dotnet テストに送信します。これを `dotnet test` は TestExecution.Completed としてアダプターに送信します。
7. アダプターが完了すると、`dotnet test` に TestSession.Terminate を送信します。これで `dotnet test` はシャットダウンします。

#### <a name="test-discovery"></a>テスト探索
![テスト探索](./media/test-protocol/dotnet-test-discover.png)

1. 任意のバージョン チェック後、アダプターは TestDiscovery.Start メッセージを送信します。 この場合、アダプターはプロセスに接続する必要がないため、`dotnet test` はランナー自体を起動しません。 また、ランナーに渡す引数の長い一覧がないため、--wait-command フラグをランナーに渡す必要がありません。 `dotnet test` は --list 引数のみをランナーに渡します。つまり、ランナーはテストを実行する必要がなく、一覧表示するだけです。
2. 次にランナーは `dotnet test` に、見つかった[テスト](https://github.com/dotnet/cli/blob/rel/1.0.0-preview2/src/Microsoft.Extensions.Testing.Abstractions/Test.cs)ごとに、TestDiscovery.TestFound を送信します (その後、アダプターに転送されます)。
3. すべてのテストが検出されると、ランナーは TestRunner.Completed メッセージを dotnet テストに送信します。これを `dotnet test` は TestDiscovery.Completed としてアダプターに送信します。
4. アダプターが完了すると、`dotnet test` に TestSession.Terminate を送信します。これで `dotnet test` はシャットダウンします。



<!--HONumber=Feb17_HO2-->


