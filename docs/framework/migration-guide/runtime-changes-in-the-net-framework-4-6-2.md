---
title: ".NET Framework 4.6.2 におけるランタイムの変更点 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.2
- application compatibility
ms.assetid: 23bf3a87-6fa1-4b5e-b92c-a39867a06e7f
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: da809955776b5a5cd3776898ecc4c97db74ceb0e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-462"></a>.NET Framework 4.6.2 におけるランタイムの変更点
まれに、ランタイムの変更が、.NET Framework の以前のバージョンをターゲットとするものの、それ以降のバージョンの .NET Framework ランタイムで実行される既存のアプリに影響を与える可能性があります。 また、異なる .NET Framework ランタイム環境で実行されるアプリケーション間での動作に違いが生じます。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] には、次の領域の変更が含まれています。  
  
-   [コア](#Core)  
  
-   [ASP.NET](#ASP)

-   [データ](#Data)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [XML 署名と入力規則](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>コア  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName><br /><br /> <xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory%2A?displayProperty=fullName>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] の文字カテゴリは Unicode バージョン 8.0 に基づきます。 .NET Framework のバージョン 4.5 から 4.6.1 では、Unicode 文字は Unicode バージョン 6.3 に基づいて分類されています。<br /><br /> 文字の比較と並べ替えは、この変更による影響を受けません。 詳細については、<xref:System.String> クラスのトピックの「Strings and The Unicode Standard」 (文字列と Unicode 標準) セクションを参照してください。|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] の文字カテゴリは、.NET Framework の以前のバージョンと一致しない場合があります。 この変更は、主にチェロキーの音節、新タイ ロ文字の母音記号および声調記号に影響します。<br /><br /> この変更に対処するには、コード レビューを行い、ハードコーディングされた Unicode 文字カテゴリに依存するロジックを削除または変更する必要があります。|Minor|  
|<xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=fullName>、<xref:System.Security.Cryptography.RSACng.ImportParameters%2A?displayProperty=fullName>、<xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A?displayProperty=fullName>、<xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=fullName>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、これらのメソッドで RSA 証明書の標準以外のキー サイズのキーにアクセスすることができます。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] とそれ以前のバージョンでは、このようなキーにアクセスしようとすると <xref:System.Security.Cryptography.CryptographicException> 例外がスローされました。|標準以外のキー サイズが使用されるときに、いずれかの例外処理ロジックが <xref:System.Security.Cryptography.CryptographicException> に依存している場合は、これを削除する必要があります。|エッジ|  
|<xref:System.Security.Cryptography.RSACng.VerifyHash%2A?displayProperty=fullName>|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、署名自体の形式が正しくない場合、このメソッドは `false` を返しました。 現在は、すべての検証エラーに対して `false` を返します。<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] および 4.6.1 では、署名自体の形式が正しくない場合、メソッドが <xref:System.Security.Cryptography.CryptographicException> を返しました。|検証が失敗し、メソッドが `false` を返す場合は、代わりにその実行が <xref:System.Security.Cryptography.CryptographicException> に依存するコードが実行される必要があります。|Minor|  
  
## <a name="a-nameasp--aspnet"></a><a name="ASP" /> ASP.NET

|特性|変更|影響|スコープ| 
|-------------|------------|------------|-----------|  
| <xref:System.Web.HttpRuntime.AppDomainApopPath%2A> | .NET Framework 4.6.2 では、null 文字を含む <xref:System.Web.HttpRuntime.AppDomainAppPath%2A> 値を取得するときに、ランタイムで <xref:System.NullReferenceException> がスローされました。 .NET Framework 4.6.1 とそれ以前のバージョンでは、<xref:System.ArgumentNullException> がスローされます。  | この変更に対応するには、次を行うことができます。 <br/> - アプリケーションが .NET Framework 4.6.2 で実行されている場合には <xref:System.NullReferenceException> を処理します。 <br /> - 以前の動作を復元し、<xref:System.ArgumentNullException> をスローする .NET Framework 4.7 にアップグレードします。 | エッジ |

<a name="Data"></a>   
## <a name="data"></a>データ  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|Azure SQL データベースの接続プールのブロック期間|既知の Azure SQL データベースに対する接続オープン要求の場合、接続プールのブロック期間が削除されます。|接続オープン要求の再試行は、一時的な接続エラーのほぼすぐ後に発生します。 詳細については、「[Mitigation: Pool Blocking Period](~/docs/framework/migration-guide/mitigation-pool-blocking-period.md)」(軽減策: プールのブロック期間) を参照してください。|Minor|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> <br /> <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName>|トランスポート セキュリティで NetTcp を使用し、証明書の資格情報の種類を使用する場合、SSL 3 プロトコルは、安全な接続のネゴシエーションに使用される既定のプロトコルではなくなりました。|TLS 1.0 は常に NetTcp のプロトコル一覧に含まれているため、ほとんどの場合、既存のアプリには影響はないと考えられます。 既存のすべてのクライアントは TLS 1.0 以降を使用して接続をネゴシエートできるようになりました。<br /><br /> Ssl3 が必要な場合は、以下の構成メカニズムのいずれかを使用して、ネゴシエートされたプロトコルの一覧に Ssl3 を追加します。<br /><br /> -   <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName> プロパティ<br />-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> プロパティ<br />-    [\<netTcpBinding>](~/docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) の [\<transport>](~/docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md) セクション<br />-   [\<customBinding>](~/docs/framework/configure-apps/file-schema/wcf/custombinding.md) セクションの [\<sslStreamSecurity>](~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) セクション|エッジ|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.TextBlock> コントロールの親の `IsEnabled` プロパティ|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、<xref:System.Windows.Controls.TextBlock> コントロールの親の `IsEnabled` プロパティを変更すると、<xref:System.Windows.Controls.TextBlock> コントロールのすべての子 (ハイパーリンクやボタンなど) に影響していました。<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] と .NET Framework のそれ以前のバージョンでは、<xref:System.Windows.Controls.TextBlock> 内部のコントロールが常に <xref:System.Windows.Controls.TextBlock> の親の `IsEnabled` プロパティの状態を反映するわけではありませんでした。|この変更は、<xref:System.Windows.Controls.TextBlock> コントロール内部のコントロールに期待される動作に準拠しています。|Minor|  
|水平スクロール、仮想化、および <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName>|メインのスクロール方向と直交する方向で独自に仮想化を行う<xref:System.Windows.Controls.ItemsControl> のスクロール操作の動作が変更されました。|この変更により、エンド ユーザーがより予測可能で直感的な操作ができるようになりますが、水平スクロールの後に <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> の正確な値に依存するすべてのアプリに影響する可能性があります。 詳細については、「[Mitigation: Horizontal Scrolling and Virtualization](~/docs/framework/migration-guide/mitigation-horizontal-scrolling-and-virtualization.md)」(軽減策: 水平方向スクロールおよび仮想化) を参照してください。|Minor|  
|WPF のスペル チェック (<xref:System.Windows.Controls.SpellCheck?displayProperty=fullName> クラス)|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] の実行中に WPF のスペル チェックで確認されていた次の 3 つの問題が [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] で対処されています。<br /><br /> -  [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で、[ISpellChecker](https://msdn.microsoft.com/library/windows/desktop/hh869767\(v=vs.85\).aspx) または [ISpellCheckerFactory](https://msdn.microsoft.com/library/windows/desktop/hh869770\(v=vs.85\).aspx) メソッドを呼び出すと、スペル チェックによって <xref:System.Runtime.InteropServices.COMException> がスローされることがありました。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、これらの例外が除去されました。<br />-   [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で、スペル チェックによってドイツ語の "Hausnummer" などの複合語のスペル ミスが正しく検出されないことがありました。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、スペル チェックで複合語が正しく処理されます。<br />-   [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] では、アプリケーションが "別のユーザーとして実行" を使用して起動されると、スペル チェックで <xref:System.UnauthorizedAccessException> がスローされました。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、このシナリオはサポートされず、スペル チェックが自動的に無効になります。|これらの変更によって、スペル チェックの信頼性が強化されます。  スローされている例外にアプリケーションのコードが依存していない限り、これらがアプリケーションに悪影響を及ぼすことはありません。|エッジ|  
| [DataGridCellsPanel.BringIndexIntoView](xref:System.Windows.Controls.DataGridCellsPanel.BringIndexInfoView(System.Int32)) メソッド | .NET Framework 4.6.2 では、列の仮想化が有効になっているが列の幅が決定されていない場合、**BringIndexIntoView** メソッドが非同期で実行されます。 ただし、非同期操作が完了する前に列が削除されると、[ArgumentOutOfRangeException](xref:System.ArgumentOutOfRangeException) が発生する場合があります。<br/></br>.NET Framework 4.7 以降、このシナリオでは例外がスローされなくなりました。 | 例外の発生を防ぐには、次のいずれかの操作を行います。 <br/> - .NET Framework 4.7.1 にアップグレードする。 <br/> .NET Framework 4.6.2 の最新のサービス パッチをインストールする。 <br/> - [DataGrid.ScrollIntoView](xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object))メソッドに対する非同期応答が完了するまでは列を削除しないようにします。 | エッジ | 
  
<a name="XML"></a>   
## <a name="signed-xml-verification-requirements"></a>署名済み XML の検証要件  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> および <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName>|外部リソースの読み込みが無効になっており、あいまいな ID ターゲットが無効と見なされます。|次のようなさまざまなケースで例外がスローされます。<br /><br /> -   ID 属性ごとに要素を特定し、同じ ID で 2 番目の要素を定義している。<br />-   正当な `NCName` 値ではない ID を定義している。<br />-   外部の URI を参照している。<br /><br /> <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A?displayProperty=fullName> は次のようなドキュメントでは常に `false` を返します。<br /><br /> -   XPath 参照の変換を使用する。<br />-   XSLT 参照の変換を使用する。<br /><br /> 開発者は <xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=fullName> および <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> の使用だけでなく、<xref:System.Security.Cryptography.Xml.Transform?displayProperty=fullName> から派生した型も確認する必要があります。ドキュメントの受信者がこれを処理できない可能性があるためです。<br /><br /> 詳細については、「[.NET Framework アプリケーションの例外エラーまたは予期しないエラーが、セキュリティ更新プログラム 3141780 をインストールした後で SignedXml が含まれるファイルを処理しているときに発生する](https://support.microsoft.com/en-us/kb/3148821)」を参照してください。|Minor|  
  
## <a name="see-also"></a>関連項目  
 [4.6.2 でのアプリケーションの互換性](~/docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)
