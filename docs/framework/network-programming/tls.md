---
title: ".NET Framework で、トランスポート層セキュリティ (TLS) のベスト プラクティス"
description: ".NET Framework とトランスポート層セキュリティ (TLS) を使用したベスト プラクティスについて説明します"
ms.date: 03/15/2018
ms.prod: .net-framework
ms.topic: article
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
author: blowdart
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64829eee5b21a44acb18cbec9b901d77d49cab90
ms.sourcegitcommit: 3eea47bff3201ae5d3395b0c7947806c2faca255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>.NET Framework で、トランスポート層セキュリティ (TLS) のベスト プラクティス

トランスポート層セキュリティ (TLS) プロトコルは、インターネット経由でやり取りされる情報のプライバシーを保護するために策定された業界標準です。 [TLS 1.2](https://tools.ietf.org/html/rfc5246)最新のリリースの標準は、以前のバージョンを超えるセキュリティの向上を提供します。 TLS 1.2 は最終的に置き換えられます[TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22)です。 この記事では、TLS プロトコルを使用する .NET Framework アプリケーションをセキュリティで保護する推奨事項を示します。

TLS バージョンには .NET Framework アプリケーションのセキュリティで保護されたままことを確認するには、**いない**ハードコーディングすることです。 .NET framework アプリケーションでは、オペレーティング システム (OS) をサポートしている TLS バージョンを使用する必要があります。

このドキュメントは開発者を対象します。

- 使用して直接、 <xref:System.Net> Api (たとえば、<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>と<xref:System.Net.Security.SslStream?displayProperty=nameWithType>)。
- WCF クライアントおよびサービスを使用してを使用して直接、<xref:System.ServiceModel?displayProperty=nameWithType>名前空間。
- 使用して[Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Web ロールとワーカー ロールをホストするアプリケーションを実行します。 参照してください、 [Azure Cloud Services](#azure-cloud-services)セクションです。

お勧めします。

- .NET Framework 4.7 またはアプリでの以降のバージョンを対象とします。 .NET Framework 4.7.1 または WCF アプリケーションでそれ以降のバージョンを対象とします。
- TLS バージョンを指定しません。 TLS バージョンの決定、OS を使用するようにコードを構成します。
- TLS や SSL のバージョンを指定しているしないことを確認するコード全体の監査を実行します。

アプリにより、OS は TLS バージョンを選択します。

- 自動的に、新しいプロトコルが、将来追加、TLS 1.3 などの利点がかかります。
- オペレーティング システムでは、セキュリティで保護されていないに検出されたプロトコルをブロックします。

セクション[、コードを監査し、コード変更を加える](#audit-your-code-and-make-code-changes)監査と、コードの更新について説明します。

この記事では、アプリをターゲットし、で実行されている .NET Framework のバージョンで使用できる最も強力なセキュリティを有効にする方法について説明します。 アプリは、セキュリティ プロトコルとバージョンを明示的に設定、その他の選択肢を止めたし、.NET Framework と OS の既定の動作が止めたされます。 TLS 1.2 の接続をネゴシエートできるアプリを設定する場合に、TLS 1.2 の接続を下位バージョンの TLS に明示的に設定しないようにします。

ハードコーディングするプロトコルのバージョンを回避することはできません場合、TLS 1.2 を指定することを強くお勧めします。 識別して、TLS 1.0 の依存関係の削除に関するガイダンスについては、ダウンロード、 [TLS 1.0 の問題を解決する](https://www.microsoft.com/download/details.aspx?id=55266)ホワイト ペーパー。

WCF サポート TLS1.0、1.1 と 1.2 の既定の .NET Framework 4.7 として。 .NET Framework 4.7.1 から始めて、WCF 既定値は、オペレーティング システムは、バージョンを構成します。 アプリケーションが明示的に構成されている場合`SslProtocols.None`、NetTcp トランスポートを使用する場合、WCF がオペレーティング システムの既定の設定を使用します。

このドキュメントの GitHub の問題に関する質問を投稿できます[トランスポート層セキュリティ (TLS) のベスト プラクティス、.NET Framework と一緒に](https://github.com/dotnet/docs/issues/4675)です。

## <a name="audit-your-code-and-make-code-changes"></a>コードを監査し、コードを変更

ASP.NET アプリケーションでは、検査、`<system.web><httpRuntime targetFramework>`要素の_web.config_目的のバージョンの .NET Framework を使用していることを確認します。

Windows フォームとその他のアプリケーションでは、次を参照してください。[する方法: .NET Framework のバージョンを対象に](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework)です。

特定の TLS や SSL のバージョンを使用していないことを確認するのにには、次のセクションを使用します。

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>アプリが .NET Framework 4.7 またはそれ以降のバージョンを対象とする場合

次のセクションでは、特定の TLS や SSL のバージョンを使用していないことを確認する方法を示します。

### <a name="for-http-networking"></a>HTTP ネットワークの

<xref:System.Net.ServicePointManager>、最適なセキュリティ プロトコルとバージョンを選択するオペレーティング システムの既定値は .NET Framework 4.7 およびそれ以降のバージョンを使用します。 既定の OS の最適な選択肢を取得するには、可能であれば、しない値を設定、<xref:System.Net.ServicePointManager.SecurityProtocol>プロパティです。 それ以外の場合は <xref:System.Net.SecurityProtocolType.SystemDefault> に設定します。

この記事の残りの部分は、.NET Framework 4.7 または HTTP ネットワークの以降のバージョンを対象とする場合に関係ありません。

### <a name="for-tcp-sockets-networking"></a>TCP ソケットのネットワー キング

<xref:System.Net.Security.SslStream>、最適なセキュリティ プロトコルとバージョンを選択するオペレーティング システムの既定値は .NET Framework 4.7 およびそれ以降のバージョンを使用します。 既定の OS の最適な選択肢を取得するには、可能であれば、使用しない、メソッドのオーバー ロード<xref:System.Net.Security.SslStream>を受け取る、明示的な<xref:System.Security.Authentication.SslProtocols>パラメーター。 それ以外の場合、渡す<xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>です。 使用しないことをお勧め<xref:System.Security.Authentication.SslProtocols.Default>設定; `SslProtocols.Default` SSL 3.0/TLS 1.0 の使用を強制および TLS 1.2 を防止します。

値を設定しないで、<xref:System.Net.ServicePointManager.SecurityProtocol>プロパティ (HTTP ネットワークで)。

メソッドのオーバー ロードを使用しない<xref:System.Net.Security.SslStream>を受け取る、明示的な<xref:System.Security.Authentication.SslProtocols>(TCP ソケットがネットワーク) のパラメーターです。 .NET Framework 4.7 またはそれ以降のバージョンをアプリのターゲットを変更するときに、推奨されるベスト プラクティスを次するします。

このトピックの残りの部分は、ネットワーク ソケット (TCP)、.NET Framework 4.7 またはそれ以降のバージョンを対象とするときに関係ありません。

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>WCF TCP トランスポート トランスポートのセキュリティ証明書資格情報を使用します。

WCF では、.NET Framework の残りの部分として、同じネットワーク スタックを使用します。

4.7.1 を対象とする場合、WCF は、OS を明示的に構成されていない場合、既定では最適なセキュリティ プロトコルを選択できるように構成します。

- で、アプリケーション構成ファイル。
- **または**、ソース コードで、アプリケーションでします。

既定では、.NET Framework 4.7 以降のバージョン TLS 1.2 を使用するように構成し、の TLS 1.1、TLS 1.0 を使用して接続を許可します。 構成を使用するバインディングを構成することによって最適なセキュリティ プロトコルを選択する OS を許可する WCF<xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>です。 これに対して設定できる<xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>です。 `SslProtocols.None` アクセスできる<xref:System.ServiceModel.NetTcpSecurity.Transport>です。 `NetTcpSecurity.Transport` アクセスできる<xref:System.ServiceModel.NetTcpBinding.Security>です。

カスタム バインドを使用する: 場合

- 構成を設定して、最適なセキュリティ プロトコルを選択する OS を許可する WCF<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>を使用する<xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>です。
- **または**構成パスで使用されるプロトコルを構成する`system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`です。

場合**いない**カスタム バインディングを使用して**と**構成を使用して、WCF バインドを設定するとき、構成パスで使用されるプロトコルの設定`system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`です。

### <a name="for-wcf-message-security-with-certificate-credentials"></a>証明書の資格情報を持つ WCF メッセージ セキュリティ

.NET framework 4.7 と既定では以降のバージョンで指定されたプロトコルを使用して、<xref:System.Net.ServicePointManager.SecurityProtocol>プロパティです。 ときに、 [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`に設定されている`true`WCF は、TLS 1.0 までの最適なプロトコルを選択します。

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>アプリが 4.7 より前の .NET Framework のバージョンを対象とする場合

次のセクションを使用して特定の TLS や SSL のバージョンを設定しているしないことを確認するようにコードを監査するには。

### <a name="for-net-framework-46---462-and-not-wfc"></a>.NET Framework 4.6 の 4.6.2 といない WFC の

設定、 `DontEnableSystemDefaultTlsVersions` `AppContext`に切り替える`false`です。 参照してください[AppContext スイッチ経由でのセキュリティを構成する](#configuring-security-via-appcontext-switches)です。

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>WCF を使用して .NET Framework 4.6 の 4.6.2 TCP トランスポートのセキュリティ証明書資格情報を使用します。

最新の OS 修正プログラムをインストールする必要があります。 参照してください[セキュリティ更新プログラム](#security-updates)です。

WCF フレームワークでは、プロトコルのバージョンを明示的に構成しない限り、TLS 1.2 までの最上位のプロトコルによって自動的に選択します。 詳細については、前のセクションを参照してください。[証明書の資格情報を持つトランスポート セキュリティを使用して WCF TCP をトランスポート](#wcf-tcp-cert)です。

### <a name="for-net-framework-35---451-and-not-wcf"></a>.NET framework 3.5、4.5.1、および WCF ではありません。

アプリを .NET Framework 4.7 またはそれ以降のバージョンにアップグレードすることをお勧めします。 をアップグレードできない場合は、以下の手順を実行します。 ある時点で、将来、アプリケーションが失敗する .NET Framework 4.7 またはそれ以降のバージョンにアップグレードするまでです。

設定、 [SchUseStrongCrypto](#schusestrongcrypto)と[SystemDefaultTlsVersions](#systemdefaulttlsversions)レジストリ キーを 1 にします。 参照してください[Windows レジストリを使用してセキュリティを構成する](#configuring-security-via-the-windows-registry)です。 .NET Framework version 3.5 をサポートしている、`SchUseStrongCrypto`明示的な TLS 値が渡されたときにのみフラグを設定します。

.NET Framework 3.5 を実行している場合は、TLS 1.2 は、プログラムで指定できるように、ホット パッチをインストールする必要があります。

| [KB3154518](https://support.microsoft.com/kb/3154518) | Windows 7 SP1 および Server 2008 R2 SP1 上で .NET Framework 3.5.1 の信頼性ロールアップ HR-1605 - TLS システム既定のバージョンのサポートが含まれる |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | 信頼性ロールアップ HR-1605 - Windows Server 2012 での .NET Framework 3.5 に含まれる、TLS システム既定のバージョンのサポート |
| [KB3154520](https://support.microsoft.com/kb/3154520) | 信頼性ロールアップ HR 1605 - Windows 8.1 および Windows Server 2012 R2 の .NET Framework 3.5 に含まれる TLS システム既定のバージョンのサポート |
| [KB3156421](https://support.microsoft.com/kb/3156421) | .NET Framework 4.5.2、4.5.1 on Windows 用修正プログラム ロールアップ 3154521 1605 |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>WCF を使用して .NET Framework 3.5 の 4.5.2 TCP トランスポートのセキュリティ証明書資格情報を使用します。

これらのバージョンの WCF フレームワークは、SSL 3.0、TLS 1.0 の値を使用してにハードコードされてです。 これらの値を変更することはできません。 更新し、TLS 1.1 と 1.2 を使用するには、NET Framework 4.6 またはそれ以降のバージョンに再ターゲットする必要があります。

## <a name="if-your-app-targets-net-framework-35"></a>アプリが .NET Framework 3.5 を対象とする場合

場合は、.NET framework または OS の選択ではなく、セキュリティ プロトコルはセキュリティ プロトコルを明示的に設定する必要があります、追加`SecurityProtocolTypeExtensions`と`SslProtocolsExtension`コードを列挙します。 `SecurityProtocolTypeExtensions` および`SslProtocolsExtension`の値を含める`Tls12`、 `Tls11`、および`SystemDefault`値。 参照してください[TLS システム既定のバージョンの Windows 8.1 および Windows Server 2012 R2 の .NET Framework 3.5 に含まれるサポート](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework)です。

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>(.NET Framework 4.6 以降のバージョン用) スイッチ AppContext 経由でのセキュリティを構成します。

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)このセクションで説明したスイッチに関連する場合、アプリのターゲットまたは .NET Framework 4.6 以降で実行されます。 既定では、または明示的に設定することによりスイッチがあるかどうか`false`可能な場合です。 コードでセキュリティ プロトコル値を指定しない 1 つまたは両方のスイッチ経由でのセキュリティを構成する場合は、そのためオーバーライド スイッチ。

HTTP ネットワークを実行しているかどうか、同じ効果をスイッチがあります (<xref:System.Net.ServicePointManager>) TCP ソケットのネットワー キングまたは (<xref:System.Net.Security.SslStream>)。

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

値`false`の`Switch.System.Net.DontEnableSchUseStrongCrypto`により強力な暗号化を使用するようにします。 値`false`の`DontEnableSchUseStrongCrypto`はより安全なネットワーク プロトコル (TLS 1.2、TLS 1.1 および TLS 1.0) を使用し、セキュリティで保護されていないプロトコルをブロックします。 詳細については、次を参照してください。 [、SCH_USE_STRONG_CRYPTO フラグ](#the-schusestrongcrypto-flag)です。 値`true`アプリの強力な暗号化を無効にします。

アプリをターゲット .NET Framework 4.6 以降では場合、このスイッチの既定値`false`です。 セキュリティで保護された既定値をお勧めです。 アプリは .NET Framework 4.6 上で実行は、以前のバージョンを対象に場合、スイッチの既定値`true`です。 その場合は、明示的に設定してください、`false`です。

`DontEnableSchUseStrongCrypto` 値のみが`true`強力な暗号化をサポートしていないため、アップグレードできませんを従来のサービスに接続する必要がある場合。

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

値`false`の`Switch.System.Net.DontEnableSystemDefaultTlsVersions`プロトコルを選択するオペレーティング システムを許可するアプリをによりします。 値`true`により、.NET Framework によって取得されたプロトコルを使用するようにします。

アプリは、.NET Framework 4.7 またはそれ以降のバージョンを対象場合、このスイッチの既定値`false`です。 推奨するセキュリティで保護された、既定値です。 アプリは、.NET Framework 4.7 またはそれ以降のバージョンで実行されますが、以前のバージョンを対象場合、スイッチの既定値`true`です。 その場合は、明示的に設定してください、`false`です。

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

値`false`の`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols`で定義されている値を使用するアプリケーションで、`ServicePointManager.SecurityProtocols`メッセージのセキュリティ証明書の資格情報を使用します。 値`true`TLS1.0 まで、使用可能な最も高いプロトコルを使用

.NET Framework 4.7 およびそれ以降のバージョンを対象とするアプリケーションでは、この値は既定でに`false`です。 .NET Framework 4.6.2 を対象とするアプリケーションにこの値は既定で、前と`true`です。

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

値`false`の`Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions`プロトコルを選択するオペレーティング システムを許可する既定の構成を設定します。 値`true`TLS1.2 まで、使用可能な最も高いプロトコルを既定値に設定します。

.NET Framework 4.7.1 およびそれ以降のバージョンを対象とするアプリケーションでは、この値は既定でに`false`です。 4.7 およびそれ以前の .NET Framework を対象とするアプリケーションでは、この値は既定でに`true`です。

TLS プロトコルの詳細については、次を参照してください。[軽減策: TLS プロトコル](../migration-guide/mitigation-tls-protocols.md)です。 詳細については`AppContext`スイッチを参照してください[ `<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)です。

## <a name="configuring-security-via-the-windows-registry"></a>Windows レジストリを使用してセキュリティを構成します。

いずれかまたは両方を設定する場合は`AppContext`スイッチがオプションではない、アプリは、このセクションで説明されている Windows のレジストリ キーを使用しているセキュリティ プロトコルを制御することができます。 いずれかまたは両方を使用することができない、`AppContext`スイッチの場合は、アプリケーションが .NET Framework のバージョンを対象、4.6 より前または構成ファイルを編集することはできません。 コードでセキュリティ プロトコル値をし、指定しない場合は、レジストリのセキュリティを構成するには、そのためはオーバーライド レジストリします。

レジストリ キーの名前は、対応する名前のような`AppContext`スイッチしますが、ない、`DontEnable`名に付加します。 たとえば、`AppContext`切り替える`DontEnableSchUseStrongCrypto`レジストリ キーと呼びます[SchUseStrongCrypto](#schusestrongcrypto)です。

これらのキーが最新のセキュリティ修正プログラムが存在するすべての .NET Framework のバージョンで使用できます。 参照してください[セキュリティ更新プログラム](#security-updates)です。

同じ効果がありますすべて以下に示すレジストリ キーの HTTP ネットワークを実行しているかどうか (<xref:System.Net.ServicePointManager>) TCP ソケットのネットワー キングまたは (<xref:System.Net.Security.SslStream>)。

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto`レジストリ キーには、DWORD 型の値が含まれています。 値 1 の場合、強力な暗号化を使用するようにします。 強力な暗号化より安全なネットワーク プロトコル (TLS 1.2、TLS 1.1、TLS 1.0) を使用し、セキュリティで保護されていないプロトコルをブロックします。 値 0 は、強力な暗号化を無効にします。 詳細については、次を参照してください。 [、SCH_USE_STRONG_CRYPTO フラグ](#the-schusestrongcrypto-flag)です。

アプリをターゲット .NET Framework 4.6 以降では、このキーの値が 1 の既定値です。 推奨するセキュリティで保護された、既定値です。 アプリでは、.NET Framework 4.6 上で実行は、以前のバージョンを対象に場合、は、0 をキーが既定値です。 その場合は、その値を 1 に明示的に設定する必要があります。

強力な暗号化をサポートしていないため、アップグレードできませんを従来のサービスに接続する必要がある場合、このキーは、値 0 をのみが必要です。

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions`レジストリ キーには、DWORD 型の値が含まれています。 値 1 の場合、オペレーティング システムのプロトコルを選択できるようにするアプリです。 値 0 の場合、.NET Framework によって取得されたプロトコルを使用するアプリです。

`<VERSION>` (.NET Framework 3.5) 用 v4.0.30319 (.NET Framework 4 以降用) または v2.0.50727 をする必要があります。

アプリでは、.NET Framework 4.7 またはそれ以降のバージョンを対象、このキーの値が 1 の既定値です。 推奨するセキュリティで保護された、既定値です。 アプリは .NET Framework 4.7 またはそれ以降のバージョンで実行されるは、以前のバージョンを対象に場合、キーの既定値は 0 にします。 その場合は、その値を 1 に明示的に設定する必要があります。

詳細については、次を参照してください。 [Windows 10 Version 1511 の累積的な更新プログラムと Windows Server 2016 Technical Preview 4: 2016 年 5 月 10、](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)です。

.NET framework 3.5.1 の詳細については、次を参照してください。 [TLS システム既定のバージョンに .NET Framework 3.5.1 を Windows 7 SP1 および Server 2008 R2 SP1 に含まれるサポート](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework)です。

次_です。REG_ファイル、レジストリ キーとそのバリエーションが最も安全な値に設定します。

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Windows レジストリの Schannel プロトコルの構成

サーバーやクライアント アプリをネゴシエートするプロトコルをきめ細かく制御のレジストリを使用することができます。 アプリのネットワークを通過 Schannel (別の名前は[セキュリティで保護されたチャネル](https://msdn.microsoft.com/library/windows/desktop/aa380123)です。 構成することによって`Schannel`アプリの動作を構成することができます。

始まる、`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols`レジストリ キー。 セット内のすべてのサブキーを作成するキーの下にある`SSL 2.0`、 `SSL 3.0`、 `TLS 1.0`、 `TLS 1.1`、および`TLS 1.2`です。 それらのサブキーの下で、サブキーを作成することができます`Client`や`Server`です。 `Client`と`Server`、DWORD 値を作成する`DisabledByDefault`(0 または 1) と`Enabled`(0 または 0 xffffffff) です。

## <a name="the-schusestrongcrypto-flag"></a>SCH_USE_STRONG_CRYPTO フラグ

有効な場合 (既定では、によって、`AppContext`切り替えるには、または Windows レジストリ)、.NET Framework を使用して、`SCH_USE_STRONG_CRYPTO`アプリは、TLS セキュリティ プロトコルを要求するときにフラグを設定します。 `SCH_USE_STRONG_CRYPTO`フラグは既定で有効にすることができます、`AppContext`切り替えるには、またはレジストリにします。 OS にフラグを渡します`Schannel`に指示する既知の脆弱な暗号アルゴリズムを無効にするには、暗号スイート、および TLS と SSL プロトコルのバージョンを相互運用性を向上させるそれ以外の場合有効にすることがあります。 詳細については次を参照してください:

- [セキュリティで保護されたチャネル](https://msdn.microsoft.com/library/windows/desktop/aa380123)
- [SCHANNEL_CRED 構造体](https://msdn.microsoft.com/library/windows/desktop/aa379810)

`SCH_USE_STRONG_CRYPTO`にフラグが渡されるも`Schannel`明示的に使用すると、 `Tls` (TLS 1.0) `Tls11`、または`Tls12`列挙の値の<xref:System.Net.SecurityProtocolType>または<xref:System.Security.Authentication.SslProtocols>です。

## <a name="security-updates"></a>セキュリティ更新プログラム

この記事でベスト プラクティスは、最新のセキュリティ更新プログラムがインストールされているによって異なります。 これらの更新プログラムには、高度な .NET Framework 4.7 とそれ以降の機能を使用する機能が含まれます。 最新のセキュリティ更新プログラムは、(も対象とする場合、以前のバージョン)、アプリが .NET Framework 4.7 およびそれ以降のバージョンで実行する場合に重要です。

オペレーティング システムの TLS を使用する最適なバージョンを選択できるようにする .NET Framework を更新するには、必要がありますをインストールするには、少なくとも。

- [品質プログラムのロールアップの .NET Framework 2017 年 8 月プレビュー](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup)です。
- **または**、 [.NET Framework 2017 年 9 月のセキュリティと品質ロールアップ](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup)です。

参照:

- [.NET framework のバージョンとの依存関係](../migration-guide/versions-and-dependencies.md)
- [方法: どの .NET Framework のバージョンがインストールされている確認](../migration-guide/how-to-determine-which-versions-are-installed.md)です。

## <a name="support-for-tls-12"></a>TLS 1.2 のサポート

TLS 1.2、OS と .NET Framework のバージョンをネゴシエートするアプリの両方は、TLS 1.2 をサポートするために必要があります。

**TLS 1.2 をサポートするオペレーティング システムの要件**

有効にするにまたはこれらをサポートするシステムで TLS 1.2 または TLS 1.1 を再び有効には、次を参照してください。[トランスポート層セキュリティ (TLS) のレジストリ設定](/windows-server/security/tls/tls-registry-settings)です。

| **OS** | **TLS 1.2 サポート** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | サポートされており、既定で有効にします。 |
| Windows 8.1</br>Windows Server 2012 R2 | サポートされており、既定で有効にします。 |
| Windows 8.0</br>Windows Server 2012 | サポートされており、既定で有効にします。 |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | サポートされますが、既定で有効化されていません。 参照してください、[トランスポート層セキュリティ (TLS) のレジストリ設定](/windows-server/security/tls/tls-registry-settings)TLS 1.2 を有効にする方法の詳細については、web ページ。 |
| Windows Server 2008 | TLS 1.2 および TLS 1.1 のサポートには、更新プログラムが必要です。 参照してください[Windows Server 2008 SP2 で TLS 1.1 および TLS 1.2 サポートを追加する更新プログラム](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s)です。 |
| Windows Vista | サポートされていません。 |

TLS と SSL のプロトコルは各バージョンの Windows では既定で有効になっているについては、次を参照してください。 [TLS/SSL (Schannel SSP) のプロトコル](https://msdn.microsoft.com/library/windows/desktop/mt808159)です。

**.NET Framework 3.5 で TLS 1.2 をサポートするための要件**

次の表は、.NET Framework 3.5 で TLS 1.2 をサポートする必要があります、OS の更新プログラムを示します。 すべての OS の更新を適用することをお勧めします。

| **OS** | **.NET Framework 3.5 で TLS 1.2 をサポートするために必要な最小の更新** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Windows 10 バージョン 1511 の累積更新プログラムと Windows Server 2016 Technical Preview 4: 10、2016 年 5 月](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [Windows 8.1 および Windows Server 2012 R2 の .NET Framework 3.5 に含まれる、TLS システム既定のバージョンのサポート](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [Windows Server 2012 での .NET Framework 3.5 に含まれる、TLS システム既定のバージョンのサポート](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [Windows 7 SP1 および Server 2008 R2 SP1 上で .NET Framework 3.5.1 に含まれる、TLS システム既定のバージョンのサポート](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Windows Vista SP2 および Server 2008 SP2 で .NET Framework 2.0 SP2 に含まれる、TLS システム既定のバージョンのサポート](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | サポートなし |

## <a name="azure-cloud-services"></a>Azure Cloud Services

使用している場合[Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Web ロールとワーカー ロールをホストし、アプリケーションを実行するを考慮に入れる TLS 1.2 をサポートする必要があるいくつかの考慮事項があります。

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET framework 4.7 が既定では Azure ゲスト OS にインストールされていません。

最新の Azure ゲスト OS ファミリ 5 リリース (Windows Server 2016) にインストールされている最新バージョンは、4.6.2 です。 各 Azure ゲスト OS に .NET Framework のバージョンがインストールされているを参照してください、 [Azure ゲスト OS リリースと SDK の互換性対応表](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix)です。

場合は、アプリが Azure ゲスト OS バージョンで利用できない .NET Framework のバージョンを対象には、自分でインストールする必要があります。 参照してください[Azure クラウド サービスのロールに .NET をインストール](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet)です。 Framework のインストールには、再起動が必要とするサービスの役割が準備完了状態に入る前に再起動もことがあります。

### <a name="azure-guest-os-registry-settings"></a>Azure ゲスト OS のレジストリ設定

Azure ゲスト OS イメージを[Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/)は既に、`SchUseStrongCrypto`レジストリ キー値を 1 に設定します。 詳細については、次を参照してください。 [SchUseStrongCrypto](#schusestrongcrypto)です。

設定、 [SystemDefaultTlsVersions](#systemdefaulttlsversions)レジストリ キーを 1 にします。 参照してください[Windows レジストリを使用してセキュリティを構成する](#configuring-security-via-the-windows-registry)です。
