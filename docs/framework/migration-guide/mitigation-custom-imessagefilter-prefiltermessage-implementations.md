---
title: "軽減策: カスタムの IMessageFilter.PreFilterMessage 実装 | Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d85c827b414cc94410a921bfae9ce3e1764d22ea
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>軽減策: カスタムの IMessageFilter.PreFilterMessage 実装
.NET Framework の [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降のバージョンを対象とする Windows フォーム アプリでは、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると、カスタムの <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装は、 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装が次の場合に、メッセージを安全にフィルター処理できます。  
  
-   次の操作のいずれか、または両方を行う場合:  
  
    -   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッドを呼び出すことで、メッセージ フィルターを追加する。  
  
    -   <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> メソッドを呼び出すことで、メッセージ フィルターを削除する。 メソッドをオーバーライドします。  
  
-   **および** <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> メソッドを呼び出すことでメッセージをポンプする。  
  
## <a name="impact"></a>影響  
 この変更によって影響を受けるのは、.NET Framework の [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以降のバージョンを対象とする Windows フォーム アプリのみです。  
  
 以前のバージョンの .NET Framework を対象とする Windows フォーム アプリの場合、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName>メソッドが呼び出されると、このような実装が <xref:System.IndexOutOfRangeException> 例外をスローする場合があります。  
  
## <a name="mitigation"></a>軽減策  
 この変更が望ましくない場合は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] またはそれ以降のバージョンを対象とするアプリでこの変更を無効にできます。この無効化は、そのアプリの構成ファイルの [\<<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 また、.NET Framework の以前のバージョンを対象とするものの [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] またはそれ以降のバージョンで実行されているアプリでは、そのアプリの構成ファイルの [\<<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、この動作を有効にできます。  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)

