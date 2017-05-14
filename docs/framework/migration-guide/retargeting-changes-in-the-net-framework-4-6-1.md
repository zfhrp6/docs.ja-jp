---
title: ".NET Framework 4.6.1 における再ターゲットの変更点 | Microsoft ドキュメント"
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
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0adc4a6cae566b6a15c5fa492620abb74b47335b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="retargeting-changes-in-the-net-framework-461"></a>.NET Framework 4.6.1 における再ターゲットの変更点
まれに、変更を再ターゲットすると [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象として再コンパイルされるアプリに影響する場合があります。 別途指定がない限り、これらの変更が、以前のバージョンの .NET Framework をターゲットとし、かつ [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されているバイナリに影響を与えることはありません。  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] には、次の領域の変更の再ターゲットが含まれます。  
  
-   [コア](#Core)  
  
-   [コード コントラクト](#Contracts)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows フォーム](#WinForms)  
  
<a name="Core"></a>   
## <a name="core"></a>コア  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降のバージョンを対象とするアプリの場合、<xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName> メソッドのオーバーロードによって作成された <xref:System.IO.Compression.ZipArchiveEntry> オブジェクトの　<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A> プロパティで、パスの区切り記号がバックスラッシュ ("\\") からフォワードスラッシュ ("/") に変更されました。|この変更によって、.NET の実装が [.ZIP ファイル形式の仕様](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)のセクション 4.4.17.1 に準拠するようになったほか、Windows 以外のシステムで ZIP アーカイブを圧縮解除できるようになりました。<br /><br /> ただし、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降のバージョンを対象とするアプリではこの動作を無効にすることができます。 詳細については、「[Mitigation: ZipArchiveEntry.FullName Path Separator (軽減策: ZipArchiveEntry.FullName パスの区切り文字)](../../../docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)」を参照してください。|エッジ|  
  
<a name="Contracts"></a>   
## <a name="code-contracts"></a>コード コントラクト  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=fullName> と <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=fullName>、および <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> への呼び出し|.NET Framework 4.6.1 が対象のアプリの場合、リライターがコンパイラの警告 CC1036: "Detected call to method 'System.String.IsNullOrWhiteSpace(System.String)' without [Pure] in method..."|これはコンパイラ エラーではなく、コンパイラ警告です。<br /><br /> この動作については [GitHubの問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) で報告されています。 この警告が表示されないようにするには、コード コントラクト ツールのソース コードの更新バージョンを [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) からダウンロードしてコンパイルします。 ページ下部から情報をダウンロードできます。|マイナー|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation"></a>Windows Communication Foundation  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> (<xref:System.IdentityModel.Claims> 名前空間)|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリで、X509 クレーム セットが、SAN フィールドに複数の DNS エントリが含まれている証明書から初期化される場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> メソッドは引数 `claimType` をすべての DNS エントリと一致させようとします。<br /><br /> 以前のバージョンの .NET Framework を対象とするアプリの場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> メソッドは、引数 `claimType` を最後の DNS エントリのみと一致させようとします。|この変更は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするすべてのアプリに影響を与えます。 以前のバージョンの .NET Framework を対象とするアプリには影響しません。<br /><br /> ただし、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリではこの動作を無効にすることができます。 さらに、アプリが以前の .NET Framework バージョンを対象とするものの、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されている場合、この動作を選択することができます。 詳細については、「[軽減策: X509CertificateClaimSet.FindClaims メソッド](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)」を参照してください。|マイナー|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows フォーム  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッド (<xref:System.Windows.Forms> 名前空間)|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とする Windows フォーム アプリでは、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると、カスタムの <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装は、 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装が次の場合に、メッセージを安全にフィルター処理できます。<br /><br /> <ul><li>次の操作のいずれか、または両方を行う場合:<br /><br /> <ul><li><xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッドを呼び出すことで、メッセージ フィルターを追加する。</li><li><xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> メソッドを呼び出すことで、メッセージ フィルターを削除する。 メソッドをオーバーライドします。</li></ul></li><li>**および** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> メソッドを呼び出すことでメッセージをポンプする。</li></ul><br /> 以前のバージョンの .NET Framework を対象とする Windows フォーム アプリのこのような実装は、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると、<xref:System.IndexOutOfRangeException> 例外をスローする場合があります。|この変更は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするすべてのアプリに影響を与えます。 以前のバージョンの .NET Framework を対象とするアプリには影響しません。<br /><br /> ただし、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリではこの動作を無効にすることができます。 さらに、アプリが以前の .NET Framework バージョンを対象とするものの、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されている場合、この動作を選択することができます。 詳細については、[「軽減策: カスタムの IMessageFilter.PreFilterMessage 実装」](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)を参照してください。|エッジ|  
  
## <a name="see-also"></a>関連項目  
 [4.6.1 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
