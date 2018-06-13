---
title: F# を使用して Azure Blob ストレージの概要します。
description: Azure Blob ストレージとクラウドには、非構造化データを格納します。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 3ab08154bd374896fce777c7c373204c9048b65c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576156"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F# を使用して Azure Blob ストレージの概要します。 #

Azure BLOB Storage は、非構造化データをオブジェクト/BLOB としてクラウドに格納するサービスです。 Blob Storage は、ドキュメント、メディア ファイル、アプリケーション インストーラーなど、任意の種類のテキストまたはバイナリ データを格納できます。 Blob Storage は、オブジェクト ストレージとも呼ばれます。

この記事では、Blob ストレージを使用した共通タスクを実行する方法を示します。 サンプルは、.NET 用 Azure ストレージ クライアント ライブラリを使用して f# を使用して書き込まれます。 対象タスクには、アップロード、一覧表示、ダウンロード、および blob を削除する方法が含まれます。

Blob ストレージの概念的概要については、次を参照してください。 [blob ストレージは、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs)です。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。 このアカウントのストレージ アクセス キーも必要があります。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成、f# スクリプトと開始 f# 対話型

この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。 F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`blobs.fsx`、f# 開発環境でします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`と`Microsoft.WindowsAzure.ConfigurationManager`パッケージと参照`WindowsAzure.Storage.dll`と`Microsoft.WindowsAzure.Configuration.dll` 、スクリプトを使用して、`#r`ディレクティブです。

### <a name="add-namespace-declarations"></a>名前空間の宣言を追加します。

次の追加`open`ステートメントの先頭に、`blobs.fsx`ファイル。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルでは、Azure ストレージ接続文字列を必要とします。 接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。

このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

ただし、これは**しないで**実際のプロジェクトです。 ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。 構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure 構成マネージャーを使用することはオプションです。 .NET Framework のなどの API を使用することも`ConfigurationManager`型です。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のコマンドを使用します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

これを返します、`CloudStorageAccount`です。

### <a name="create-some-local-dummy-data"></a>ローカル ダミー データの一部を作成します。

開始する前に、スクリプトのディレクトリにダミーのローカル データの一部を作成します。 後でこのデータをアップロードします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob サービス クライアントを作成します。

`CloudBlobClient`型では、コンテナーと Blob ストレージに格納された blob を取得することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Blob ストレージからデータを読み書きするコードを記述する準備が整いました。

## <a name="create-a-container"></a>コンテナーを作成します。

この例が既に存在しない場合は、コンテナーを作成する方法を示します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

既定では、新しいコンテナーがプライベート、つまり、このコンテナーから blob をダウンロードするストレージ アクセス キーを指定する必要があります。 すべてのユーザーに、コンテナー内のファイルを使用できるようにする場合は、次のコードを使用して公開するコンテナーを設定できます。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

インターネット上のだれも、パブリック コンテナー内の blob を参照してくださいが、変更したり、適切なアカウント アクセス キーまたは共有アクセス署名がある場合にのみ、それらを削除します。

## <a name="upload-a-blob-into-a-container"></a>Blob コンテナーをアップロードします。

Azure Blob ストレージには、ブロック blob とページ blob がサポートしています。 ほとんどの場合、ブロック blob は、推奨される型を使用します。

ブロック blob にファイルをアップロードするには、コンテナーの参照を取得し、ブロック blob 参照を取得するを使用します。 Blob の参照を作成したらにアップロードできる任意のデータのストリームに呼び出すことによって、`UploadFromFile`メソッドです。 この操作は、しなかった以前存在、または存在する場合は上書きしますか場合、blob を作成します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>コンテナー内の blob を一覧表示します。

コンテナー内の blob を一覧表示するには、コンテナー参照をまず取得します。 コンテナーを使用することができますし、 `ListBlobs` blob やその中のディレクトリを取得します。 豊富なプロパティと、返されるためのメソッドにアクセスする`IListBlobItem`にキャストする必要があります、 `CloudBlockBlob`、 `CloudPageBlob`、または`CloudBlobDirectory`オブジェクト。 型が不明な場合は、キャストを決定するため、型チェックを使用できます。 次のコードを取得し、内の各項目の URI を出力する方法を示しています、`mydata`コンテナー。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

