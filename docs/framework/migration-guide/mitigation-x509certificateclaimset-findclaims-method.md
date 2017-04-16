---
title: "軽減策: X509CertificiateClaimSet.FindClaims メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 3
---
# 軽減策: X509CertificiateClaimSet.FindClaims メソッド
[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象としたアプリを使用して開始すると、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> メソッドは `claimType` 引数と、その SAN フィールド内のすべての DNS エントリを一致させようとします。  
  
## 影響  
 この変更は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象としたアプリにのみ影響を与えます。  
  
 以前のバージョンの .NET Framework を対象としたアプリでは、<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=fullName> メソッドは `claimType` 引数と最後の DNS エントリのみを一致させようとします。  
  
## 軽減策  
 この変更が望ましくない場合は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリでこの変更を無効にできます。この無効化は、そのアプリの構成ファイルの [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" /> </runtime>  
  
```  
  
 また、.NET Framework の以前のバージョンを対象とするものの [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されているアプリでは、そのアプリの構成ファイルの [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、この動作を有効にできます。  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" /> </runtime>  
  
```  
  
## 参照  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)