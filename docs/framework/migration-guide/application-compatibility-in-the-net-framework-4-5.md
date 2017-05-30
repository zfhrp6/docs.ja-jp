---
title: ".NET Framework 4.5 のアプリケーションの互換性 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility, .NET Framework
- breaking changes [.NET Framework]
ms.assetid: 5c50747c-806c-44a9-ac58-5bbe12a284fa
caps.latest.revision: 76
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 5f63c3217b6def96240447501247d22a1058cacf
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="application-compatibility-in-the-net-framework-45"></a>.NET Framework 4.5 のアプリケーションの互換性
このトピックでは、修正や顧客フィードバックに基づく変更点など、.NET Framework 4 と 4.5 のアプリケーションの互換性に関する問題について説明します。 これらの変更点のほとんどは、アプリケーションのプログラミング変更を必要としません。 プログラミング変更が必要になる可能性のある変更点については、表の「影響」列を参照してください。  
  
> [!IMPORTANT]
>  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は [!INCLUDE[winxp](../../../includes/winxp-md.md)] ではサポートされないことに注意してください。  
  
 .NET Framework 4.5 と 4.5.1 間の互換性の問題については、「[4.5.1 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)」をご覧ください。  
  
 このトピックでは、次の分野の主な変更点について説明します。  
  
