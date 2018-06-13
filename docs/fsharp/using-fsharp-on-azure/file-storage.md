---
title: F# を使用して Azure File storage の概要します。
description: クラウド内の Azure File storage の場合は、ファイル データを格納およびから Azure の仮想マシン (VM) クラウドのファイル共有をマウントまたは内部設置型アプリケーションから Windows を実行します。
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569344"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>F# を使用して Azure File storage の概要します。 #

Azure のファイル ストレージが標準を使用して、クラウド内のファイル共有を提供するサービスで[サーバー メッセージ ブロック (SMB) プロトコル](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)です。 SMB 2.1 と SMB 3.0 の両方がサポートされます。 Azure File storage では、迅速かつ高コストの再作成せずに、Azure へのファイル共有に依存するレガシ アプリケーションを移行できます。 Azure の仮想マシンまたはクラウド サービスや内部設置型のクライアントを実行しているアプリケーションは、デスクトップ アプリケーションの一般的な SMB 共有のマウントと同様に、クラウド内のファイル共有をマウントできます。 アプリケーション コンポーネントの任意の数をマウントし、同時にファイル記憶域共有にアクセスします。

ファイル ストレージの概念的概要についてを参照してください[ファイル記憶域として .NET ガイド](/azure/storage/storage-dotnet-how-to-use-files)です。

## <a name="prerequisites"></a>必須コンポーネント

このガイドを使用するのにはまず[Azure ストレージ アカウントを作成する](/azure/storage/storage-create-storage-account)です。
ストレージ アクセス キーは、このアカウントにも必要です。

## <a name="create-an-f-script-and-start-f-interactive"></a>作成、f# スクリプトと開始 f# 対話型

この記事のサンプルは、F# でアプリケーションまたは f# スクリプトで使用できます。 F# スクリプトを作成するを持つファイルを作成、`.fsx`拡張子、たとえば`files.fsx`、f# 開発環境でします。

