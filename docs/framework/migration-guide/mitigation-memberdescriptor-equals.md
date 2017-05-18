---
title: "軽減策: MemberDescriptor.Equals | Microsoft Docs"
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
ms.assetid: cf3735f0-0dd4-4bef-b4b0-575264e10f39
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 409f06f4dfbe7be50dd2c487e49d3d4d8a477539
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-memberdescriptorequals"></a>軽減策: MemberDescriptor.Equals
[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドの実装が変更されました。 `System.ComponentModel.EventDescriptor.Equals` メソッドと `System.ComponentModel.PropertyDescriptor.Equals` メソッドでは基底クラスの実装が継承されるため、変更はこれらのメソッドにも影響します。  
  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] より前のバージョンの .NET Framework を対象とするアプリでは、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドの一部の等価テストで、あるオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> プロパティと、別のオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> プロパティが誤って比較されていました。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドで 2 つのオブジェクトの <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> プロパティが比較されます。  
  
## <a name="impact"></a>影響  
 この変更により、<xref:System.ComponentModel.MemberDescriptor?displayProperty=fullName> オブジェクトの等価テストが正しく実装され、影響は最小限になるはずです。  
  
## <a name="mitigation"></a>軽減策  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降のバージョンの .NET Framework を対象とするアプリが、メンバー記述子が等しい場合に `false` を返すことがある <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドに依存している場合に利用可能な回避策は次の 2 つがあります。  
  
-   app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することで、ソース コードを変更せずにこの変更を無効にすることができます。  
  
    ```xml  
  
    <runtime>  
        <AppContextSwitchOverrides value = "Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />  
     </runtime>  
  
    ```  
  
-   次のコード フラグメントのように、ソース コードを変更し、<xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=fullName> メソッドを呼び出した後で <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=fullName> プロパティと <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=fullName> プロパティを手動で比較して以前の動作を復元することができます。  
  
    ```csharp  
  
    if (memberDescriptor1.Equals(memberDescriptor2) &   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)) {  
          // Code to execute if true.  
    }  
    else {  
          // Code to execute if false.     
    }  
  
    ```  
  
    ```  
  
    If memberDescriptor1.Equals(memberDescriptor2) And   
        memberDescriptor1.Description.Equals(memberDescriptor2.Category)  
          // Code to execute if True.  
    Else  
          // Code to execute if False.     
    End If  
  
    ```  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前のバージョンを対象とするアプリでは、app.config ファイルに次の値を追加することで、この変更を有効にできます。  
  
```xml  
  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true />  
</runtime>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)   
 [4.6.2 でのアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-2.md)