-   [コア](#core)  
  
-   [データ](#sql)  
  
-   [ネットワーク](#network)  
  
-   [シリアル化](#serialize)  
  
-   [印刷](#Printing)  
  
-   [ツールとリソース](#tools)  
  
-   [ASP.NET](#asp)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [MEF (Managed Extensibility Framework)](#mef)  
  
-   [Web アプリケーション](#web)  
  
-   [Windows Communication Foundation (WCF)](#wcf)  
  
-   [Windows フォーム](#winForms)  
  
-   [Windows Presentation Foundation (WPF)](#wpf)  
  
-   [Windows Workflow Foundation (WF)](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md#wwf)  
  
-   [XML、XSLT](#xml)  
  
 このトピックでは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]で廃止と宣言された型およびメンバーについては説明しません。 これらの一覧は、「[クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)」をご覧ください。 新しい機能の詳細については、「[新機能](../../../docs/framework/whats-new/index.md)」を参照してください。  
  
<a name="core"></a>   
## <a name="core"></a>コア  
 以下のアプリケーションの互換性の問題に加え、シリアル化に関連する問題について「[シリアル化](#serialize)」のセクションを参照してください。  
  
|特性|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName> メソッドおよび <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A?displayProperty=fullName> メソッド|<xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName> メソッドで -1 が返されたり、例外がスローされることがなくなりました。 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A?displayProperty=fullName> メソッドでは、コレクションの 1 つに完了のマークが付けられても例外がスローされることがなくなりました。|この変更の結果、コレクションの 1 つが空であったり完了していても、他のコレクションに取得できる項目がある場合にコレクションで作業をすることができるようになりました。|  
|<xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=fullName>|コンパイル済みの正規表現のアセンブリが [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] でビルドされ、 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]を対象としている場合、 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされているシステム上でそのアセンブリの正規表現の 1 つを使用しようとすると、例外をスローします。|この問題を回避するには、次のいずれかの方法を実行します。<br /><br /> [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使用して正規表現を含むアセンブリをビルドします。<br /><br /> 解釈される正規表現を使用します。|  
|<xref:System.Threading.Tasks.Task?displayProperty=fullName> の破棄|`Task.IAsyncResult.AsyncWaitHandle`を除き、<xref:System.Threading.Tasks.Task?displayProperty=fullName> メソッドでオブジェクトが破棄された後も <xref:System.ObjectDisposedException> の例外がスローされることがなくなりました。|この変更により、キャッシュされたタスクを使用できるようになりました。 たとえば、メソッドで新しいタスクを割り当てる代わりに、既に完了した操作を表す、キャッシュされたタスクを返すことができます。 これは、タスクの任意のコンシューマーによって破棄されてしまうと、使用不可能になってしまう以前の .NET Framework のバージョンでは不可能でした。|  
|<xref:System.Threading.Tasks.Task?displayProperty=fullName> 操作での無視された例外|<xref:System.Threading.Tasks.Task?displayProperty=fullName> クラスは非同期操作を表すため、非同期処理中に発生する重大ではない例外がすべてキャッチされます。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、例外が確認されておらず、コードがタスクを待機していない場合、例外がファイナライザー スレッドに反映されなくなり、ガベージ コレクションの実行時にプロセスがクラッシュします。|この変更により、<xref:System.Threading.Tasks.Task> クラスを使用して観察されていない非同期処理を実行するアプリケーションの信頼性が向上します。 以前の動作は <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> イベントに適切なハンドラーを指定することによって復元できます。|  
|タイムアウト引数を使用する <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=fullName> メソッド|[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]では、これらのメソッドは動作が矛盾していました。 タイムアウトの期限が切れたときに、メソッドを呼び出す前に完了した、またはキャンセルされたタスクが 1 つ以上ある場合、メソッドでは <xref:System.AggregateException> 例外がスローされていました。 タイムアウトの期限が切れたときに、メソッドを呼び出す前に完了した、またはキャンセルされたタスクがなく、メソッドを呼び出した後で 1 つ以上のタスクがこれらの状態になると、メソッドでは `false`が返されていました。<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、これらのメソッドはオーバーロードされ、タイムアウト期限が切れたときにいずれかのタスクが実行中の場合は `false` を返します。また、入力タスクが取り消された (メソッド呼び出しの前と後のどちらで取り消されたかに関わりなく) 場合、かつ、それ以外に実行中のタスクがない場合に限り、<xref:System.AggregateException> 例外をスローします。|この変更により、メソッドの動作が一貫します。 ただし、タイムアウトの期限が切れる前に少なくとも 1 つのタスクに障害が発生していたり、タスクがキャンセルされていた場合、アプリケーション コードが例外をスローするためにタイムアウト対応の <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=fullName> のオーバーロードに依存する可能性もわずかながらあります。 その場合は、<xref:System.Threading.Tasks.Task.IsCanceled%2A?displayProperty=fullName> プロパティを同じ目的で使用できます。|  
|複数バージョン対応時の型転送のサポート|新しい CodeDOM の機能を使用すると、mscorlib.dll の [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] バージョンではなく、mscorlib.dll の対象バージョンに対してコンパイルできるようになります。|この変更により、CodeDOM が型転送された 2 つの定義を見つけたときのコンパイラ警告 (および警告がエラーとして扱われる場合はコンパイル エラー) が防げるようになりました。 異なるバージョンの参照アセンブリが 1 つの場所に混在している場合にのみ、この変更によって意図しない副作用が生じることがあります。|  
|<xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=fullName>|コレクションの要素が変更されると、列挙子によって <xref:System.InvalidOperationException> の例外がスローされます。|この変更は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とするアプリケーションにのみ適用され、悪影響が及ぶことはありません。 データの整合性が保護され、競合状態を特定できる確率が高くなります。|  
|<xref:System.Uri?displayProperty=fullName>|International Resource Identifier (IRI) 解析に 2 つの変更を加えたことにより、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションの URI が影響を受けました。<br /><br /> [\<iriParsing>](../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md) は既定で有効になり、無効にすることはできません。 以前は、これは既定で無効になっていました。<br /><br /> URI の非ホスト部分では Unicode 正規化形式 C (NFC) が実行されなくなりました。 以前は、`<iriParsing>` が有効になっていると URI 全体に対して NFC が実行されていました。|NFC (正規化形式 C) ではない正規化されたファイル名が含まれる URI は、C という形式で正規化されません。 IRI 解析が正規化されていない文字列を使用して正規化されたファイル名を持つファイルにアクセスすると、アプリケーション エラーが発生する可能性があります。 これは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションにのみ影響します。|  
|<xref:System.Uri?displayProperty=fullName>|無効な `mailto:` URL では、<xref:System.Uri> クラスのコンストラクターで例外がスローされます。|これは再コンパイルされ、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象とするアプリケーションにのみ影響します。|  
|<xref:System.Uri?displayProperty=fullName>|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションでは、元の URI 文字列のパス セグメントの末尾のドット (たとえば `http://www.proseware.com/LLC./About.aspx`) が保持されます。 1 つまたは 2 つのドットから構成されるパス セグメント (たとえば、`http://www.proseware.com/..`、`http://www.proseware.com/./default.htm`) は削除されますが、3 つの以上連続するドットを持つパス セグメント (たとえば、`http://localhost/dir1/.../dir2`) は保持されます。|この変更は、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションにのみ影響します。 末尾のドットが削除されることに依存しているアプリケーションではエラーが発生する場合があります。|  
|<xref:System.Uri?displayProperty=fullName>|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションでは、 `file://` URI 内のクエリが許可されます。 文字 ? は、パスの一部として解釈されるため、エスケープされません。|この変更は、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションにのみ影響します。 文字 ? のエスケープに依存するアプリケーション では、エラーが発生する場合があります。|  
|<xref:System.Uri?displayProperty=fullName>|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションでは、Unicode 制御文字の U+0080 ～ U+009F が正確にエンコードされません。|通常、URI には Unicode 制御文字を使用しません。|  
|<xref:System.Uri.EscapeDataString%2A?displayProperty=fullName>、<xref:System.Uri.EscapeUriString%2A?displayProperty=fullName>、および <xref:System.Uri.UnescapeDataString%2A?displayProperty=fullName>|現在、予約されている文字と予約されていない文字の一覧では、[RFC 3986](http://tools.ietf.org/html/rfc3986) がサポートされています。|具体的な変更内容:<br /><br /> <xref:System.Uri.EscapeDataString%2A> は、予約されている文字を RFC 3986 に基づいてエスケープします。<br /><br /> <xref:System.Uri.EscapeUriString%2A> は、予約されている文字をエスケープしません。<br /><br /> <xref:System.Uri.UnescapeDataString%2A> は、無効なエスケープ シーケンスが発生した場合に例外をスローしません。<br /><br /> 予約されていないエスケープ文字はエスケープ解除されます。|  
|<xref:System.Uri.IsWellFormedUriString%2A?displayProperty=fullName>|.NET Framework 4.5 以降、文字列は常に [RFC 3986](http://tools.ietf.org/html/rfc3986) と [RFC 3987](http://tools.ietf.org/html/rfc3987)に従って適切な形式と見なされます。 .NET Framework の以前のバージョンでは、URI の解析および IDN 解析が有効である場合にのみ、文字列は RFC 3986 および RFC 3987 に従って適切な形式と見なされます。|.NET Framework 4.5 以降のバージョンを対象とするアプリの場合、このメソッドは、以前のバージョンの .NET Framework を対象とするアプリによって適切な形式と見なされた URI の `false` を返します。 たとえば、最初のセグメントにコロンが含まれる相対 URI ("2013.05.29_14:33:41" など) は、適切な形式と見なされません。<br /><br /> この変更は、.NET Framework 4.5 以降のバージョンを対象とするアプリのみに影響します。|  
|<xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName>|<xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName> は、<xref:System.IAsyncResult.CompletedSynchronously%2A?displayProperty=fullName> プロパティにアクセスできます。 <xref:System.IAsyncResult.CompletedSynchronously%2A?displayProperty=fullName> の間違った実装によって、<xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=fullName> メソッドの呼び出しで定義されていない動作が発生する可能性があります。|<xref:System.IAsyncResult.CompletedSynchronously%2A?displayProperty=fullName> プロパティの実装が誤って `true` を返すと、結果のタスクは完了しません。|  
  
<a name="sql"></a>   
## <a name="data"></a>データ  
  
### <a name="sqlclient"></a>SQLClient  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で実行されているマネージ コードから SQL Server データベースに接続できる機能。|既存の同期 API コード パスは、非同期サポートを追加するように変更されました。|IFS ではない Winsock ベース サービス プロバイダー (BSP) または複層階サービス プロバイダー (LSP) が、SQL Server に接続できる機能に干渉する可能性があります。 Microsoft サポートの Web サイトの「[SetFileCompletionNotificationModes API causes an IO completion port not work correctly with a non-IFS LSP installed](http://go.microsoft.com/fwlink/p/?LinkId=256032)」 (SetFileCompletionNotificationModes API が原因で、IFS ではない LSP がインストールされている場合に IO 完了ポートが正常に機能しない) を参照してください。|  
|<xref:System.Data.SqlClient.SqlConnection?displayProperty=fullName> 型|SQL Server 1997 データベースへの接続はサポートされなくなりました。|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で実行されているアプリケーションは SQL Server 1997 データベースに接続できません。|  
|<xref:System.Data.SqlClient.SqlConnection?displayProperty=fullName> 型|仮想インターフェイス アダプター (VIA) プロトコルを使用した SQL Server データベースへの接続はサポートされなくなりました。|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] で実行されているアプリケーションは、VIA を使用して SQL Server データベースに接続できません。|  
|<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> 型|データを列に挿入する場合、<xref:System.Data.SqlClient.SqlBulkCopy> は `VARCHAR` と `CHAR` の型の既定エンコードではなく、挿入先の列のエンコードを使用します。|この変更により、挿入先の列が既定のエンコードを使用しない場合に、既定のエンコードを使用することによって発生するデータ破損の可能性がなくなります。 まれに、エンコードに変更を加えることによって、挿入先の列に収まりきらない大きいデータが生成された場合に、既存のアプリケーションで <xref:System.Data.SqlClient.SqlException> の例外がスローされることがあります。|  
|<xref:System.Data.SqlClient?displayProperty=fullName>の照合順序|`sql_variant` データはデータベースの照合順序ではなく `sql_variant` の照合順序を使用します。|この変更により、データベースの照合順序が `sql_variant` の照合順序と異なる場合にデータ破損が生じる可能性に対応できます。 破損したデータに依存するアプリケーションでは、エラーが発生する場合があります。|  
  
### <a name="entity-framework"></a>Entity Framework  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Data.Objects.ObjectContext.CreateDatabase%2A?displayProperty=fullName> メソッドによって作成されるログ ファイル|<xref:System.Data.Objects.ObjectContext.CreateDatabase%2A> メソッドが、直接、または SqlClient プロバイダーと共に Code First と接続文字列の `AttachDBFilename` 値を使用して呼び出されると、*filename*.ldf ではなく *filename*_log.ldf という名前のログ ファイルが作成されます (*filename* は、`AttachDBFilename` 値で指定されたファイルの名前になります)。|この変更により、SQL Server の仕様に従ってログ ファイル名が提供されるため、デバッグ機能が向上します。 予期しない副作用はありません。|  
|データ定義言語 (DDL: Data Definition Language) API|`AttachDBFilename` を指定したときの DDL API の動作は次のように変更されました。<br /><br /> 接続文字列で `Initial Catalog` の値を指定する必要がなくなりました。 以前は、`AttatchDBFilename` と `Initial Catalog` の両方が必要でした。<br /><br /> `AttatchDBFilename` と `Initial Catalog` の両方が指定され、所定の MDF ファイルが存在する場合、<xref:System.Data.Objects.ObjectContext.DatabaseExists%2A?displayProperty=fullName> メソッドは `true`を返します。 以前は、`false`が返されていました。<br /><br /> `AttatchDBFilename` と `Initial Catalog` の両方が指定され、所定の MDF ファイルが存在する場合に、<xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> メソッドを呼び出すとファイルが削除されます。<br /><br /> 接続文字列で存在しない MDF の <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> 値および存在しない `AttachDBFilename` が指定されたときに `Initial Catalog` が呼び出されると、メソッドでは <xref:System.InvalidOperationException> 例外がスローされます。 以前は、<xref:System.Data.SqlClient.SqlException> の例外がスローされていました。|これらの変更により、DDL API を使用するアプリケーションおよびツールの構築が簡単になりました。 これらの変更は、次のシナリオでアプリケーションの互換性に影響を及ぼす可能性があります。<br /><br /> `DROP DATABASE` で <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> が返されたときに、<xref:System.Data.Objects.ObjectContext.DatabaseExists%2A?displayProperty=fullName> を呼び出す代わりに直接 `true` コマンドを実行するコードをユーザーが作成した場合。 データベースがアタッチされておらず、MDF ファイルが存在する場合、これによって既存のコードが破損します。<br /><br /> <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A?displayProperty=fullName> と MDF ファイルが存在しない場合に、<xref:System.Data.SqlClient.SqlException> 例外ではなく <xref:System.InvalidOperationException> 例外をスローするように、`Initial Catalog` メソッドを要求するコードをユーザーが作成した場合。|  
|<xref:System.Data.Objects.ObjectContext.CreateDatabase%2A?displayProperty=fullName> メソッドおよび <xref:System.Data.Common.DbProviderServices.CreateDatabase%2A?displayProperty=fullName> メソッド|空のデータベースを作成した後にデータベース オブジェクトの作成が失敗した場合、メソッドはデータベースの作成を削除して、元の <xref:System.Data.SqlClient.SqlException> 例外を反映させます。 データベースの削除に失敗すると、メソッドは <xref:System.InvalidOperationException> 例外をスローします。|この変更により、空の使用不可能なデータベースが作成できなくなります。 例外処理は、データベースを正常に削除することによって元の <xref:System.Data.SqlClient.SqlException> 例外が反映されるため、多少変更されます。|  
|<xref:System.Data.Objects.ObjectContext.Translate%2A?displayProperty=fullName> メソッドおよび <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%2A?displayProperty=fullName> メソッド|`T` が列挙型の場合、メソッドは正しくデータベースからデータを返します。  以前は、列挙体の型がサポートされていなかったため、結果は常にゼロにキャストされるか、列挙型に変換されていました。 <xref:System.UInt16>、<xref:System.UInt32> および <xref:System.UInt64> など、Entity Framework によってサポートされていない基になる型では、従来どおりゼロが返されたり、基の値がゼロの列挙型に変換されたりします。|列挙型のサポートは [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]の Entity Framework で新たに追加されました。 ただし、開発者コードがゼロになる結果に依存している場合は、特定のコードによってはアプリケーション エラーが生じることがあります。|  
  
### <a name="linq"></a>LINQ  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Linq.Enumerable.Empty%2A?displayProperty=fullName> メソッド|メソッドは新しい <xref:System.Collections.Generic.IEnumerable%601> 型を返さず、代わりにキャッシュされた内部インスタンスを返します。|この変更により、パフォーマンスが改善されました。 ただし、複数の呼び出しから <xref:System.Linq.Enumerable.Empty%2A?displayProperty=fullName> まで 2 つの一意の空の型を取得しなければならないコードは失敗します。|  
  
<a name="network"></a>   
## <a name="networking"></a>ネットワーキング  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName> 名前空間の型とメンバー|[!INCLUDE[win8](../../../includes/win8-md.md)]ではこの型とメンバーはサポートされていません。 呼び出そうとすると、<xref:System.PlatformNotSupportedException> の例外がスローされます。|アプリケーションは、[!INCLUDE[win8](../../../includes/win8-md.md)]でこれらの型とメンバーを使用できません。|  
|<xref:System.Net.Mail.MailMessage> オブジェクトのシリアル化と逆シリアル化。|.NET Framework 4.5 では、メール メッセージに非 ASCII 文字を含めることができます。 .NET Framework 4 では、ASCII 文字しかサポートされていません。|非 ASCII 文字が含まれ、.NET Framework 4.5 でシリアル化された <xref:System.Net.Mail.MailMessage> オブジェクトは、.NET Framework 4 で逆シリアル化することはできません。|  
  
<a name="Printing"></a>   
## <a name="printing"></a>印刷  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Printing.PrintSystemJobInfo.JobStream%2A?displayProperty=fullName>|このプロパティは、印刷ジョブのストリームを公開し、ユーザーがこのストリームに書き込むことによって、基になるオペレーティング システムの印刷コンポーネントに生データを送信できるようにします。<br /><br /> .NET Framework 4.5 以降、Windows 8 より後のバージョンの Windows オペレーティング システムでは、このストリームに書き込むデータは XPS 形式のパッケージ ストリームにする必要があります。|印刷内容を出力するには、次のいずれかの操作を行います。<br /><br /> <xref:System.Windows.Xps.XpsDocumentWriter> クラスを使用して印刷内容を出力します。 これが、推奨される方法です。<br /><br /> <xref:System.Printing.PrintSystemJobInfo.JobStream%2A?displayProperty=fullName> プロパティによって返されるストリームに送信されるデータを、XPS 形式のパッケージ ストリームにします。|  
  
<a name="serialize"></a>   
## <a name="serialization"></a>シリアル化  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Xml.Serialization.XmlSerializer> クラスを使用したシリアル化|WCF 4.5 では、<xref:System.Xml.Serialization.XmlSerializer> クラスは、C# コンパイラへの依存関係を削除するように最適化されています。 この変更により、コールド起動シナリオのパフォーマンスが著しく向上します。|この変更により、WCF 4 でコンパイルされ、WCF 4.5 に対して実行される XML シリアル化のコードで問題が発生する可能性があります。 WCF 4.5 で既存の XML シリアル化コードの実行時に問題が発生した場合は、次の構成要素を使用して、WCF 4 の XmlSerializer の動作に戻します。<br /><br /> `<configuration>    <system.xml.serialization>    <xmlSerializer useLegacySerializerGeneration="true"/>    </system.xml.serialization> </configuration>`|  
|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=fullName> クラスによるシリアル化と逆シリアル化|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> を使用したシリアル化では、オブジェクトの内部状態をエンコードすることができます。この内部状態は、.NET Framework のバージョン間で同じであるとは限りません。  相違がある場合、.NET Framework の 1 つのバージョンでシリアル化されたコンテンツは他のバージョンで逆シリアル化できません。|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> クラスについては、バージョン間の互換性が保証されません。 代わりに、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> クラスおよび <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=fullName> クラスを使用してください。|  
  
<a name="tools"></a>   
## <a name="tools-and-resources"></a>ツールとリソース  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|MSBuild|コマンド プロンプトで MSBuild を実行すると、特定のプロジェクトのビルドを無効にするソリューション構成ファイルが考慮されます。|MSBuild は、Visual Studio で呼び出された場合もコマンド プロンプトで実行された場合も同じように動作します。 別のソリューションを作成したり、ソリューションからプロジェクトを削除して、ソリューションにプロジェクトのサブセットを作成する必要はありません。|  
|MSBuild|MSBuild プロジェクト ファイルの `TreatAsLocalProperty` プロパティでは、`OutDir` プロパティなどの特定のプロパティがグローバル レベルでオーバーライドされるのを防ぎます。|`OutDir` プロパティをオーバーライドすると、`OutDir` が MS.Common.Targets ファイルがインポートされた後でオーバーライドされたグローバル プロパティだったときに壊れる可能性があります。|  
|Windows エラー レポート: Watson バケット|マネージ クラッシュはいくつかの条件に基づいてカテゴリに分類されていますが、そのうちの 1 つはアセンブリ バージョンでした。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、アセンブリ バージョンではなくファイルのバージョンが使用されます。|アセンブリのバージョン変更はメジャー リリース間でのみ行われるため、アセンブリのバージョンではなくファイルのバージョンをカテゴリに使用すると、マネージ クラッシュに関係したアセンブリの特定のバージョンを判断できるようになります。|  
|MSBuild|<xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=fullName> コレクションのプロジェクトからのデータは、ガベージ コレクターにより自動的には解放されません。|プロジェクトを明示的に <xref:Microsoft.Build.Evaluation.ProjectCollection> コレクションへ読み込む場合、コレクションの各メンバーに対して <xref:Microsoft.Build.Evaluation.ProjectCollection.UnloadProject%28Microsoft.Build.Evaluation.Project%29> メソッドを呼び出す必要があります。|  
  
<a name="asp"></a>   
## <a name="aspnet"></a>ASP.NET  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|ASP.NET IIS 登録ツール (aspnet_regiis.exe)|[!INCLUDE[win8](../../../includes/win8-md.md)] では、ASP.NET のインストールとアンインストールを実行する `–i` オプションと `–u` オプションはサポートされません。|IIS 8 を使用して ASP.NET 4.5 をインストールまたはアンインストールするには、**[Windows 機能の有効化または無効化]** ダイアログ ボックス、サーバー管理ツール、または `dism.exe` コマンド ライン ツールを使用します。|  
|<xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> コントロール|<xref:System.Web.UI.Page.LoadComplete?displayProperty=fullName> イベントが原因で、<xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> のコントロールがパラメーターの作成/更新/削除に変更を加えるためにデータ バインディングを呼び出すことがなくなりました。|この変更により、データベースへの不要なアクセスが排除され、コントロールの値がリセットされるのを防ぐことができるほか、<xref:System.Web.UI.WebControls.SqlDataSource> や <xref:System.Web.UI.WebControls.ObjectDataSource>などのように他のデータ コントロールと一貫性の取れた動作が生成されます。 この変更により、アプリケーションが <xref:System.Web.UI.Page.LoadComplete?displayProperty=fullName> イベントのデータ バインディングの呼び出しに依存するような珍しい状況において、異なる動作が生成されるようになりました。|  
|<xref:System.Net.WebUtility.HtmlDecode%2A?displayProperty=fullName> メソッド、<xref:System.Net.WebUtility.UrlDecode%2A?displayProperty=fullName> メソッド、および [System.Web.Helpers.Json.Decode](https://msdn.microsoft.com/library/system.web.helpers.json.decode.aspx) メソッド|既定では、デコード メソッドによって無効な入力シーケンスが無効な UTF-16 文字列にデコードされることがなくなりました。 代わりに、元の入力が返されます。|デコーダーの出力の変更は、UTF-16 データではなくバイナリ データを文字列に格納した場合にのみ影響があります。 明示的にこの動作を制御するには、[\<appSettings>](http://msdn.microsoft.com/en-us/0d65a3f1-c522-423d-89b6-44921b6daebb) 要素の `aspnet:AllowRelaxedUnicodeDecoding` 属性を `true` に設定してレガシの動作を有効にするか、`false` に設定して現在の動作を有効にします。|  
|<xref:System.Net.WebUtility.HtmlEncode%2A?displayProperty=fullName> メソッド|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションの場合、基本多言語面 (BMP: Basic Multilingual Plane) の外部にある文字は、<xref:System.Net.WebUtility.HtmlDecode%2A?displayProperty=fullName> メソッドに渡されたときに正常に往復します。|この変更は、現在のアプリケーションには影響がありません。 元の動作を復元するには、[\<httpRuntime>](http://msdn.microsoft.com/library/e1f13641\(v=vs.100\).aspx) 要素の `targetFramework` 属性を "4.5" 以外の文字列に設定します。 また、.NET Framework の対象バージョンに関係なくこの動作を制御するために `unicodeEncodingConformance` 構成要素の `unicodeDecodingConformance` 属性と `<webUtility>` 属性を設定することもできます。|  
|<xref:System.Web.HttpRequest.ContentEncoding%2A?displayProperty=fullName> プロパティ|UTF-7 エンコードは禁止されています。|UTF-7 データの受信を必要とするアプリケーションのデータが、正しくデコードされない場合があります。 これはほとんどの場合は起こりませんが、[\<appSettings>](http://msdn.microsoft.com/en-us/0d65a3f1-c522-423d-89b6-44921b6daebb) 要素の `aspnet:AllowUtf7RequestContentEncoding` 属性を使用してレガシ動作に戻すことができます。|  
|<xref:System.Web.HttpUtility.JavaScriptStringEncode%2A?displayProperty=fullName>|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、このメソッドはアンパサンド (&amp;) 文字をエスケープします。|アプリがこのメソッドの以前の動作に依存している場合、`aspnet:JavaScriptDoNotEncodeAmpersand` 設定を構成ファイル内の [ASP.NET appSettings 要素](http://msdn.microsoft.com/en-us/bb60e711-0669-4118-a54d-8dd71e009a00) に追加できます。|  
|<xref:System.Web.Security.MachineKey.Encode%2A?displayProperty=fullName> メソッドおよび <xref:System.Web.Security.MachineKey.Decode%2A?displayProperty=fullName> メソッド|これらのメソッドは今後使用しません。|これらのメソッドを呼び出すコードをコンパイルすると、コンパイラ警告が生成されます。 別の方法として、<xref:System.Web.Security.MachineKey.Protect%2A?displayProperty=fullName> および <xref:System.Web.Security.MachineKey.Unprotect%2A?displayProperty=fullName> を使用することをお勧めします。|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|特性|変更|影響|  
|-------------|------------|------------|  
|SHA-256 コード署名証明書を使用して ClickOnce で発行されたアプリケーション。|この実行可能ファイルは SHA256 で署名されます。 以前は、コード署名証明書が SHA-1 か SHA-256 に関係なく、SHA 1 で署名されました。 この方法は、次の対象に適用されます。<br /><br /> Visual Studio 2012 以降でビルドされたすべてのアプリケーション。<br /><br /> .NET Framework 4.5 がインストールされているシステム上で、Visual Studio 2010 以前でビルドされたアプリケーション。<br /><br /> さらに、.NET Framework 4.5 以降が存在する場合、コンパイル対象となった .NET Framework のバージョンに関係なく、ClickOnce マニフェストはSHA-256 証明書の SHA 256 で署名されます。|ClickOnce 実行可能ファイルの署名方法に関するこの変更は、Windows Server 2003 システムにのみ影響を及ぼします。これらのシステムには、[KB 938397](http://support.microsoft.com/kb/938397) をインストールする必要があります。<br /><br /> アプリが .NET Framework 4 以前のバージョンをターゲットとしている場合でも、SHA-256 を使用したマニフェストの署名方法の変更により、.NET Framework 4.5 以降のバージョンに対するランタイム依存関係が導入されます。 この問題は Visual Studio 2013 Update 3 および [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で解決されています。 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] の解決策については、「[ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)」をご覧ください。|  
  
<a name="mef"></a>   
## <a name="managed-extensibility-framework-mef"></a>MEF (Managed Extensibility Framework)  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|<xref:System.ComponentModel.Composition.Primitives.ComposablePartCatalog?displayProperty=fullName> と派生クラス|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降、MEF カタログで <xref:System.Collections.IEnumerable> が実装されるようになったため、シリアライザーの作成には使用できなくなりました (<xref:System.Xml.Serialization.XmlSerializer> オブジェクト)。|MEF カタログをシリアル化しようとすると、例外がスローされます。|  
  
<a name="web"></a>   
## <a name="web-applications"></a>Web アプリケーション  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|.NET Framework 1.1 および 2.0 からのマネージ ブラウザーでのコントロールのホスト|これらのコントロールのホストは、Internet Explorer でブロックされます。|Internet Explorer では、マネージ ブラウザーを使用してコントロールをホストするアプリケーションは起動できません。 以前の動作を復元するには、レジストリ サブキー HKLM/SOFTWARE/MICROSOFT/.NETFramework の EnableIEHosting 値を、x86 システム用および x64 システム上の 32 ビット プロセス用に 1 に設定し、レジストリ サブキー HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework の EnableIEHosting 値を x64 システム上の 64 ビット プロセス用に 1 に設定します。|  
  
<a name="wcf"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 以下のアプリケーションの互換性の問題に加え、シリアル化に関連する問題について「[シリアル化](#serialize)」のセクションを参照してください。  
  
|特性|変更|影響|  
|-------------|------------|------------|  
|Internet Information Services (IIS) または ASP.NET 開発サーバーでホストされており、`maxRequestLength` (ASP.NET の場合) または `maxReceivedMessageSize` (WCF の場合) を超える WCF Web サービスのメッセージ |HTTP 状態コードは 400 (正しくない要求) から 413 (要求したエンティティが大きすぎます) に変更され、`maxRequestLength` または `maxReceivedMessageSize` 設定を超えるメッセージでは <xref:System.ServiceModel.ProtocolException> 例外がスローされます。 これには、転送モードが <xref:System.ServiceModel.TransferMode>である場合も含まれます。|この変更により、メッセージ長が ASP.NET または WCF で許可されている制限を超えたときのデバッグが簡単になります。<br /><br /> HTTP 400 状態コードに基づいて処理を実行するコードはすべて変更する必要があります。|  
|OData URL の `Replace`|OData URL の `Replace` メソッドは既定で無効になっています。|OData `Replace` が無効であると (既定の設定)、ユーザー要求は例外をスローし、要求は失敗します。|  
|<xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName>|<xref:System.ServiceModel.Web.WebServiceHost?displayProperty=fullName> オブジェクトでは、アプリケーション コードによって明示的なエンドポイントが追加された場合に、既定のエンドポイントが追加されなくなりました。|クライアント アプリケーションが、既定で追加されなくなったエンドポイントに接続しようとすると、HTTP エラーが発生します。|  
  
<a name="winForms"></a>   
## <a name="windows-forms"></a>Windows フォーム  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|System.Drawing.dll|アセンブリの `CheckForOverflowUnderflow` プロパティは、`true` に設定されます。|これまではオーバーフローが発生すると、その結果は自動的に切り捨てられました。 現在では、<xref:System.OverflowException> 例外がスローされます。|  
|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName> コンストラクター|このコンストラクターの使用は推奨されていません。|このコンストラクターは、64 ビット システムで動作しなくなりました。 代わりに、<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Drawing.Imaging.EncoderParameterValueType%2CSystem.IntPtr%29?displayProperty=fullName> コンストラクターを使用してください。|  
  
<a name="wpf"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 以下のアプリケーションの互換性の問題に加え、シリアル化に関連する問題について「[シリアル化](#serialize)」のセクションを参照してください。  
  
|特性|変更|影響|  
|-------------|------------|------------|  
|<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit%2A?displayProperty=fullName> プロパティ|<xref:System.Windows.Controls.TextBox> クラスと <xref:System.Windows.Controls.RichTextBox> クラスを元に戻す操作の最大回数の既定の制限値が、-1 (制限なし) から 100 に変更されました。|この変更によって生じる悪影響はないはずです。 ただし、コントロールをインスタンス化した後に明示的に <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit%2A> プロパティを設定することは可能です。|  
|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> 列挙体|<xref:System.Windows.Controls.PageRangeSelection> メンバーと <xref:System.Windows.Controls.PageRangeSelection> メンバーが、列挙型に追加されました。|この変更が、既存のアプリケーションに与える影響はありません。 この列挙型を使用する既存のメンバーの既定値は <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> です。|  
|<xref:System.Windows.DataTemplate> 要素|<xref:System.Windows.DataTemplate> の要素は、UI オートメーション (UIA) ツリーのコントロール ビューに表示されます。|この変更により、ユーザー補助が向上します。 ただし、隣接する要素を検索するために UIA ツリーの以前の構造を必要とするテスト ツールには影響があります。|  
|<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> プロパティとバインドされたプロパティの同期|場合によっては、データ バインディングの書き込み操作中にプロパティが変更された場合、<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> プロパティにデータ バインディング プロパティ値の以前の値が反映されることがあります。|これによって生じる悪影響はないはずです。 ただし、<xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty%2A?displayProperty=fullName> プロパティを `false` に設定して、以前の動作を復元することは可能です。|  
|<xref:System.Windows.Controls.TextBox?displayProperty=fullName> プロパティ|<xref:System.Windows.Controls.TextBox?displayProperty=fullName> のコントロールが非アクティブになると、ボックス内で選択したテキストが、テキスト ボックスがアクティブなときとは異なる色で表示されます。|<xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported%2A?displayProperty=fullName> プロパティを `false` に設定して、以前の動作を復元することができます。|  
|<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName>|<xref:System.Windows.Controls.Primitives.MultiSelector.CanSelectMultipleItems%2A> を `true` に設定した <xref:System.Windows.Controls.Primitives.MultiSelector> から派生されたコントロールの <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> コレクションに重複がある場合、重複した項目が複数回表示されます。 データ ソースからこれらの項目を削除すると (たとえば、`Items.Clear` を呼び出すことにより)、<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> コレクションからそれらの項目を削除できなくなります。最初のインスタンスのみが削除されます。<br /><br /> <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> コレクションを引き続き使用すると (`SelectedItems.Clear` の呼び出しなど)、<xref:System.ArgumentException> などの問題が発生する可能性があります。これは、<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> コレクション内に、データ ソース内にもはや存在しない項目が含まれているためです。|この問題は、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では対処済みです。 <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> コレクションに重複項目が含まれている場合、データ ソースからそれらを削除し、その後も <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A?displayProperty=fullName> コレクションを使用するには、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] にアップグレードしてください。|  
|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy%2A?displayProperty=fullName>|[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] では、メソッドは現在のインスタンスへの参照を返します。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、新しいインスタンスが返されます。|等しい値の参照を前提としているコードは、正しいコンテキストでのスレッドの実行は、現在でも正しく実行されることを示します。 ただし、変更が行われたため、<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy%2A?displayProperty=fullName> を呼び出すコードはテストする必要があります。|  
|<xref:System.Windows.Interop.HwndSource.AddHook%2A?displayProperty=fullName> メソッドの呼び出しによって追加されるハンドラーを使用した `WM_POWERBROADCAST` メッセージの監視|ウィンドウはハンドルを `WM_POWERBROADCAST` RegisterPowerSettingNotification [関数に渡すことによって、](https://msdn.microsoft.com/library/windows/desktop/aa373196.aspx) の通知を受けるための登録を明示的に行う必要があります。 WPF では、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] によってすべてのウィンドウで自動的にこの処理が行われていました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、WPF によって自動的に 1 つの特殊なウィンドウが登録されますが、ほとんどのアプリ ウィンドウは自動的に登録されません。|`WM_POWERBROADCAST` 通知を処理するコードは実行されません。<br /><br /> 引き続き `WM_POWERBROADCAST` 通知を受け取るには、[RegisterPowerSettingNotification](https://msdn.microsoft.com/library/windows/desktop/aa373196.aspx) 関数を呼び出して、WPF ウィンドウ (通常はアプリケーションのメイン ウィンドウ) が `WM_POWERBROADCAST` 通知を受け取るための登録を行います。 C# で開発した WPF アプリでは、このためにプロジェクト プロパティの **[ビルド]** タブで **[アンセーフ コードの許可]** ボックスをオンにする必要もあります。<br /><br /> さらに、アプリケーションがシャットダウンされるまで保持されないウィンドウを登録する場合は、[UnregisterPowerSettingNotification](https://msdn.microsoft.com/library/windows/desktop/aa373237.aspx) 関数を呼び出し、これに対して `HPOWERNOTIFY` RegisterPowerSettingNotification[ 関数の呼び出しから返された](https://msdn.microsoft.com/library/windows/desktop/aa373196.aspx)ハンドルを渡すことで、ウィンドウの登録を解除してください。|  
  
<a name="wwf"></a>   
## <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|System.Activities.dll のセキュリティ|アセンブリは <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性でマークされています。|派生クラスに <xref:System.Security.SecurityCriticalAttribute>のマークを付けることはできません。 以前は、派生型に <xref:System.Security.SecurityCriticalAttribute>マークを付ける必要がありました。 ただし、この変更によって生じる実質的な影響はないはずです。|  
|WF 3.0 の型およびメンバー|WF 3.0 の型とメンバーは互換性のために残されているものとしてマークされるようになりました。|WF 3.0 の型またはメンバーを使用するソース コードをコンパイルすると、コンパイラ エラーが発生します。 <xref:System.Activities> 名前空間では WF 4 の型およびメンバーを使用する必要があります。|  
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> クラス|<xref:System.Activities.Presentation.DragDropHelper> クラスには、複数のオブジェクトでのドラッグ アンド ドロップ操作をサポートする新しいメソッドが含まれています。 1 つのオブジェクトのドラッグをサポートする既存のドラッグ アンド ドロップ メソッドは廃止されました。 (詳しくは、「[クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)」をご覧ください。)|古いメソッドは廃止されますが、コンパイラと共通言語ランタイムの両方で引き続きサポートされます。 ただし、新しいメソッドの方が機能性が優れています。 既存のメソッドで推奨される代替メソッドは次のとおりです。<br /><br /> <xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName> の代わりに <xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName> を使用します。<br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Activities.Presentation.WorkflowViewElement%29> の代わりに <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29> を使用します。<br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItems%28System.Windows.DragEventArgs%29> の代わりに <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29> を使用します。<br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObjects%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29> の代わりに <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29> を使用します。|  
|<xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> メソッドへの呼び出しのオーバーロードの解決|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には、<xref:System.Action?displayProperty=fullName> 型のパラメーターが含まれる新しいオーバーロードが追加されています。 既存のコードを再コンパイルすると、コンパイラは <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> パラメーターを持つ <xref:System.Delegate> メソッドを <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> パラメーターを持つ <xref:System.Action?displayProperty=fullName> メソッドとして呼び出しを解決することができます。|<xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> パラメーターを持つ <xref:System.Delegate> オーバーロードへの呼び出しが <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=fullName> パラメーターを持つ <xref:System.Action?displayProperty=fullName> オーバーロードへの呼び出しとして解決されると、次のような動作上の変化が生じることがあります。<br /><br /> 例外が発生した場合、<xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter?displayProperty=fullName> イベントと <xref:System.Windows.Threading.Dispatcher.UnhandledException?displayProperty=fullName> イベントは発生しません。 代わりに、例外は <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> イベントによって処理されます。<br /><br /> <xref:System.Windows.Threading.DispatcherOperation.Result%2A?displayProperty=fullName> などの一部のメンバーの呼び出しは、操作が完了するまでブロックされます。|  
|<xref:System.Activities.Expressions.Literal%601?displayProperty=fullName> クラス|関連した <xref:System.Windows.Markup.ValueSerializer> オブジェクトは、<xref:System.DateTime> コンポーネントと <xref:System.DateTimeOffset> コンポーネントが非ゼロで (`Second` 値の場合)、`Millisecond` プロパティが <xref:System.DateTime> ではない <xref:System.DateTime.Kind%2A?displayProperty=fullName> オブジェクトまたは <xref:System.DateTimeKind> オブジェクトを文字列ではなくプロパティ要素構文に変換します。|この変更により、<xref:System.DateTime> 値と <xref:System.DateTimeOffset> 値を往復させることができるようになります。 入力 XAML が属性構文であると想定するカスタム XAML パーサーは正しく機能しません。|  
  
<a name="xml"></a>   
## <a name="xml-xslt"></a>XML、XSLT  
  
|機能|変更|影響|  
|-------------|------------|------------|  
|`XDocument.Validate` メソッド|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName> 値が <xref:System.Xml.Linq.XDocument.Load%2A> メソッドに渡されたときに検証エラーが発生すると、<xref:System.Xml.Schema.XmlSchemaException.LineNumber%2A?displayProperty=fullName> プロパティと <xref:System.Xml.Schema.XmlSchemaException.LinePosition%2A?displayProperty=fullName> プロパティに行情報が含まれるようになりました。|<xref:System.Xml.Schema.XmlSchemaException.LineNumber%2A?displayProperty=fullName> プロパティと <xref:System.Xml.Schema.XmlSchemaException.LinePosition%2A?displayProperty=fullName> のプロパティの値を必要とする例外処理コードは機能しなくなります。|  
|<xref:System.Xml.XmlTextReader?displayProperty=fullName> を使用した XML ファイルの読み込み|DTD エンティティの展開は 10,000,000 文字までに制限されています。|DTD エンティティの展開を使用しない XML ファイルの読み込みや、制限された DTD エンティティの展開を使用した XML ファイルの読み込みは、影響を受けません。 DTD エンティティの展開が 10,000,000 文字を超えるファイルは読み込みに失敗し、例外をスローします。|  
|<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=fullName> クラスの上位互換モード|[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では、XSLT 1.0 の上位互換性に、次の問題がありました。<br /><br /> バージョンが 2.0 に設定されているときに、パーサーが認識できない XSLT 1.0 コンストラクトに遭遇すると、スタイル シートの読み込みが失敗していました。<br /><br /> スタイル シートのバージョンが 1.1 に設定されている場合、`xsl:sort` コンストラクトでデータを並べ替えることができませんでした。<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、これらの問題は修正され、XSLT 1.0 の上位互換モードが正常に機能するようになりました。|XSLT 1.0 の上位互換モードは、以前と同じように機能します。|  
|XSLT ファイルが複雑すぎる場合の例外メッセージ|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、XSLT ファイルが複雑すぎる場合のエラー メッセージのテキストが 「スタイル シートが複雑すぎます」になります。 以前のバージョンのエラー メッセージは 「XSLT コンパイル エラー」でした。|エラー メッセージのテキストに依存するアプリケーション コードは機能しなくなります。 ただし、例外の種類は同じなので、この変更による実質的な影響はありません。|  
|xsd:anyURI の XML スキーマ検証|[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、XML スキーマ検証が厳格化されました。 xsd:anyURI を使用して mailto プロトコルなどの URI を検証したときに、URI にスペースが入っていると検証は失敗します。 .NET Framework の以前のバージョンでは、検証は成功していました。|この変更は、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を対象とするアプリケーションにのみ影響します。|  
  
## <a name="see-also"></a>関連項目  
 [クラス ライブラリの互換性のために残されている機能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [新機能](../../../docs/framework/whats-new/index.md)   
 [アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [4.5.1 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [4.5.2 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)