次に、使用、[パッケージ マネージャー](package-management.md)など[パケットを作成](https://fsprojects.github.io/Paket/)または[NuGet](https://www.nuget.org/)をインストールする、`WindowsAzure.Storage`パッケージと参照`WindowsAzure.Storage.dll`を使用して、スクリプトで`#r`ディレクティブです。

### <a name="add-namespace-declarations"></a>名前空間の宣言を追加します。

次の追加`open`ステートメントの先頭に、`files.fsx`ファイル。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>接続文字列を取得します。

このチュートリアルでは、Azure ストレージ接続文字列を必要があります。 接続文字列の詳細については、次を参照してください。[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)です。

このチュートリアルでは、スクリプトでは、次のように、接続文字列を入力します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

ただし、これは**しないで**実際のプロジェクトです。 ストレージ アカウント キーは、ストレージ アカウントのルート パスワードに似ています。 常に、ストレージ アカウント キーを保護するように注意します。 ハード コーディング、または他のユーザーにアクセスできるプレーン テキスト ファイルに保存して他のユーザーに配布しないでください。 侵害されていると思われる場合は、Azure ポータルを使用して、キーを再生成することができます。

実際のアプリケーションは、ストレージの接続文字列を維持するために最適な方法は、構成ファイルでです。 構成ファイルから接続文字列をフェッチするには、は、これを行うことができます。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure 構成マネージャーを使用することはオプションです。 .NET Framework のなどの API を使用することも`ConfigurationManager`型です。

### <a name="parse-the-connection-string"></a>接続文字列を解析します。

接続文字列を解析するには、次のコマンドを使用します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

これは、戻り値は、`CloudStorageAccount`です。

### <a name="create-the-file-service-client"></a>ファイル サービス クライアントを作成します。

`CloudFileClient`型では、ファイル ストレージに格納されているファイルをプログラムで使用することができます。 サービス クライアントを作成する方法の 1 つを次に示します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

ファイル記憶域にデータを読み書きするコードを記述する準備が整いました。

## <a name="create-a-file-share"></a>ファイル共有を作成します。

この例が既に存在しない場合は、ファイル共有を作成する方法を示します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>ルート ディレクトリとサブディレクトリを作成します。

ここでは、ルート ディレクトリを取得し、ディレクトリ、ルートのサブディレクトリを取得します。 まだ存在しない場合は、両方ともタイプを作成します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>テキストをファイルとしてアップロードします。

この例では、テキストとしてファイルをアップロードする方法を示します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>ファイルをダウンロードするファイルのローカル コピーする

先ほど作成したファイルをダウンロードするここで、ローカル ファイルに内容を追加します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>ファイル共有の最大サイズを設定します。

次の例では、共有の現在の使用状況を確認する方法と、共有のクォータを設定する方法を示します。 `FetchAttributes` 共有の設定を呼び出す必要があります`Properties`、および`SetProperties`Azure File storage にローカルの変更を反映します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>ファイルまたはファイル共有の共有アクセス署名を生成します。

ファイル共有または個々 のファイルの共有アクセス署名 (SAS) を生成することができます。 共有アクセス署名を管理するファイル共有上の共有アクセス ポリシーを作成することもできます。 共有アクセス ポリシーを作成する、推奨されてを侵害する必要がある場合に、SAS を取り消す手段を提供します。

共有を作成するここでは、共有上のポリシーにアクセスし、そのポリシーを使用して、共有のファイルの SAS の制約を指定します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

詳細については、作成して、共有アクセス署名を使用して、次を参照してください。[を使用して共有アクセス署名 (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1)と[作成して使用して Blob ストレージの SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2)です。

### <a name="copy-files"></a>ファイルのコピー

ファイルを別のファイルまたは blob または blob にファイルをコピーできます。 ファイル、または、blob にファイルを blob をコピーしている場合、*必要があります*同じストレージ アカウント内にコピーする場合でも、ソース オブジェクトの認証に shared access signature (SAS) を使用します。

### <a name="copy-a-file-to-another-file"></a>別のファイルにファイルをコピーします。

ここでは、同じ共有内の別のファイルにファイルをコピーします。 このコピー操作は、同じストレージ アカウント内のファイル間でコピーするので、コピーを実行するのに共有キー認証を使用することができます。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>ファイルを blob にコピーします。

ここで、ファイルを作成し、同じストレージ アカウント内の blob にコピーします。 コピー操作中にソース ファイルへのアクセスを認証するサービスを使用するソース ファイルの SAS を作成します。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

同じ方法でファイルに blob をコピーできます。 ソース オブジェクトが blob の場合は、コピー操作中にその blob へのアクセスの認証に SAS を作成します。

## <a name="troubleshooting-file-storage-using-metrics"></a>メトリックを使用してファイルの記憶域のトラブルシューティング

Azure Storage Analytics は、ファイル ストレージのメトリックをサポートします。 メトリック データと要求のトレースし、問題を診断できます。

ファイル ストレージのメトリックを有効にすることができます、 [Azure Portal](https://portal.azure.com)、または次のように F# から行うことができます。

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>次の手順

Azure File storage の詳細については、これらのリンクを参照してください。

### <a name="conceptual-articles-and-videos"></a>概念に関する記事やビデオ

- [Windows と Linux の azure のファイル ストレージ: 摩擦のないクラウド SMB のファイル システム](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Linux で Azure File Storage を使用する方法](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>ツールのファイル記憶域のサポート

- [Azure ストレージで Azure PowerShell の使用](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Storage で AzCopy を使用する方法](/azure/storage/storage-use-azcopy)
- [Azure ストレージと Azure CLI を使用します。](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>参照

- [参照を .NET 用 storage クライアント ライブラリ](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [ファイル サービス REST API リファレンス](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>ブログの投稿

- [Azure のファイル ストレージが一般的に使用できるようになりました](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Azure 内のファイル ストレージ](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Microsoft Azure ファイル サービスの概要](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Microsoft Azure ファイルへの接続を保持します。](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
