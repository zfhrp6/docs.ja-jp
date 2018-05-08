---
title: Azure での F# の使用
description: F# での Azure サービスの使用の概要します。
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 9a6e384874426584a19e1dc83a35c3f80e59537a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-f-on-azure"></a>Azure での F# の使用

F# は卓越したクラウド プログラミング言語であり、Web アプリケーション、クラウド サービス、クラウドでホストされるマイクロ サービスの作成、および拡張性の高いデータの処理に頻繁に使用されます。

次のセクションでは、広範囲の Azure サービスで F# を使用する方法に関するリソースを紹介します。

> [!NOTE]
> 特定の Azure サービスがこのドキュメント セットに記載されていない場合、そのサービスの Azure Functions または .NET のドキュメントを参照してください。 言語に依存しない言語固有のドキュメントを必要としない一部の Azure サービスはここに記載されていません。

## <a name="using-azure-virtual-machines-with-f"></a>F# で Azure の仮想マシンの使用 #

Azure では、さまざまな仮想マシン (VM) の構成をサポートします。[Linux および Windows の仮想マシン](https://azure.microsoft.com/services/virtual-machines/)に関するページを参照してください。

実行、コンパイル、スクリプト作成のために F# をインストールするには、「[Using F# on Linux](http://fsharp.org/use/linux)」(Linux での F# の使用) および「[Using F# on Windows](http://fsharp.org/use/windows)」(Windows での F# の使用) を参照してください。


## <a name="using-azure-functions-with-f"></a>F# による Azure 関数の使用 #

[Azure Functions](https://azure.microsoft.com/services/functions/) を使用すると、クラウドで小さなコードの集まりまたは "関数" を簡単に実行できます。 問題を解決するために必要なコードのみを手元で作成することができます。アプリケーション全体またはコードを実行するためのインフラストラクチャについて心配する必要はありません。 関数は、Azure ストレージおよびその他のクラウドでホストされるリソースでイベントに接続されます。 データは、関数の引数を使用して F# 関数に渡されます。 必要に応じて任意の開発言語を使用し、スケールを Azure に任せることができます。

Azure Functions は、F# を第一級の言語としてサポートし、F# コードを効率と拡張性に優れた方法で事後対応型で実行します。 Azure Functions で F# を使用する方法のリファレンス ドキュメントについては、「[Azure Functions F# 開発者向けリファレンス](/azure/azure-functions/functions-reference-fsharp)」を参照してください。

Azure Functions と F# の使用に関する他のリソース:

* [Suave を使用した F# での Azure Functions のスケールアップ](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [F# で Azure 関数を作成する方法](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Azure の関数で、Azure の型プロバイダーの使用](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>F# での Azure ストレージの使用 #

Azure Storage は、顧客のニーズに合う耐久性、可用性、スケーラビリティを必要とする最新のアプリケーション向けのストレージ サービスの基本階層です。 F# プログラムは、次の記事で説明されている方法を使用して、Azure Storage サービスと直接やり取りできます。

* [F# を使用した Azure Blob Storage の概要](blob-storage.md)
* [F# を使用した Azure File Storage の概要](file-storage.md)
* [F# を使用した Azure Queue Storage の概要](queue-storage.md)
* [F# を使用した Azure Table Storage の概要](table-storage.md)

Azure Storage は、明示的な API 呼び出しではなく、宣言型の構成を使って Azure Functions と組み合わせても使用できます。 F# の例を含む「[Azure Functions における Storage BLOB のバインド](/azure/azure-functions/functions-bindings-storage)」を参照してください。

## <a name="using-azure-app-service-with-f"></a>F# で Azure App Service の使用 #

[Azure App Service](https://azure.microsoft.com/services/app-service/) は、クラウドまたはオンプレミスでどこにでもデータに接続する強力な Web アプリおよびモバイル アプリをビルドするためのクラウド プラットフォームです。

* [F# Azure Web API の例](https://github.com/fsprojects/azure-webapi-example)
* [Azure 上の web アプリケーションでの F# のホスト](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Azure HDInsight と F# での Apache Spark の使用

[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) は、大規模なデータ分析アプリケーションを実行するオープン ソースの処理のフレームワークです。 Azure では、Apache Spark は簡単かつ低コストで展開できます。 F# で、Spark 用の .NET API である [Mobius](https://github.com/Microsoft/Mobius) を使用して、Spark アプリケーションを開発します。

* [Mobius を使用した F# での Spark アプリケーションの実装](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Mobius を使用する F# Spark アプリケーションの例](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-cosmos-db-with-f"></a>F# での Azure Cosmos DB の使用 #

[Azure の Cosmos DB](https://azure.microsoft.com/services/cosmos-db)高可用性、世界各地に分散アプリのための NoSQL サービスです。

Azure Cosmos DB は、2 つの方法で f# を使用できます。

1. F# Azure 関数の作成に使用するに対応するためまたは Azure Cosmos DB コレクションへの変更が発生します。 参照してください[Azure 関数の Azure Cosmos DB バインド](/azure/azure-functions/functions-bindings-cosmosdb)、または
2. 使用して、 [SQL API を Azure Cosmos DB .NET SDK](/azure/cosmos-db/sql-api-sdk-dotnet)です。 関連のサンプルは、C# の場合です。

## <a name="using-azure-event-hubs-with-f"></a>F# での Azure Event Hubs の使用 #

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) は、Web サイト、アプリケーション、およびデバイスからのクラウド スケール テレメトリの取り込みを提供します。

Azure Event Hubs は、2 つの方法で F# で使用できます。

1. イベントによってトリガーされる F# Azure Functions を作成します。 「[Azure Functions における Event Hub のバインド](/azure/azure-functions/functions-bindings-event-hubs)」を参照してください。
2. または、[.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted) を使用します。 これらの例は C# であることに注意してください。

## <a name="using-azure-notification-hubs-with-f"></a>F# による Azure Notification Hubs の使用 #

[Azure Notification Hubs](/azure/notification-hubs/) は、任意のバックエンド (クラウドまたはオンプレミス) から任意のモバイル プラットフォームにモバイル プッシュ通知を送信するためのマルチプラット フォームに対応するスケール アウト プッシュ インフラストラクチャです。

Azure Notification Hubs は、2 つの方法で F# で使用できます。

1. 通知ハブに結果を送信する F# Azure Functions を作成します。 「[Azure Functions における通知ハブの出力バインド](/azure/azure-functions/functions-bindings-notification-hubs)」を参照してください。
2. または、[.NET SDK for Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/) を使用します。 これらの例は C# であることに注意してください。


## <a name="implementing-webhooks-on-azure-with-f"></a>Azure で f# Webhook を実装します。 #

[Webhook](https://en.wikipedia.org/wiki/Webhook)は、Web 要求によってトリガーされるコールバックです。 Webhook は、GitHub などのサイトでイベントを通知するために使用されます。 

[Azure Function F# と Webhook バインド](/azure/azure-functions/functions-bindings-http-webhook)を使用して、Webhook を F# で実装し、Azure でホストすることができます。します。

## <a name="using-webjobs-with-f"></a>F# による web ジョブの使用 #

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) は、オンデマンド、継続的、またはスケジュール指定の 3 つの方法で App Service Web アプリで実行できるプログラムです。

[F# Webjob の例](https://github.com/andredublin/fsharp-azure-webjob)

## <a name="implementing-timers-on-azure-with-f"></a>F# を使用した Azure にタイマーを実装します。 #

タイマーは、スケジュールに従って、1 回または定期的に呼び出し関数をトリガーします。

[Azure Function F# とタイマー トリガー](/azure/azure-functions/functions-bindings-timer)を使用して、タイマーを F# で実装し、Azure でホストすることができます。

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>F# スクリプトを使用した Azure リソースの展開と管理 #

Azure VM はプログラムで展開し、Microsoft.Azure.Management パッケージと API を使用して、F# スクリプトから管理します。 例については、「[.NET の管理ライブラリの概要](https://msdn.microsoft.com/library/dn722415.aspx)」と[Azure Resource Manager の使用](/azure/azure-resource-manager/resource-manager-deployment-model)に関するページを参照してください。

同様に、他の Azure リソースも同じコンポーネントを使用して、F# スクリプトから展開および管理できます。 たとえば、ストレージ アカウントを作成、Azure クラウド サービスを展開 Azure Cosmos DB インスタンスを作成および f# スクリプトから Azure 通知ハブをプログラムで管理します。

F# スクリプトを使用したリソースの展開および管理は、通常必要はありません。 たとえば、Azure リソースは JSON テンプレートの説明から直接展開することもでき、これをパラメーター化できます。 [Azure クイック スタート テンプレート](https://azure.microsoft.com/resources/templates/)などの例を含む[Azure Resource Manager テンプレート](/azure/azure-resource-manager/resource-manager-template-best-practices)を参照してください。

## <a name="other-resources"></a>その他のリソース

* [すべての Azure サービスのドキュメント](/azure/)
