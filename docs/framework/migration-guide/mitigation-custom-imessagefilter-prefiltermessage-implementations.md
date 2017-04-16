---
title: "軽減策: カスタムの IMessageFilter.PreFilterMessage 実装 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 2
---
# 軽減策: カスタムの IMessageFilter.PreFilterMessage 実装
[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とする Windows フォーム アプリでは、カスタムの <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装は、<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=fullName> 実装が次の場合に <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると、メッセージを安全にフィルター処理することができます。  
  
-   次の操作のいずれか、または両方を行う場合:  
  
    -   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> メソッドを呼び出してメッセージ フィルターを追加する。  
  
    -   <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> メソッドを呼び出してメッセージ フィルターを削除する。 メソッドをオーバーライドします。  
  
-   **および**、<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> メソッドを呼び出してメッセージをポンプする場合。  
  
## 影響  
 この変更は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とする Windows フォーム アプリにのみ影響を与えます。  
  
 .NET Framework の以前のバージョンを対象とする Windows フォーム アプリの場合、このような実装で、<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=fullName> メソッドが呼び出されると <xref:System.IndexOutOfRangeException> 例外がスローされることがあります。  
  
## 軽減策  
 この変更が望ましくない場合は、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] を対象とするアプリでこの変更を無効にできます。この無効化は、そのアプリの構成ファイルの [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して行います。  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" /> </runtime>  
  
```  
  
 また、.NET Framework の以前のバージョンを対象としているが [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で実行されているアプリでは、そのアプリの構成ファイルの [\<runtime\>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の構成設定を追加して、この動作を有効にできます。  
  
```xml  
  
<runtime> <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" /> </runtime>  
  
```  
  
## 参照  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)