名前の blob パスについては、名前にすることもできます。 これにより、整理したり、従来のファイル システムと同様に走査できる仮想ディレクトリ構造が作成されます。 ディレクトリ構造は、仮想のみ - Blob ストレージで使用できる唯一のリソースがコンテナーと blob ことに注意してください。 ただし、ストレージ クライアント ライブラリが用意されています、`CloudBlobDirectory`仮想ディレクトリを参照し、この方法で構成されている blob を操作するプロセスを簡略化するオブジェクト。

たとえば、次の一連のという名前のコンテナーにブロック blob `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

呼び出すと`ListBlobs`(上記のサンプル) のように、コンテナー階層の一覧が返されます。 両方が含まれている場合`CloudBlobDirectory`と`CloudBlockBlob`結果の出力は次のように検索し、ディレクトリと、コンテナー内の blob をそれぞれ表すオブジェクト。

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

必要に応じて、設定することができます、`UseFlatBlobListing`のパラメーター、`ListBlobs`メソッドを`true`です。 この場合、コンテナー内のすべての blob として返されます、`CloudBlockBlob`オブジェクト。 呼び出し`ListBlobs`を次のようなフラット リストを返します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

また、結果は次のように、表示、コンテナーの現在の内容に応じて。

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a>Blob をダウンロードします。

Blob をダウンロードするには、最初に blob の参照を取得およびを呼び出す、`DownloadToStream`メソッドです。 次の例では、 `DownloadToStream` blob の内容をローカル ファイルに永続化することができますし、ストリーム オブジェクトに転送する方法です。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

使用することも、`DownloadToStream`メソッドを文字列として blob のコンテンツをダウンロードします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Blob を削除します。

Blob を削除するには、まず blob 参照を取得しを呼び出す、`Delete`メソッドです。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>非同期的にページ内の blob を一覧表示します。

Blob の数が多い一覧を作成する、または 1 つの一覧作成操作で返す結果の数を制御する場合、結果のページ内の blob を一覧表示できます。 この例は、大量の結果セットを返すを待機中に実行がブロックされていないようにに非同期的に、ページに結果を返す方法を示します。

この例は、この一覧を表示するには、フラットな blob を示していますが、設定して、階層的な一覧についてを実行することも、`useFlatBlobListing`のパラメーター、`ListBlobsSegmentedAsync`メソッドを`false`です。

サンプルは、非同期メソッドを定義を使用して、`async`ブロックします。 ``let!``キーワードは、一覧のタスクが完了するまでに、サンプル メソッドの実行を中断します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

次のようにこの非同期ルーチンここで使用できます。 最初に、ダミー データ (このチュートリアルで以前に作成されたローカル ファイルを使用) をアップロードします。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

ここで、ルーチンを呼び出します。 使用する``Async.RunSynchronously``非同期操作の実行を強制します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>追加 blob への書き込み

追加 blob には、ログ記録などの追加操作は適しています。 ブロック blob と同様に、追加 blob は、ブロックで構成が blob の末尾に追加されます常に、追加 blob に新しいブロックを追加するとき。 更新するか、追加 blob に既存のブロックを削除することはできません。 ブロック blob には、追加 blob のブロック Id は公開されません。

追加 blob 内の各ブロックは、最大 4 MB は、他のサイズを指定でき、追加 blob は最大 50,000 ブロックを含めることができます。 追加 blob の最大サイズよりも少し 195 GB (4 MB X 50,000 ブロック) ではこのためです。

次の例では、追加して、新しい blob を作成し、単純なログ記録操作をシミュレートする、いくつかのデータを追加します。

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

参照してください[Understanding ブロック Blob、ページ Blob、および追加 Blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) blob の 3 つの種類の違いの詳細についてはします。

## <a name="concurrent-access"></a>同時実行のアクセス

使用することがサポートするには同時アクセスを blob に複数のクライアントまたは複数のプロセスのインスタンスから**Etag**または**リース**です。

* **Etag** -blob またはコンテナーが変更されたことで別のプロセスを検出する方法を提供

* **リース**-取得だけで、更新可能な書き込み、または一定の時間の blob へのアクセスを削除する方法を提供

詳細については、次を参照してください。[同時実行制御を管理する Microsoft Azure ストレージに](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/)です。

## <a name="naming-containers"></a>名前付けコンテナー

Azure ストレージ内のすべての blob は、コンテナー内に存在する必要があります。 コンテナーは、blob 名の一部を形成します。 たとえば、`mydata`これらのサンプル blob Uri 内のコンテナーの名前を指定します。

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

コンテナー名には、有効な DNS 名、次の名前付け規則に準拠している必要があります。

1. コンテナー名は文字または数字で始める必要があり、文字、数字、およびダッシュ (-) 文字のみを含めることができます。
1. すべてのダッシュ (-) 文字必要があります直前および後にアルファベットまたは数字です。コンテナー名では、連続するダッシュ文字は使用できません。
1. コンテナー名のすべての文字を小文字にする必要があります。
1. コンテナー名は 3 ~ 63 文字の長さでなければなりません。

コンテナーの名前が小文字で常にする必要がありますに注意してください。 コンテナー名に、大文字を含めるか、それ以外の場合、コンテナーの名前付け規則に違反した場合 400 (Bad Request) エラーが発生する可能性があります。

## <a name="managing-security-for-blobs"></a>Blob のセキュリティを管理します。

既定では、Azure ストレージ データを維持、セキュリティで保護されたアカウント アクセス キーを所有しているであるアカウント所有者へのアクセスを制限することによってです。 ストレージ アカウント内の blob データを共有する必要がある場合、アカウント アクセス キーのセキュリティを損なうことがなくこれを行う必要があります。 さらに、ネットワーク経由でと Azure ストレージに安全であることを確認する blob データを暗号化できます。

### <a name="controlling-access-to-blob-data"></a>Blob データへのアクセスを制御

既定では、ストレージ アカウント内の blob データはストレージ アカウント所有者にのみアクセスできます。 Blob ストレージに対する要求を認証すると、既定では、アカウント アクセス キーが必要です。 ただし、他のユーザーに特定の blob データを使用できるようにすることができます。

Blob ストレージへのアクセスを制御する方法の詳細については、「[アクセス制御の blob ストレージ セクションについては、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data)です。


### <a name="encrypting-blob-data"></a>Blob データの暗号化

Azure ストレージでは、クライアントとサーバーの両方の blob データの暗号化をサポートします。

Blob データの暗号化の詳細については、「[暗号化を blob ストレージのセクションでは、.NET ガイド](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data)です。

## <a name="next-steps"></a>次の手順

これで、Blob ストレージの基本を学習した次の詳細については、これらのリンク。

### <a name="tools"></a>ツール
- [F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)の f# 型プロバイダー Blob、テーブルおよびキューの Azure ストレージの資産を探索し、それらに対する CRUD 操作を簡単に適用するために使用できます。
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)用 Microsoft Azure テーブル ストレージ サービスを使用して、f# API
- [Microsoft Azure ストレージ エクスプ ローラー (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)は free、スタンドアロンのアプリから Microsoft Windows、OS X、Linux で、Azure ストレージのデータを視覚的に処理することができます。

### <a name="blob-storage-reference"></a>Blob ストレージのリファレンス

- [.NET 用 azure ストレージ Api](/dotnet/api/overview/azure/storage)
- [Azure ストレージ サービス REST API リファレンス](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>関連ガイド

- [C# での Azure Blob ストレージの概要](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows 上の AzCopy コマンド ライン ユーティリティでのデータを転送します。](/azure/storage/common/storage-use-azcopy)
- [Linux 上の AzCopy コマンド ライン ユーティリティでのデータを転送します。](/azure/storage/common/storage-use-azcopy-linux)
- [Azure ストレージ接続文字列を構成します。](/azure/storage/common/storage-configure-connection-string)
- [Azure ストレージ チーム ブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
