---
title: F# を使用して Azure キュー ストレージの概要します。
description: Azure キューでは、アプリケーション コンポーネント間で信頼性の高い非同期メッセージングを提供します。 クラウドを単独でスケーリングのアプリケーション コンポーネントのメッセージングを有効します。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569419"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F# を使用して Azure キュー ストレージの概要します。 #

Azure キュー ストレージは、クラウド アプリケーションのコンポーネント間のメッセージングを提供します。 スケールのアプリケーションを設計するには、アプリケーション コンポーネントは多くの場合、切り離されて、それらを個別に拡張できるようにします。 キュー ストレージは、クラウド、デスクトップ、社内設置のサーバー、またはモバイル デバイスで実行されているかどうか、アプリケーション コンポーネント間の通信用の非同期メッセージングを提供します。 キュー ストレージには、非同期タスクを管理して、プロセスのワークフローの構築もサポートしています。

### <a name="about-this-tutorial"></a>このチュートリアルについて

このチュートリアルでは、Azure キュー ストレージを使用した一般的なタスクの f# コードを記述する方法を示します。 作成してキューを削除して追加する、読み取り、およびキューのメッセージを削除する、以下のタスクについて説明します。

キュー ストレージの概念的な概要を参照してください[キューを格納する .NET ガイド](/azure/storage/storage-dotnet-how-to-use-queues)です。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。
ストレージ アクセス キーは、このアカウントにも必要です。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成、f# スクリプトと開始 f# 対話型

この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。 F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`queues.fsx`、f# 開発環境でします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。

### <a name="add-namespace-declarations"></a>名前空間の宣言を追加します。

次の追加`open`ステートメントの先頭に、`queues.fsx`ファイル。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルでは、Azure ストレージ接続文字列を必要があります。 接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。

このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

ただし、これは**しないで**実際のプロジェクトです。 ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。 構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure 構成マネージャーを使用することはオプションです。 .NET Framework のなどの API を使用することも`ConfigurationManager`型です。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のコマンドを使用します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

これは、戻り値は、`CloudStorageAccount`です。

### <a name="create-the-queue-service-client"></a>キュー サービス クライアントを作成します。

`CloudQueueClient`クラスでは、キュー ストレージに格納されているキューを取得することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

キュー ストレージからデータを読み書きするコードを記述する準備が整いました。

## <a name="create-a-queue"></a>キューを作成します。

この例では、存在しない場合は、キューを作成する方法を示します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>キューにメッセージを挿入します。

既存のキューにメッセージを挿入するに最初に作成する新しい`CloudQueueMessage`です。 次に、呼び出し、`AddMessage`メソッドです。 A`CloudQueueMessage`から作成することか、形式の文字列 (utf-8) または`byte`次のように、配列。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>次のメッセージをピークする方法

呼び出すことによって、キューから削除することがなくキュー、前面のメッセージをピークすることができます、`PeekMessage`メソッドです。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>処理のため次のメッセージを取得します。

処理のため、キューの先頭にあるメッセージを取得するには呼び出すことによって、`GetMessage`メソッドです。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

使用して、メッセージを正常に処理を後で示す`DeleteMessage`です。

## <a name="change-the-contents-of-a-queued-message"></a>キューに置かれたメッセージの内容を変更します。

取得したメッセージ内の場所のキューに内容を変更することができます。 メッセージは、作業のタスクを表している場合は、作業タスクの状態を更新するこの機能を使用する可能性があります。 次のコードでは、新しいコンテンツを含むキューのメッセージを更新し、もう 1 つの 60 秒を拡張する表示タイムアウトを設定します。 これは、メッセージに関連付けられている作業の状態を保存し、により、クライアント メッセージで作業を続行する別の分。 ハードウェアまたはソフトウェアの障害により、処理手順が失敗した場合に、最初からやり直すことがなくキューのメッセージで複数のステップのワークフローを追跡するために、この手法を使用する可能性があります。 通常、同様に、再試行カウントを保持するができますし、削除は、メッセージが複数回を超える再試行された場合。 これは、アプリケーション エラーが処理されるたびにトリガーをメッセージから保護します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>次のメッセージをキューから削除

コード 2 つの手順で、キューからメッセージをキューします。 呼び出すと`GetMessage`キュー内の次のメッセージを取得します。 返されたメッセージ`GetMessage`このキューからメッセージを読み取るその他のコードを非表示になります。 既定では、このメッセージでは 30 秒間の非表示に維持されます。 完了するには、キューからメッセージを削除する必要がありますも呼び出す`DeleteMessage`です。 メッセージを削除するには、この 2 段階プロセスでは、コードは、ハードウェアまたはソフトウェアの障害によりメッセージの処理に失敗すると、コードの別のインスタンスは、同じメッセージを取得し、もう一度やり直してくださいことを保証します。 コードの呼び出し`DeleteMessage`直後に、メッセージが処理されました。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>非同期のワークフローを使用して、共通のキュー ストレージ Api

この例では、共通のキュー ストレージ Api の非同期ワークフローを使用する方法を示します。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>キューから取り出すメッセージの追加オプション

キューからメッセージの取得をカスタマイズする 2 つの方法はあります。
最初に、(最大 32 個) のメッセージのバッチを取得できます。 第二に、長いまたは短い非表示タイムアウトを設定する、詳細や、各メッセージを完全に処理にかかる時間が、コードを許可します。 次のコード例では`GetMessages`20 を取得する 1 つのメッセージを呼び出すし、それぞれのメッセージを処理します。 また、メッセージごとに 5 分間に非表示タイムアウトを設定します。 呼び出し以降後 5 分が経過している 5 分間は、同時にすべてのメッセージの開始を`GetMessages`、削除されていないすべてのメッセージが可視になります。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>キューの長さを取得します。

キュー内のメッセージの数の推定値を取得できます。 `FetchAttributes`メソッドは、メッセージ数など、キューの属性を取得するキュー サービスを確認します。 `ApproximateMessageCount`プロパティによって取得された最後の値を返します、`FetchAttributes`メソッドを呼び出さずに、キュー サービス。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>キューを削除します。

削除するキューとそれに含まれるすべてのメッセージを呼び出し、`Delete`キュー オブジェクトのメソッドです。

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>次の手順

キュー ストレージの基本を学習したようになりましたことはより複雑な記憶域タスクについて学習するこれらのリンクに従います。

- [.NET 用 azure ストレージ Api](/dotnet/api/overview/azure/storage)
- [Azure ストレージの型プロバイダー](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure ストレージ チーム ブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure ストレージ接続文字列を構成します。](/azure/storage/common/storage-configure-connection-string)
- [Azure ストレージ サービス REST API リファレンス](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
