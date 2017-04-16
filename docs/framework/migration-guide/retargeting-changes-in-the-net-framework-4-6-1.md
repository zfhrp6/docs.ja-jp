---
title: ".NET Framework 4.6.1 における再ターゲットの変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 411ad548-30fa-43da-8716-10eccfc839e6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# .NET Framework 4.6.1 における再ターゲットの変更点
まれに、変更を再ターゲットすると [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象として再コンパイルされるアプリに影響する場合があります。 別途指定がない限り、これらの変更が、以前のバージョンの .NET Framework をターゲットとし、かつ [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されているバイナリに影響を与えることはありません。  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] には、次の領域の変更の再ターゲットが含まれます。  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows フォーム](#WinForms)  
  
<a name="WCF"></a>   
## Windows Communication Foundation  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName><br /><br /> \(<xref:System.IdentityModel.Claims> 名前空間\)|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリで、X509 クレーム セットが、SAN フィールドに複数の DNS エントリが含まれている証明書から初期化される場合、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> メソッドは `claimType` 引数をすべての DNS エントリと一致させようとします。<br /><br /> 以前のバージョンの .NET Framework を対象としたアプリでは、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A> メソッドは `claimType` 引数と最後の DNS エントリのみを一致させようとします。|この変更は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象としたすべてのアプリに影響を与えます。 以前のバージョンの .NET Framework を対象とするアプリには影響しません。<br /><br /> ただし、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリではこの動作を無効にすることができます。 さらに、以前のバージョンの .NET Framework を対象とするアプリが [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されている場合、この動作を選択することができます。 詳細については、「[軽減策: X509CertificiateClaimSet.FindClaims メソッド](../../../docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)」を参照してください。|マイナー|  
  
<a name="WinForms"></a>   
## Windows フォーム  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッド \(<xref:System.Windows.Forms> 名前空間\)|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とする Windows フォーム アプリでは、カスタムの <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装は、<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装が次の場合に <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると、メッセージを安全にフィルター処理することができます。<br /><br /> <ul><li>次の操作のいずれか、または両方を行う場合:<br /><br /> <ul><li><xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッドを呼び出してメッセージ フィルターを追加する。</li><li><xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> メソッドを呼び出してメッセージ フィルターを削除する。 メソッドをオーバーライドします。</li></ul></li><li>**なおかつ**、<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> メソッドを呼び出してメッセージをポンプする場合。</li></ul><br /> 以前のバージョンの .NET Framework を対象とする Windows フォーム アプリでは、このような実装で、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると <xref:System.IndexOutOfRangeException> 例外がスローされることがあります。|この変更は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象としたすべてのアプリに影響を与えます。 以前のバージョンの .NET Framework を対象とするアプリには影響しません。<br /><br /> ただし、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリではこの動作を無効にすることができます。 さらに、以前のバージョンの .NET Framework を対象とするアプリが [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されている場合、この動作を選択することができます。 詳細については、「[軽減策: カスタムの IMessageFilter.PreFilterMessage 実装](../../../docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)」を参照してください。|エッジ|  
  
## 参照  
 [4.6.1 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)