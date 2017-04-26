---
title: ".NET Framework 4.6 におけるランタイムの変更点 | Microsoft Docs"
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
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6
- application compatibility
ms.assetid: 5262bcfa-6e48-416b-8972-69cb4002d386
caps.latest.revision: 34
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 77002c3d1b6553156c225b3efba9a2f29009915a
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-46"></a>.NET Framework 4.6 におけるランタイムの変更点
まれに、ランタイムの変更が、.NET Framework の以前のバージョンをターゲットとするものの、それ以降のバージョンの .NET Framework ランタイムで実行される既存のアプリに影響を与える可能性があります。 また、異なる .NET Framework ランタイム環境で実行されるアプリケーション間での動作に違いが生じます。 次の領域の変更が含まれています。  
  
-   [コア](#Core)  
  
-   [データ](#Data)  
  
-   [ネットワーク](#Networking)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [セットアップと配置](#Setup)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [新しい 64 ビット JIT コンパイラ](#RyuJIT)  
  
<a name="Core"></a>   
## <a name="core"></a>コア  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降の <xref:System.Globalization.PersianCalendar> クラスでは、イスラム暦の太陽アルゴリズムが使用されるようになりました。|イスラム暦の太陽アルゴリズムでは、イランとアフガニスタンで現在使用されているペルシャ暦と同じ結果が生成されます。 また、グレゴリオ暦の 1800 年からグレゴリオ暦の 2023 年の日付について、以前のアルゴリズムと同じ日付が生成されます。 この範囲外の日付には、<xref:System.Globalization.PersianCalendar> クラスを使用して日付を変換する (たとえば、グレゴリオ暦の日付とペルシャ暦の日付の間で) 場合や特定の年がうるう年かどうかを決定する場合に、影響が及ぶことがあります。<br /><br /> この変更を理由として、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] がインストールされたシステムでは、<xref:System.Globalization.PersianCalendar.MinSupportedDateTime%2A?displayProperty=fullName> プロパティの値が 0622 年 3 月 21 日から 0622 年 3 月 22 日に変更されました。<br /><br /> 詳細については、<xref:System.Globalization.PersianCalendar> に関するトピックを参照してください。|マイナー|  
|<xref:System.Runtime.Versioning.TargetFrameworkAttribute>|既定のアプリケーション ドメインに関しては、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティの値は <xref:System.Runtime.Versioning.TargetFrameworkAttribute> が存在する場合にはこの属性から派生します。ただし、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティに対して名前が割り当てられて明示的に定義されている場合は除きます。  .NET Framework の以前のバージョンでは、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> 属性の値は `null` でした。ただし、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティでターゲット フレームワークを明示的に指定しないで、さまざまな特別なコード パスを実行したり、既定以外のアプリ ドメインを作成したりする場合は除きます。<br /><br /> 既定以外のアプリケーション ドメインの場合、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティの値の決定方法に変更はありません。 <xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> プロパティに明示的に値が割り当てられていない場合、既定以外のアプリ ドメインは既定のアプリケーション ドメインからターゲット フレームワークの名前を継承します。|既定のアプリケーション ドメインの場合、<xref:System.AppDomainSetup.TargetFrameworkName%2A?displayProperty=fullName> はこれまでは `null` を返していましたが、null 以外の値を返すことがあります。 これは、適切な動作です。|エッジ|  
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|システムにインストールされている証明書が .NET Framework でサポートされていない場合、`verbose` 引数で `True` 値を渡すと有効な文字列が返されます。 .NET Framework の以前のバージョンでは、サポートされていない証明書の公開キーの情報にアクセスしようとすると、例外がスローされることがあります。|このメソッドは情報提供のみが目的で、ドキュメントは .NET Framework のバージョン間で出力に一貫性がない場合があることを示しています。 この変更が影響を及ぼすのは、`ToString(True)` メソッドを呼び出し、.NET Framework によってサポートされていない証明書がインストールされているアプリに対してのみです。 この変更で例外をスローするのではなく文字列を返すことにより、メソッドがより堅牢になっています。|エッジ|  
|Windows イベント トレーシング (ETW)|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] および 4.6.1 では、2 つのイベント名の違いがサフィックスの "Start" または "Stop" である場合 (1 つのイベント名が `LogUser` であり、もう 1 つのイベント名が `LogUserStart` である場合など)、ランタイムから <xref:System.ArgumentException> がスローされます。 この場合、ランタイムはイベント ソースを作成できないため、ログ記録は生成できません。|違いがサフィックスの "Start" または "Stop" のみである 2 つのイベント名がないことを確認してください。<br /><br /> この要件は、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降では削除されています。ランタイムでは、サフィックスの "Start" のみ異なるイベント名が明確に区別されるようになりました。|エッジ|  
|リフレクションと分散 COM (DCOM)|リフレクション オブジェクトはマネージ コードからアウト プロセス DCOM クライアントに渡されなくなりました。 この影響を受ける型は、<xref:System.Reflection.Assembly>、<xref:System.Reflection.MemberInfo> とその派生型 (<xref:System.Reflection.FieldInfo>、<xref:System.Reflection.MethodInfo>、<xref:System.Type>、<xref:System.Reflection.TypeInfo> など)、<xref:System.Reflection.MethodBody>、<xref:System.Reflection.Module>、<xref:System.Reflection.ParameterInfo> です。|このオブジェクトの [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707.aspx) を呼び出すと、`E_NOINTERFACE` が返されます。|マイナー|  
  
<a name="Data"></a>   
## <a name="data"></a>データ  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|`localhost` に解決される SQL Server データベースへの TCP/IP 接続|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降でこうした接続を行おうとすると、次のエラーで失敗していました: "SQL Server への接続を確立しているときにネットワーク関連またはインスタンス固有のエラーが発生しました。 サーバーが見つからないかアクセスできません。 インスタンス名が正しいこと、および SQL Server がリモート接続を許可するように構成されていることを確認してください。 (プロバイダー: SQL ネットワーク インターフェイス、エラー: 26 - 指定されたサーバーまたはインスタンスの位置を特定しているときにエラーが発生しました)"。|この問題は [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] で修正済みであり、バージョン 4.6 以前の動作に戻っています。 `localhost` に解決される SQL Server データベースに接続するには、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] にアップグレードします。|マイナー|  
  
<a name="Networking"></a>   
## <a name="networking"></a>ネットワーク  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> クラスの日時の値|[RFC822](http://www.ietf.org/rfc/rfc0822.txt) と [RFC2822](http://www.ietf.org/rfc/rfc2822.txt) に準拠するため、書式設定後の日時の値の時刻が 2 桁になりました。 以前は、午前 10時 00分より前の時間は 1 桁で表されていました。|この変更は、次のような使用シナリオに影響します。<br /><br /> - .NET Framework の異なるバージョン間でシリアル化された <xref:System.Net.Mime.ContentDisposition> オブジェクトの長さやハッシュ コードを比較する場合。<br />- .NET Framework の異なるバージョン間で <xref:System.Net.Mime.ContentDisposition.ToString%2A> メソッドの戻り値または <xref:System.Net.Mime.ContentDisposition> 日時プロパティの値を表す文字列を比較する場合。|マイナー|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|SSL セキュリティと証明書認証で NETTCP を使用する WCF サービス|.NET Framework 4.6 では、WCF SSL の既定のプロトコル一覧に TLS 1.1 および TLS 1.2 が追加されます。 クライアントとサーバーの両方のマシンに .NET Framework 4.6 以降がインストールされている場合は、TLS 1.2 がネゴシエーションに使用されます。|TLS 1.2 では MD5 証明書認証がサポートされません。 このため、顧客が MD5 証明書を使用する場合、WCF クライアントでは WCF サービスへ接続できません。 詳細については、「[Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md)」(軽減策: WCF サービスと証明書認証) を参照してください。|マイナー|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|マルチ モニターのシナリオにおけるウィンドウのレンダリング|マルチ モニターのシナリオでディスプレイの外部にウィンドウを拡張すると、ウィンドウ全体がクリッピングなしでレンダリングされます。|「[軽減策: WPF ウィンドウのレンダリング](../../../docs/framework/migration-guide/mitigation-wpf-window-rendering.md)」を参照してください。|マイナー|  
|WPF テキスト対応コントロールのスペル チェック機能|プラットフォームのスペル チェック機能は入力言語リストに存在する言語でしか使用できないため、スペル チェック機能が Windows 10 での実行時に動作しないことがあります。|Windows 10 では、使用可能なキーボードのリストに言語を追加すると、対応するオンデマンド機能 (FOD) パッケージが自動的にダウンロードおよびインストールされ、スペル チェック機能が提供されます。 入力言語リストに言語を追加することで、スペル チェック機能がサポートされます。|マイナー|  
  
<a name="Setup"></a>   
## <a name="setup-and-deployment"></a>セットアップと配置  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|製品のバージョン管理|製品のバージョン管理が、.NET Framework の以前のリリース (特に .NET Framework 4、4.5、4.5.1、および 4.5.2) から変更されました。 詳細については、「[軽減策: 製品のバージョン管理](../../../docs/framework/migration-guide/mitigation-product-versioning.md)」を参照してください。|「[軽減策: 製品のバージョン管理](../../../docs/framework/migration-guide/mitigation-product-versioning.md)」を参照してください。|Medium|  
  
<a name="ClickOnce"></a>   
## <a name="clickonce"></a>ClickOnce  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|SHA-256 コード署名証明書を使用して ClickOnce で発行されたアプリケーション。|[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 以前のバージョンをターゲットとし、SHA-256 証明書で署名された ClickOnce アプリは、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンに対するランタイム依存関係を持たなくなりました。|これまでは、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 以前のバージョンをターゲットとする ClickOnce アプリに SHA-256 証明書を使用して署名する場合、ターゲット システム上に [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降のバージョンが存在する必要がありました。 そのため、存在しない場合はエラーが発生しました。 この変更により、その依存関係がなくなったので、[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 以前のバージョンをターゲットとする ClickOnce アプリの署名にSAH-256 証明書が使用できるようになりました。|マイナー|  
  
<a name="RyuJIT"></a>   
## <a name="the-new-64-bit-jit-compiler"></a>新しい 64 ビット JIT コンパイラ  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|64 ビット JIT コンパイル|.NET Framework 4.6 以降では、Just-In-Time コンパイルには新しい 64 ビット JIT コンパイラが使用されます。 この変更は、32 ビット JIT コンパイラには影響しません。|場合によっては、予期しない例外がスローされるか、32 ビット コンパイラまたは以前の 64 ビット JIT コンパイラを使用してアプリを実行したときとは動作が異なる可能性があります。 **注:** これら問題はすべて、.NET Framework 4.6.2 と共にリリースされた新しい 64 ビット コンパイラで対処済みです。 また、Windows 更新プログラムに含まれる .NET Framework 4.6 および 4.6.1 のサービス リリースでも大部分に対処済みです。 <br /><br /> 詳細については、「[Mitigation: New 64-bit JIT Compiler](../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)」(軽減策: 新しい 64 ビット JIT コンパイラ) を参照してください。|エッジ|  
|例外処理 (`try` 領域から返す)|以前の JIT64 Just-In-Time コンパイラとは異なり、新しい 64 ビット JIT コンパイラでは、`try` 領域での IL `ret` 命令は許可されません。|ECMA 335 仕様により `try` 領域から戻ることは許可されておらず、そうした IL を生成する既知のマネージ コンパイラはありません。 ただし、JIT64 コンパイラは、リフレクション出力を使用して生成される場合にはこうした IL を実行します。<br /><br /> `ret` オペコードが `try` 領域に含まれる IL をアプリで生成する場合は、次のようにしてください。<br /><br /> - .NET Framework 4.5 をターゲットにするか [\<useLegacyJIT>](../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) 要素をアプリケーション構成ファイルに追加して、古い JIT コンパイラを使用しこの変更点を回避する。<br />- 生成された IL が `try` 領域の後で返されるように更新する。<br />-|エッジ|
