---
title: "軽減策: ClaimsIdentity コンストラクター | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 946903f1-0fbf-4f67-805b-1eb48352024d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84016664708b9b7fc61a9535e5f7910417caa6f1
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-claimsidentity-constructor"></a>軽減策: ClaimsIdentity コンストラクター
[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=fullName> コンストラクターが <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティを設定する方法が変わりました。 <xref:System.Security.Principal.IIdentity> 引数が <xref:System.Security.Claims.ClaimsIdentity> オブジェクトで、その <xref:System.Security.Claims.ClaimsIdentity> オブジェクトの <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティが `null` ではない場合、<xref:System.Security.Claims.ClaimsIdentity.Clone%2A?displayProperty=fullName> メソッドを使用して <xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティがアタッチされます。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] では、<xref:System.Security.Claims.ClaimsIdentity.Actor%2A> プロパティは既存の参照としてアタッチされます。  
  
## <a name="impact"></a>影響  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降、新しい <xref:System.Security.Claims.ClaimsIdentity> オブジェクトの <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティは、<xref:System.Security.Principal.IIdentity> 引数の <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=fullName> プロパティと同じではありません。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前のバージョンでは同じです。  
  
## <a name="mitigation"></a>軽減策  
 この動作が望ましくない場合、アプリケーション構成ファイルで `Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity` スイッチを `true` に設定して以前の動作を復元することができます。 この場合、web.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに以下を追加します。  
  
```  
  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Security.ClaimsIdentity.SetActorAsReferenceWhenCopyingClaimsIdentity=true" />  
   </runtime>  
</configuration>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
