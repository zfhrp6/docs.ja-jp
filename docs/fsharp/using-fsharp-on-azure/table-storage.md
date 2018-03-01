---
title: "F# を使用して Azure テーブル ストレージの概要します。"
description: "Azure テーブル ストレージ、NoSQL データ ストアを使用してクラウドに構造化データを格納します。"
keywords: "visual f#、f#、関数型プログラミングでは、.NET では、.NET Core では、Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 905374a60261b0c2a863edb956943d41ae80f04d
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a>F# を使用して Azure テーブル ストレージの概要します。 #

Azure テーブル ストレージは、クラウドで構造化された NoSQL データを格納するサービスです。 テーブル ストレージは、schemaless 設計により、キー/属性ストアです。 テーブル ストレージは schemaless であるためには、アプリケーションするの必要に応じて、データを適応させる簡単です。 データへのアクセスは、高速でコスト効果の高いアプリケーションのすべての種類です。 テーブル ストレージでは、コストと比べて著しく低く従来の SQL のようなデータのボリュームを通常します。

テーブル ストレージを使用して、web アプリケーション、アドレス帳、デバイス情報、およびサービスを必要とするメタデータの他の種類のユーザー データなどの柔軟なデータセットを格納することができます。 テーブルのエンティティの任意の数を格納することができ、ストレージ アカウントは、ストレージ アカウントの容量の上限に達するまで、テーブルの任意の数を含めることがあります。

### <a name="about-this-tutorial"></a>このチュートリアルについて

このチュートリアルでは、f# を作成してテーブルの削除し挿入、更新、削除、およびテーブル データのクエリを含む、Azure テーブル ストレージを使用した一般的なタスクを実行するコードを記述する方法を示します。

テーブル ストレージの概念的概要についてを参照してください[テーブル ストレージは、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-tables)

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。
ストレージ アクセス キーは、このアカウントにも必要です。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成、f# スクリプトと開始 f# 対話型

この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。 F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`tables.fsx`、f# 開発環境でします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。 Microsoft.Azure 名前空間を取得するために、'Microsoft.WindowsAzure.ConfigurationManager' に対して再度操作を行います。

### <a name="add-namespace-declarations"></a>名前空間の宣言を追加します。

次の追加`open`ステートメントの先頭に、`tables.fsx`ファイル。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルでは、Azure ストレージ接続文字列を必要があります。 接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。

このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

ただし、これは**しないで**実際のプロジェクトです。 ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。 構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Azure 構成マネージャーを使用することはオプションです。 .NET Framework のなどの API を使用することも`ConfigurationManager`型です。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のコマンドを使用します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

これは、戻り値は、`CloudStorageAccount`です。

### <a name="create-the-table-service-client"></a>Table サービス クライアントを作成します。

`CloudTableClient`クラスでは、テーブルおよびテーブル ストレージに格納されているエンティティを取得することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

テーブル ストレージへのデータを読み書きするコードを記述する準備が整いました。

## <a name="create-a-table"></a>テーブルを作成します。

この例では、存在しない場合、テーブルを作成する方法を示します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a>テーブルにエンティティを追加します。

継承する型を持つエンティティがある`TableEntity`です。 拡張できます`TableEntity`、好きなようには、型で*必要があります*パラメーターなしのコンス トラクターです。 両方があるプロパティのみ`get`と`set`は、Azure テーブルに格納されます。

エンティティのパーティションと行キーは、テーブル内のエンティティを一意に識別します。 同じパーティション キーを持つエンティティは、別のパーティション キーを持つものよりも高速に問い合わせることができますが、並列操作のスケーラビリティを高めるため、さまざまなパーティション キーを使用できます。

例を次に示します、`Customer`を使用して、`lastName`パーティション キーとして、`firstName`行キーとして。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

これで、追加、`Customer`テーブルにします。 作成するためには、`TableOperation`は、テーブルでを実行します。 この場合、作成する、`Insert`操作します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a>エンティティのバッチを挿入します。

エンティティのバッチは、1 回の書き込み操作を使用してテーブルに挿入できます。 バッチ操作では、操作を 1 回の実行にまとめることができますが、いくつかの制限。

- 更新を行うことができます、削除し、同じバッチ操作でを挿入します。
- バッチ操作では、最大 100 個のエンティティを含めることができます。
- すべてのエンティティのバッチ処理の同じパーティション キーが必要です。
- バッチ操作でクエリを実行することはできますが、バッチ内にのみ操作があります。

バッチ操作に 2 つの insert を結合する一部のコードを次に示します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a>パーティション内のすべてのエンティティを取得します。

クエリを実行するすべてのエンティティのパーティション内のテーブルを使用して、`TableQuery`オブジェクト。 ここでは、フィルター処理するエンティティ「排除」が、パーティション キーが。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

結果を印刷するようになりました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a>パーティション内のエンティティの範囲を取得します。

パーティション内のすべてのエンティティのクエリを実行しない場合は、行キー フィルターのパーティション キーのフィルタを組み合わせることによって、範囲を指定できます。 ここでは、使用する 2 つのフィルター「排除」パーティション内のすべてのエンティティを取得するのに、行キー (名) から始まり、文字、アルファベットでは、"M"より前です。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

結果を印刷するようになりました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a>1 つのエンティティを取得します。

特定の 1 つのエンティティを取得するクエリを記述することができます。 ここを使用する、`TableOperation`顧客「Larry 排除」を指定します。 コレクションは、代わりに戻る、`Customer`です。 テーブル サービスから 1 つのエンティティを取得する最も簡単な方法は、クエリで、パーティション キーと行キーの両方を指定します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

結果を印刷するようになりました。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a>エンティティを置き換えます

エンティティを更新するにテーブル サービスから取得、エンティティ オブジェクトを変更し、サービスを使用してテーブルに変更を保存、`Replace`操作します。 これにより、それが取得されてから、操作が失敗する場合、サーバー上のエンティティが変更された場合を除き、サーバーで、完全に置き換えられるエンティティです。 この失敗は、アプリケーション、その他のソースからの変更を誤って上書きしないようにします。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a>エンティティ挿入または置換

場合によっては、エンティティが存在するかどうか、テーブル内かがわからない。 それに格納されている現在の値が不要になった場合は、します。 使用することができます`InsertOrReplace`に、エンティティを作成するか、その状態に関係なく、存在する場合に置き換えます。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a>エンティティのプロパティのサブセットのクエリ

テーブル クエリでは、それらのすべてではなくエンティティからプロパティをいくつかを取得できます。 投影法と呼ばれる、この手法は、特に大規模なエンティティの場合、クエリのパフォーマンスを向上できます。 ここでは、のみ用の電子メール アドレスを使用して返す`DynamicTableEntity`と`EntityResolver`です。 このコードは、テーブル サービスでアカウントを使用している場合にのみが実行されるように、プロジェクションがローカル ストレージ エミュレーターでサポートされないことに注意してください。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a>ページ内のエンティティを非同期に取得します。

場合は、エンティティの数が多いお読みになっており、それらすべてで返されるを待機しているセグメント化されたクエリを使用するのではなく、取得した、それらを処理する場合します。 ここでは、結果は、非同期ワークフローを使用すると、豊富な結果が返されるを待っているときに実行がブロックされていないにページに返します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

今すぐ実行するこの計算に同期的に。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a>エンティティを削除します。

取得した後は、エンティティを削除できます。 同様に、エンティティを更新するには、取得した後、エンティティが変更された場合は失敗します。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a>テーブルを削除します。

ストレージ アカウントからテーブルを削除することができます。 削除されたテーブルは削除されるまでの期間の再作成に使用できなくなります。

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a>次の手順

これで、テーブル ストレージの基本を学習したより複雑な記憶域タスクについて学習するこれらのリンクに従います。

- [.NET 用 azure ストレージ Api](/dotnet/api/overview/azure/storage)
- [Azure ストレージの型プロバイダー](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure ストレージ チーム ブログ](https://blogs.msdn.microsoft.com/b/windowsazurestorage/)
- [Azure ストレージ接続文字列を構成します。](/azure/storage/common/storage-configure-connection-string)
- [.NET で Azure テーブル ストレージの概要](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
